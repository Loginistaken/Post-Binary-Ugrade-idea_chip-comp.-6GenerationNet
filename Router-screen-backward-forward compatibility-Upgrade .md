# Post-Binary Upgrade (PC‑ASIC‑II) — Revised for modem→screen / display‑level placement and correct symbol packing

## Display‑side PBUA specification (block diagram, functional blocks, and placement)

Goal: define a display‑integrated Post‑Binary Upgrade Adapter (Display‑PBUA) that receives A–Z post‑binary streams, 
decodes them into pixels, and hands decoded frames to the display framebuffer with minimal latency and low CPU involvement.

Block diagram (ASCII):

Modem/Edge PBUA ---> Optical/RF Link ---> Display Optical Rx/Front End
                                           |
                                           v
                                +----------------------------+
                                |  WDM Demux / Spectral     |
                                |  Locker & Thermal Cal     |
                                +----------------------------+
                                           |
                                           v
                                +----------------------------+
                                | Coherent Detector Array /  |
                                | Direct Detector Array      |
                                +----------------------------+
                                           |
                                           v
                                +----------------------------+
                                | Symbol Demapper & FEC     |
                                |  - 5‑bit fixed mode       |
                                |  - Base‑26 variable mode  |
                                |  - Phase/Amplitude sublevels
                                +----------------------------+
                                           |
                                           v
                                +----------------------------+
                                | Frame Reconstructor &     |
                                |  Depacketiser             |
                                +----------------------------+
                                           |
                                           v
                                +----------------------------+
                                | Display Framebuffer Bridge|
                                |  - DMA engine             |
                                |  - Pixel format convert   |
                                |  - Compositor hooks       |
                                +----------------------------+
                                           |
                                           v
                                +----------------------------+
                                | Display Panel / SoC GPU   |
                                +----------------------------+

Placement notes:
- The Display‑PBUA may be implemented as: (a) integrated IP inside the display controller SoC for AR/VR/mobile;
-  (b) a discrete module on smart TV/monitor PCB; or (c) an external dongle that exposes a standard display interface
-   (eDP/DP/HDMI) together with a low‑latency DMA path to the host.
- For lowest latency and power, integrate the Display‑PBUA into the display controller so decoded frames write directly
-  to the panel's scanout buffers.

## Display‑PBUA register map (suggested minimal set)

Register offsets are relative to MMIO base for the Display‑PBUA device.

- 0x00 CONTROL — Control register (bitmask)
  - bit0: DEVICE_ENABLE
  - bit1: RESET
  - bit2: MODE_SELECT (0 = 5‑bit fixed, 1 = base‑26)
  - bit3: LINK_UP
  - bits[7:4] reserved

- 0x04 STATUS — Read‑only status
  - bit0: RX_LOCK (spectral locked)
  - bit1: FEC_OK
  - bit2: FRAME_READY
  - bit3: DMA_BUSY
  - bits[31:8]: error code

- 0x08 CAPABILITIES — bitmask indicating supported features
  - bit0: SUPPORTS_5BIT
  - bit1: SUPPORTS_BASE26
  - bit2: SUPPORTS_PHASE_SUBLEVELS
  - bit3: SUPPORTS_AMPLITUDE_SUBLEVELS
  - bit4: SUPPORTS_COHERENT_RX

- 0x0C RX_RATE — negotiated symbol rate (symbols/sec) as 32‑bit integer
- 0x10 FRAMEBUF_ADDR — physical address for framebuffer write (64‑bit via pair: 0x10 low, 0x14 high)
- 0x18 FRAME_WIDTH — pixels per line (32‑bit)
- 0x1C FRAME_HEIGHT — lines per frame (32‑bit)
- 0x20 PIXEL_FMT — pixel format code (e.g., 0x0 = YUV420, 0x1 = RGB565, 0x2 = RGBA8888)
- 0x24 IRQ_MASK — IRQ enable bits
  - bit0: IRQ_FRAME_READY
  - bit1: IRQ_LINK_LOST
  - bit2: IRQ_FEC_ERROR
- 0x28 CONTROL2 — control extensions (force rebase, debug mode, loopback)

Event/interrupt flow:
- Host writes FRAMEBUF_ADDR, FRAME_WIDTH/HEIGHT, PIXEL_FMT and sets DEVICE_ENABLE.
- On each decoded frame the Display‑PBUA writes to FRAMEBUF_ADDR via DMA and raises IRQ_FRAME_READY when complete.
- Host can read STATUS to confirm FEC_OK and RX_LOCK.

## Link & API negotiation (handshake) — minimal sequence

1. Link discovery: Display‑PBUA advertises CAPABILITIES (readable by host/modem) via side channel or during link up.
2. Capability negotiation: Modem/edge PBUA and Display‑PBUA exchange preferred mode (5‑bit or base‑26),
3.  max symbol rate, max frame stripe width, and FEC profile ID. This may be done via a small control
channel piggybacked on the optical link or via a separate control radio (Bluetooth/sideband) during setup.
4. Mode select: Host writes CONTROL.MODE_SELECT and sets FRAMEBUF_ADDR/format.
5. Run time: Modem sends stream; Display‑PBUA decodes frames, performs FEC, writes frame buffer, signals IRQ.
6. Fallback: If RX_LOCK or FEC fails, edge PBUA can fall back to mmWave lanes or request reconfiguration (lower symbol rate, stronger FEC).

Negotiated parameters (example TLVs):
- TLV 0x01: MODE (0x00=5BIT,0x01=BASE26)
- TLV 0x02: SYMBOL_RATE (uint32)
- TLV 0x03: FEC_PROFILE_ID (uint8)
- TLV 0x04: FRAME_STRIPE_WIDTH (pixels)
- TLV 0x05: PIXEL_FMT

## Display Framebuffer Bridge — behavior & host integration

- Expose a lightweight driver that maps the FRAMEBUF_ADDR region as a grantable DMA buffer.
- The driver should expose an ioctl or sysfs node to negotiate mode and to provide buffer addresses.
- For embedded displays, integrate as an SoC IP with device tree bindings.
- For compositors: support zero‑copy buffer handoff where the PBUA DMA target is registered as a scanout buffer.
- Provide a minimal API for notifying the compositor of new frames (IRQ or eventfd).
- Power management hooks: when no link traffic, reduce LO power and place detectors in low‑power mode.
- Allow host to put device into deep sleep via CONTROL.RESET.

## Firmware pseudo‑code (FPGA/ASIC pseudo‑logic)

The following is a small example of the core decode/pack logic for a Display‑side PBUA. 
It shows both 5‑bit fixed mapping (fast path) and base‑26 decode (efficient path). This is intentionally compact and illustrative.

```pseudo
// High level loop in hardware/firmware
init():
  load_FEC_profile()
  read_mode = CONTROL.MODE_SELECT
  if read_mode == 0: // 5‑bit
    demapper = demap_5bit
  else:
    demapper = demap_base26

main_loop():
  while DEVICE_ENABLE:
    symbol = rx_next_symbol()            // read next A–Z + sublevels
    bits = demapper(symbol)
    buffer.append(bits)
    if frame_boundary_detected(buffer):
      payload = FEC_decode(buffer)
      if FEC_ok(payload):
        frame = depacketize(payload)
        pixel_buf = convert_to_pixel_format(frame, PIXEL_FMT)
        dma_write(FRAMEBUF_ADDR, pixel_buf)
        raise_irq(IRQ_FRAME_READY)
      else:
        handle_fec_error()
      buffer.clear()

// demapping for 5‑bit fixed mode: map symbol index (0..25) to 5 bits
function demap_5bit(symbol):
  index = symbol.color_index  // 0..25
  if index > 25:
    // control/escape handling
    return handle_control_symbol(index)
  // return 5‑bit word; fastest path
  return to_bits(index, 5)

// demapping for base‑26: accumulate digits and convert to bits in chunks
function demap_base26(symbol):
  digit = symbol.color_index // 0..25
  base26_accumulate.push(digit)
  // Convert groups of k digits to bytes when possible. Example: accumulate 13 digits -> 8 bytes.
  if base26_accumulate.length >= 13:
    bytes = base26_to_bytes(base26_accumulate.take(13))
    base26_accumulate.discard(13)
    return bytes_to_bits(bytes)
  else:
    return []

function base26_to_bytes(digits[13]):
  // big‑integer conversion: value = sum(digits[i]*26^(n-1-i))
  // convert value to 8 bytes big‑endian
  value = 0
  for d in digits:
    value = value * 26 + d
  return to_bytes(value, 8)
```

Implementation notes for firmware:
- The 5‑bit path is deterministic and low latency: one symbol → one 5‑bit output; minimal buffering.
- The base‑26 path is more efficient in average bits per symbol but requires accumulation
-  and big‑integer math; implement in hardware via a small multi‑precision accumulator
-  or microcode on an embedded microcontroller inside the PBUA.
- Both paths should feed the same FEC decoder pipeline. The modem should advertise if
- it will use base‑26 to ensure decoder buffering is sized correctly.

## Test plan & verification checklist (modem→display latency and power)

Test objectives:
- Verify binary↔A–Z mapping correctness (roundtrip).
- Measure end‑to‑end latency (modem→display framebuffer ready) under different placement scenarios (modem‑PBUA, edge PBUA, display‑PBUA).
- Measure power consumption for display‑side PBUA in active decode and idle modes.
- Verify FEC thresholds and graceful degradation under SNR loss.

Test cases:

1) Functional roundtrip
- Inject known binary test payload at modem‑PBUA (patterned bytes). Send through fabric to Display‑PBUA.
- At Display‑PBUA, decode and reconstruct payload. Verify bit‑exact match (for both 5‑bit and base‑26 modes).
- Pass/fail: exact match

2) Symbol packing edge cases
- Test payloads whose length yields different residues for 5‑bit packing and base‑26 packing.
- Verify reserved control codes (26–31) handled gracefully.

3) Latency benchmarks
- Scenario A: Modem PBUA → direct optical link → Display‑PBUA (display integrated).
- Scenario B: Modem PBUA → Edge PBUA → Display‑PBUA
- Scenario C: Modem PBUA → Edge PBUA → Host GPU decode (legacy path) → panel

Measure:
- Tx timestamp at modem (when first symbol emitted)
- RX timestamp when Display‑PBUA raises FRAME_READY
- Host path: measure at compositor having a rendered frame available

Targets (example):
- Display‑integrated path: median latency <= 2 ms, p95 <= 5 ms for 4K30 streams (values depend on link and FEC).
- Edge path: median <= 5–10 ms. Legacy path (CPU/GPU): higher; specify baseline for comparison.

4) Power measurement
- Measure Display‑PBUA active power during decode at target symbol rate (WDM lanes used) and idle power with LO gated.
- Target: consumer SoC Display‑PBUA active power < 1 W for mobile/AR use; < 5 W for large displays (example goals, to be tuned per hardware).

5) FEC and SNR thresholds
- Sweep SNR and measure FEC failure rate for each FEC profile at several symbol rates and modulation depths.
- Verify graceful degradation: when SNR drops, link negotiates lower symbol rate or falls back to mmWave lanes.

6) Robustness & reconfiguration
- Simulate burst loss, packet reorder and test resynchronization and frame partial recovery abilities.
- Verify driver APIs for buffer rollover and DMA correctness under stress (rapid frame rates, multi‑window compositing).

7) UX & fallbacks
- Test display update behavior when frames lost: frozen, partial refresh, or quickly switched to lower quality gracefully.
- Verify that compositor/OS sees consistent buffer states.

Verification artifacts to produce
- Bit��exact trace logs for symbol streams and decoded frames.
- Latency histogram graphs for each scenario and symbol rate.
- Power vs symbol‑rate plots.
- FEC BER vs SNR curves and negotiated fallback points.

---

End of appended canvas content for post-binary‑upgrade_v2.md
