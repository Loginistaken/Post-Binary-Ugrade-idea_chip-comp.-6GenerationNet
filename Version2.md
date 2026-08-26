
PBUA DUAL-DOMAIN FABRIC — FINAL CONCEPTUAL REBUILD

Optical Standard, Wireless Optional (OS/WO)

Updated Post-Binary A–Z Photonic System — High-Radix PAM / EL-40 Architecture

Conceptual 2026–2030 Development Target | Build-Me-Phase Specification

  STATUS: CONCEPT / ARCHITECTURAL DESIGN IN BUILD-ME PHASE

  This document defines a proposed architecture, not a completed product
  or established industry standard. Individual technologies used by the
  architecture are real and commercially or experimentally established,
  but the complete PBUA integration, exact 26-channel A–Z mapping, EL-40
  control model, adapter architecture, and claimed system-level
  latency/energy advantages still require engineering, fabrication,
  interoperability testing, and benchmarking.

------------------------------------------------------------------------

1. INTRODUCTION — THE UPDATED POST-BINARY PBUA CONCEPT

The Post-Binary Unified Architecture (PBUA) is a proposed higher-radix
transport and media architecture intended to move beyond the limitations
of heavily serialized binary data transport without requiring the
immediate replacement of binary computing itself.

The original vision is retained: information can be organized as an A–Z
logical photonic alphabet, represented by 26 distinct optical channel
identities, with multiple amplitude states on each channel. The updated
architecture makes that vision more practical by separating the logical
alphabet from the physical implementation.

The system is therefore not literally a computer in which every
transistor stops using binary 0 and 1. CPUs, GPUs, memory, sensors,
DACs, operating systems, and conventional peripherals can remain binary
internally. The proposed post-binary transition occurs primarily in the
way high-volume information is organized, transported, synchronized, and
reconstructed.

The updated architecture is built around one central idea:

Use parallel photonic transport when it provides the best path; use
wireless when mobility or blockage requires it; and let EL-40 select the
simplest physical configuration that meets the media deadline with the
lowest practical energy cost.

This becomes the PBUA Dual-Domain Fabric — Optical Standard, Wireless
Optional (OS/WO).

The system is deliberately being rebuilt as a realistic 2026–2030
development concept rather than presented as an already manufactured 8G
product.

------------------------------------------------------------------------

2. WHAT “POST-BINARY” MEANS IN THIS ARCHITECTURE

PBUA uses “post-binary” as an architectural term.

The conventional model is dominated by binary digital representation and
serialized transport:

binary data → serializer → electrical link → receiver → reconstruction

PBUA proposes:

binary-compatible source → higher-radix mapper → parallel
optical/wireless PHY → synchronized reconstruction → conventional media
output

The key change is therefore not the disappearance of binary logic. It is
the movement of high-bandwidth data through a higher-radix, parallel,
adaptive transport layer.

The PBUA system can consequently coexist with existing binary computers.
A conventional computer can send HDMI, DisplayPort, PCIe-class,
Ethernet, USB, or other supported data into the PBUA adapter. A
PBUA-capable source can instead use the proposed A–Z/WDM/PAM transport.
The receiver translates the result back into ordinary pixels, audio
samples, or application data where required.

------------------------------------------------------------------------

3. THE UPDATED CENTRAL ARCHITECTURE

The complete system is organized as:

SOURCE → PBUA MEDIA/TRANSPORT ENCODER → RADIX MAPPER → EL-40 →
DUAL-DOMAIN PHY → FEC/TIMING → UNIVERSAL PBUA ADAPTER → FRAME/AUDIO
RECONSTRUCTION → OUTPUT

The dual-domain PHY contains:

1.  Optical Standard Port
2.  Free-Space Optical continuity option
3.  Wireless Optional Port
4.  Legacy electrical/high-speed compatibility port
5.  Control sideband

The optical domain is preferred for high-volume data when a suitable
path exists.

The wireless domain is not a second copy of the 26-channel optical
system. It is a continuity and mobility layer using appropriate radio
PHYs such as QAM/MCS, MIMO, OFDMA, carrier aggregation, and multi-link
operation where supported.

------------------------------------------------------------------------

4. PBUA DUAL-DOMAIN FABRIC — THE NEW SYSTEM-WIDE RULE

The updated PBUA rule is:

OPTICAL WHEN AVAILABLE.

Use guided photonics, integrated silicon photonics, optical docking, or
another appropriate optical path for large data transfers when the
measured link can satisfy the deadline and energy budget.

WIRELESS WHEN MOBILITY OR BLOCKAGE REQUIRES IT.

Use Wi-Fi, cellular, or another approved wireless PHY when the user is
mobile, the optical path is unavailable, the beam is blocked, or
untethered operation is required.

DO NOT FORCE THE 26 A–Z OPTICAL WDM CHANNELS INTO CONVENTIONAL RADIO
SPECTRUM.

The wireless system translates the PBUA information representation into
its native radio modulation and coding system.

This separation makes the architecture more realistic and prevents the
optical and radio portions from being treated as if they were physically
identical technologies.

------------------------------------------------------------------------

5. ONE ELECTROMAGNETIC FAMILY — DIFFERENT PHYSICAL DOMAINS

Optical photons and radio photons belong to the same electromagnetic
family. They differ in frequency, wavelength, propagation environment,
hardware, and application.

The architecture therefore uses a hierarchy of physical transport
domains:

  -----------------------------------------------------------------------
  Domain                  Approximate region      PBUA role
  ----------------------- ----------------------- -----------------------
  Guided optical          Telecom infrared,       Preferred high-capacity
                          e.g. 1310–1550 nm class fabric

  Free-space optical      IR or visible optical   Short-range optical
                          bands                   wireless / docking

  Wi-Fi / cellular        RF, microwave, mmWave   Mobility and
                          and future bands        blocked-path continuity

  Display/camera optics   Visible optical band    Human media
                                                  capture/presentation
  -----------------------------------------------------------------------

The system does not claim that one photon type is inherently faster. The
optimization concerns the total system path: serialization, queueing,
encoding, FEC, memory movement, retransmission, presentation timing, and
power.

------------------------------------------------------------------------

6. THE A–Z ALPHABET — UPDATED COLOR TERMINOLOGY

The original visual language used 26 colors. The engineering version
must distinguish the visual metaphor from the physical implementation.

A–Z represents 26 logical optical channel identities.

Each identity is assigned to a stabilized wavelength channel in the
optical implementation.

Therefore:

A = optical channel 1 B = optical channel 2 … Z = optical channel 26

The diagrams may color-code these channels for human understanding.
Those colors are a visualization of the channel identities. They are not
a claim that the physical device contains exactly 26 naturally occurring
visible colors.

The preferred physical implementation is a set of wavelength-defined
optical channels, potentially in telecom infrared regions, with the
exact wavelengths, spacing, guard bands, source architecture, and
channel count determined by optical engineering and standards
compatibility.

This correction preserves the original A–Z idea while making it
technically precise.

------------------------------------------------------------------------

7. HIGH-RADIX ORGANIZATION

The A–Z layer is a higher-radix logical organization.

A 26-symbol alphabet has:

log2(26) ≈ 4.70 bits per logical symbol

before coding, framing, modulation, synchronization, and implementation
overhead.

PBUA then separates three concepts:

RADIX — how information is organized logically.

WDM — how multiple wavelength-defined channels are transported in
parallel.

PAM — how amplitude states are represented within each optical channel.

This separation is central to the updated architecture.

The system does not require one optical carrier to distinguish 26
fragile amplitude levels.

Instead:

26 stabilized wavelength lanes + PAM-4/PAM-8 per lane + FEC + parallel
detection.

------------------------------------------------------------------------

8. PAM-4 AND PAM-8

PAM provides multiple amplitude states on each optical lane.

PAM-4 provides four amplitude states and is the more conservative
operating mode.

PAM-8 provides eight amplitude states and is the higher-capacity
proposed mode.

The system therefore has adaptive optical modulation:

PAM-8 → PAM-4 → lower symbol rate / fewer channels → alternate domain

when signal quality, thermal state, FEC burden, or power constraints
require it.

The architecture does not assume PAM-8 is always superior. A lower-order
mode can be preferable when it reduces errors, retransmissions, DSP
work, or energy per successfully delivered frame.

------------------------------------------------------------------------

9. MICRO-COMB / SILICON-NITRIDE IMPLEMENTATION DIRECTION

The preferred conceptual source architecture is a silicon-photonics or
silicon-nitride photonics platform using integrated wavelength
generation rather than a large independent laser array.

A micro-comb can provide a set of evenly spaced optical lines from a
pumped resonator. In the PBUA concept, the usable subset would be
selected and stabilized to create the desired A–Z channel grid.

The architecture may use:

-   silicon photonics
-   silicon nitride photonics
-   integrated micro-combs
-   minimal heterogeneous III–V or other high-performance gain/source
    material where necessary
-   conventional semiconductor doping and control structures
-   integrated modulators
-   photodetectors
-   wavelength monitoring
-   thermal control

This is a proposed implementation direction, not a claim that a
production-ready 26-channel PBUA micro-comb chip already exists.

------------------------------------------------------------------------

10. MATERIAL AND MANUFACTURING OBJECTIVE

The updated concept deliberately moves away from earlier exotic-crystal
assumptions.

The bulk platform is intended to rely on silicon/silicon-nitride
photonics and established semiconductor processing. Minimal specialized
III–V or other gain/source material may still be required.

The objective is to reduce dependence on large volumes of high-hazard or
scarce optical source materials and to simplify manufacturing compared
with an architecture built around extensive exotic photonic materials.

The system must not be described as non-toxic. Semiconductor and
photonic manufacturing still involves hazardous chemicals,
high-temperature processing, cleaning, deposition, etching, and
waste-management requirements.

The defensible goal is:

lower material-hazard and scarcity burden relative to the earlier
proposed architecture, while retaining practical photonic functionality.
THE UPDATED POST-BINARY A–Z PHOTONIC SYSTEM

PART 2 PART1 (CONTINUED BELOW)
 
  STATUS: CONCEPTUAL / IN BUILD-ME PHASE. This document defines a
  proposed photonic architecture. The component technologies exist, but
  the complete 26-channel A–Z implementation, EL-40 integration,
  universal adapter, and system-level performance claims require
  prototype construction and measurement.

1. THE UPDATED VISION

Imagine a computer transport system that does not depend on moving every
high-bandwidth workload through one heavily serialized binary path.
Instead, information is organized into a higher-radix A–Z logical
alphabet and carried through multiple wavelength-defined optical lanes.
Each lane can use PAM-4 or PAM-8 amplitude states. The result is a
proposed parallel photonic transport fabric intended to reduce
serialization, unnecessary processing, and energy per delivered
workload.

The important correction is that the 26 “colors” are not 26 natural
visible colors. They are 26 logical identities assigned to stabilized
optical wavelength channels. Diagrams can display those identities as
colors for readability.

The system remains binary-compatible internally. CPUs, GPUs, memories,
sensors and conventional interfaces can remain binary. PBUA is
post-binary primarily at the transport and symbol-organization layer.

2. WHY THE SYSTEM IS BEING REBUILT

The earlier concept is rebuilt around technologies that are closer to
practical semiconductor and photonic manufacturing:

-   silicon photonics
-   silicon-nitride photonics
-   micro-comb wavelength generation
-   minimal heterogeneous optical gain/source material where needed
-   integrated modulators
-   photodetectors
-   PAM-4/PAM-8
-   WDM
-   FEC
-   thermal feedback
-   hardware timestamps
-   DMA
-   adaptive power management
-   EL-40 domain control

The goal is not to claim that a finished PBUA chip already exists. The
goal is to define a credible build path from existing technologies
toward the proposed architecture.

3. MATERIAL AND TOXICITY DIRECTION

The updated platform favors silicon/silicon-nitride photonics with
minimized specialized optical-source material. This can reduce reliance
on large volumes of high-hazard or scarce materials compared with
earlier exotic implementations.

It does not mean the chip is non-toxic. Semiconductor manufacturing
still uses hazardous processing chemicals and requires controlled
fabrication and waste handling.

The correct claim is:

a lower-hazard-material design direction, not zero-toxicity
manufacturing.

4. A–Z HIGH-RADIX LAYER

The logical alphabet contains 26 symbols:

A, B, C, … Z

A 26-symbol alphabet represents approximately 4.70 bits of information
per ideal symbol before overhead.

PBUA separates:

RADIX = logical organization

WDM = wavelength parallelism

PAM = amplitude states on each wavelength

This prevents the architecture from requiring one laser to distinguish
26 extremely close amplitude states.

5. 26 WDM CHANNELS

The target optical implementation contains 26 stabilized
wavelength-defined channels.

A conceptual mapping is:

A → λ1 B → λ2 C → λ3 … Z → λ26

The exact wavelength grid, channel spacing, guard bands, source
technology, detector architecture and packaging must be selected through
engineering validation.

The physical wavelengths may be in telecom infrared regions rather than
the visible spectrum.

6. MICRO-COMB SOURCE ARCHITECTURE

A silicon-nitride or silicon-photonics micro-comb can serve as a
conceptual wavelength-generation mechanism. One pump source can generate
a comb of optical lines, from which a controlled subset can be used for
the PBUA wavelength grid.

The system then adds the required:

-   filtering
-   stabilization
-   modulation
-   monitoring
-   detection
-   thermal control

The 26-channel target remains a PBUA design requirement, not a statement
that every current micro-comb automatically provides the exact
production-ready PBUA channel grid.

7. PAM-4 / PAM-8 PER CHANNEL

Each wavelength channel can use:

PAM-4 — robust operating mode.

PAM-8 — higher-capacity operating mode.

EL-40 can select between them based on:

-   signal quality
-   thermal state
-   FEC burden
-   power budget
-   deadline
-   wavelength stability

The adaptive sequence can be:

PAM-8 → PAM-4 → lower symbol rate → fewer active wavelengths → alternate
domain.

8. WHY THIS CAN REDUCE SERIALIZATION

The architecture does not rely on one stream carrying the entire
workload sequentially. Multiple wavelength lanes can transport
independently recoverable groups at the same time.

For a high-resolution video frame, groups can be distributed across
lanes. The exact mapping is dynamic rather than permanently assigning a
letter to one region of a picture.

The goal is:

more parallel transport and less waiting behind a single serial path.

This does not guarantee 26× lower latency. The complete system must be
measured.

9. WHY THIS CAN REDUCE ENERGY

The target is not simply high optical power. EL-40 activates only the
resources required by the workload.

Heavy video may use more wavelengths.

Normal video may use fewer.

Audio-only operation can use a protected low-bandwidth configuration.

Unused optical lanes, radio links, DSP blocks and other resources can
enter low-power states.

The relevant metric is:

energy per successfully presented frame/sample interval.

10. THE NEW EL-40 ROLE

EL-40 is the adaptive control layer above the optical PHY.

It observes:

-   channel quality
-   wavelength drift
-   PAM mode
-   symbol rate
-   FEC corrections
-   temperature
-   power
-   frame deadline
-   audio deadline
-   synchronization
-   available optical lanes
-   wireless availability

It chooses the operating state rather than forcing maximum performance
at all times.

The governing rule is:

use the lowest-energy configuration that can reliably satisfy the
required deadline.

11. THE PBUA DUAL-DOMAIN UPGRADE

The photonic system is now part of a larger architecture called:

PBUA DUAL-DOMAIN FABRIC

Optical Standard, Wireless Optional (OS/WO)

The optical fabric is the preferred high-capacity transport when
available.

Wireless is the mobility/continuity layer.

The wireless side does not recreate 26 optical wavelength channels in
radio spectrum.

Instead, the same logical information is translated into native radio
PHYs:

-   QAM
-   MCS adaptation
-   MIMO
-   OFDMA
-   carrier aggregation
-   multi-link operation
-   QoS
-   wireless FEC

Thus:

PAM = optical PHY

QAM/MCS = radio PHY

12. OPTICAL / FSO / RADIO HIERARCHY

The transport family becomes:

guided optical → preferred bulk path

FSO/Li-Fi → short-range optical wireless option

Wi-Fi/cellular → mobile or blocked-path continuity

The same PBUA media representation can cross these domains.

13. CAMERA-TO-PBUA PATH

The camera remains a conventional image sensor.

The complete path is:

camera sensor → image processor → PBUA media encoder → RADIX mapper →
A–Z channel organization → WDM → PAM → optical transport

Optional camera-side intelligence can identify motion, regions of
interest, objects, metadata and other useful information for adaptive
transmission.

14. AUDIO PROTECTION

Audio receives protected scheduling because synchronization errors can
be more disruptive than loss of video enhancement.

Priority order:

1.  synchronization
2.  audio
3.  essential video
4.  enhancement video

Digital audio still ultimately follows:

samples → DAC → amplifier → speaker.

PBUA transports the data; it does not replace the physical audio
transducer.

15. PMSE — MEDIA SYNCHRONIZATION

The PBUA Media Synchronization Engine tracks:

-   source clock
-   capture timestamp
-   frame ID
-   audio sample ID
-   sequence number
-   arrival timestamp
-   reconstruction time
-   presentation timestamp

This lets the system measure real end-to-end presentation latency rather
than assuming that optical propagation alone determines latency.

16. SIX-PART LATENCY MODEL

PBUA measures:

1.  source processing
2.  encoding/RADIX mapping
3.  physical flight
4.  decode/FEC/reconstruction
5.  presentation
6.  wireless contention/retransmission tail

The target is lower end-to-end and especially lower tail latency.

The architecture makes no claim that photons travel faster than light.

17. ERROR CORRECTION

A possible layered implementation is:

outer Reed-Solomon-type protection + inner soft-decision LDPC or
polar-type protection.

Exact coding remains a hardware-validation task.

A post-FEC BER such as 10^-15 is an engineering target, not a
demonstrated PBUA result.

18. WAVELENGTH LOCKING

The 26-channel fabric requires:

-   spectral monitoring
-   thermal feedback
-   guard bands
-   calibration
-   drift detection
-   channel health monitoring

When a channel becomes unstable:

remove → reassign → recover.

19. THERMAL CONTROL

Optical transport can reduce some electrical transport losses, but the
complete module still produces heat through drivers, lasers, modulators,
detectors, DSP, FEC and power electronics.

EL-40 therefore treats temperature as part of transport selection.

A thermal event can trigger:

lower optical power → lower PAM → lower symbol rate → fewer channels →
alternate path.

20. UNIVERSAL PBUA ADAPTER

The PBUA Adapter is the bridge between generations.

It accepts, conceptually:

-   legacy binary
-   modern high-speed binary
-   hybrid electrical/photonic
-   PBUA optical
-   FSO
-   wireless continuity
-   EL-40 coordinated PBUA

The display does not need to understand A–Z photonic symbols. The
adapter reconstructs a conventional framebuffer and audio stream.

21. PUGC

PUGC — PBUA Universal Generation Connector — is a connector architecture
containing:

-   legacy electrical interfaces
-   high-speed interfaces
-   optical interface
-   wireless module interface
-   control sideband
-   power management
-   capability negotiation

It can be implemented as a PCB, chiplet, docking station, external
adapter or integrated display controller.

22. MODERN STANDARDS COMPATIBILITY

The updated PBUA concept is designed to coexist with current standards
rather than replace them immediately.

The 2026 design context includes HDMI 2.2, DisplayPort/eDP families,
PCIe 7.0, UCIe 3.0, current Wi-Fi multi-link architectures and 5G/future
6G connectivity.

HDMI 2.2 currently defines up to 96 Gb/s with next-generation FRL and
retains backward compatibility. PCIe 7.0 defines 128 GT/s raw signaling.
UCIe 3.0 defines 48/64 GT/s chiplet data rates and enhanced
management/power capabilities.

PBUA-specific functionality remains an overlay architecture and must be
validated independently.

23. PERFORMANCE TARGETS — CAREFUL WORDING

The system is intended to target:

-   lower end-to-end latency
-   lower energy per presented frame
-   high aggregate bandwidth
-   lower serialization overhead
-   fewer unnecessary memory copies
-   stable audio/video synchronization
-   graceful optical-to-wireless fallback

These are engineering targets, not demonstrated results.

The earlier speculative “sub-10 ns” figure should therefore be treated
as a possible local/interconnect design target for selected paths, not a
claim about total camera-to-display latency across the complete system.
Total latency must include encoding, FEC, memory, scheduling and
presentation.

Likewise, terabit-class throughput remains a design objective that
depends on actual baud rate, channel count, coding overhead, packaging,
optical loss, crosstalk and receiver capability.

24. BUILD-ME PHASE

The proposed build sequence is:

Phase 1: software A–Z/RADIX model.

Phase 2: single-channel PAM/FEC optical demonstrator.

Phase 3: multi-wavelength optical demonstrator.

Phase 4: 26-channel wavelength-grid prototype.

Phase 5: EL-40 closed-loop controller.

Phase 6: Universal PBUA Adapter/PUGC prototype.

Phase 7: FSO and wireless continuity.

Phase 8: camera/audio/display end-to-end demonstration.

Phase 9: comparative energy/latency benchmarking.

25. WHAT MUST BE PROVEN

The prototype must establish:

-   number of stable wavelengths
-   aggregate throughput
-   PAM-4/PAM-8 performance
-   optical power
-   BER
-   FEC burden
-   thermal drift
-   crosstalk
-   energy/bit
-   energy/frame
-   end-to-end latency
-   99th-percentile latency
-   audio/video synchronization error
-   domain-switch time
-   recovery after optical blockage

26. FINAL POST-BINARY DEFINITION

The updated Post-Binary A–Z Photonic System is a proposed higher-radix
transport architecture in which 26 logical A–Z identities are mapped
onto stabilized optical wavelength channels, each using adaptive
PAM-4/PAM-8 signaling, while EL-40 dynamically manages wavelength
allocation, FEC, timing, thermal state, power and physical-domain
selection. The optical system is the preferred high-capacity fabric; FSO
and QAM/MCS-based wireless are optional continuity domains; and the
Universal PBUA Adapter preserves compatibility with conventional binary
computers and modern display/system interfaces.

27. FINAL STATUS

Concept: active.

Development state: build-me phase.

Target period: 2026–2030 for progressive prototypes.

Official standard status: PBUA itself is not an established industry
standard.

8G status: architectural designation only.

26-color status: 26 logical wavelength identities, visually represented
as colors; not 26 natural visible colors.

Core objective: experimentally determine whether the integrated PBUA
architecture can achieve lower end-to-end latency and lower energy per
successfully delivered workload than appropriate contemporary baselines.

FINAL STATEMENT

The PBUA concept is now rebuilt around one coherent rule: parallel
photonics is the preferred high-capacity transport fabric, wireless is
the optional mobility/continuity layer, and EL-40 continuously chooses
the least complex and least energy-intensive configuration that can
still meet the required media deadline.

------------------------------------------------------------------------
continued from top 
11. WHY PARALLELISM IS CENTRAL TO LOWER LATENCY

The lower-latency concept does not depend on photons traveling faster
than light.

It depends on reducing the amount of information that must wait in a
serialized pipeline.

A single serialized path resembles:

A → B → C → D → E → F → …

PBUA proposes multiple wavelength lanes operating simultaneously:

λ1 | λ2 | λ3 | … | λ26

The workload can be divided across independently recoverable groups.
This attacks serialization and can increase aggregate transport
capacity.

However, 26 channels do not automatically create 26× lower latency.
Actual latency depends on source processing, encoding, modulation,
propagation, FEC, receiver DSP, memory, scheduling, and display
presentation.

The correct target is therefore:

lower end-to-end presentation latency.

------------------------------------------------------------------------

12. THE COMPLETE LATENCY MODEL

PBUA defines six measurable latency components:

1.  Source processing
2.  Encode / RADIX mapping
3.  Physical transport
4.  Decode / FEC / reconstruction
5.  Presentation
6.  Wireless contention / retransmission tail

The sixth component becomes especially important in wireless operation
because average latency can look acceptable while occasional
retransmission events create large spikes.

The system should therefore optimize not only mean latency but also:

95th percentile latency

99th percentile latency

and, where relevant, higher tail percentiles.

------------------------------------------------------------------------

13. THE LOWER-LATENCY DESIGN STRATEGY

PBUA attacks latency through several independent mechanisms:

-   parallel wavelength transport
-   reduced serialization
-   hardware timestamping
-   dedicated optical PHY processing
-   direct DMA pathways
-   reduced memory copies
-   controlled buffering
-   adaptive FEC
-   adaptive modulation
-   deadline-aware scheduling
-   selective redundancy
-   direct framebuffer reconstruction
-   media-aware prioritization

The intended advantage is therefore architectural and system-level.

PBUA does not claim that photons travel faster than light.

------------------------------------------------------------------------

14. THE LOWER-ENERGY DESIGN STRATEGY

Energy becomes a first-class EL-40 variable rather than an afterthought.

The architecture attempts to reduce:

-   unnecessary optical channels
-   unnecessary radio links
-   excessive modulation complexity
-   unnecessary FEC processing
-   memory copies
-   duplicate transmission
-   retransmission
-   CPU intervention
-   idle laser/modulator power
-   unnecessary thermal-management load

The primary proposed metric is:

joules per successfully presented frame

and for audio:

joules per successfully presented sample interval.

This is more meaningful than simply comparing transmitter wattage.

------------------------------------------------------------------------

15. POWER-AWARE RESOURCE ACTIVATION

EL-40 can conceptually operate the photonic fabric as a variable-size
resource pool.

Heavy video:

more wavelengths active

Normal video:

fewer wavelengths where possible

Audio-only:

minimal protected transport resources

Idle:

unused optical/RF/DSP resources parked

The previously discussed 0.5–2 mW per active optical wavelength should
remain an engineering investigation target, not a demonstrated result.

------------------------------------------------------------------------

16. EL-40 — THE ADAPTIVE CONTROL LAYER

EL-40 is the system’s domain-neutral control and optimization layer.

It monitors:

-   optical link quality
-   wavelength stability
-   PAM mode
-   symbol rate
-   FEC correction burden
-   thermal state
-   power state
-   available bandwidth
-   wireless SNR/RSSI
-   radio MCS
-   retransmissions
-   mobility
-   frame deadlines
-   audio deadlines
-   synchronization state
-   interface capabilities

EL-40 does not need to perform every low-level PHY operation itself. It
coordinates specialized hardware engines and selects their operating
states.

Its central question is:

Which available physical configuration can deliver the required
information reliably within the required deadline and energy budget?

------------------------------------------------------------------------

17. EL-40 DOMAIN SELECTION POLICY

Conceptually:

    if optical_link_stable and deadline_ok:
        use optical for bulk media
        protect audio + synchronization
    elif optical_available_but_constrained:
        reduce wavelengths or PAM level
        preserve protected media timing
    elif free_space_optical_is_viable:
        use FSO for appropriate short-range traffic
    elif wireless_available:
        use compressed/adaptive wireless transport
        protect audio + timestamps
        reduce enhancement video
    else:
        preserve last-good-frame
        maintain audio if possible

The exact state machine remains an engineering task.

The principle is fixed:

use the simplest PHY that reliably satisfies the deadline.

------------------------------------------------------------------------

18. WIRELESS IS THE OPTIONAL CONTINUITY DOMAIN

The wireless system is deliberately not a 26-color WDM radio system.

Instead, the PBUA logical data representation is translated into the
appropriate radio PHY.

Conceptual mapping:

  -----------------------------------------------------------------------
  Optical PBUA                        Wireless equivalent
  ----------------------------------- -----------------------------------
  26 wavelength lanes                 MIMO streams / carrier aggregation
                                      / multi-link

  PAM-4/PAM-8                         QAM + MCS selection

  wavelength locking                  frequency/beam/link tracking

  WDM allocation                      channel/OFDMA resource allocation

  optical FEC                         wireless FEC families

  protected audio                     QoS/priority flow

  hardware timestamps                 network time synchronization

  sleep unused wavelengths            disable unused links/streams

  optical power control               RF transmit-power control
  -----------------------------------------------------------------------

This lets the wireless system inherit the adaptive philosophy of PBUA
without pretending that radio hardware can directly decode the optical
A–Z wavelength grid.

------------------------------------------------------------------------

19. QAM IS THE RADIO-SIDE COUNTERPART TO PAM

The two modulation families remain separate.

Optical: PAM-4 / PAM-8

Radio: QAM / MCS

PAM changes optical intensity levels. QAM changes radio constellation
states and, through MCS selection, combines modulation and coding
choices appropriate to the radio link.

EL-40 treats them as PHY-specific tools beneath the same media
scheduler.

------------------------------------------------------------------------

20. FREE-SPACE OPTICAL — THE MIDDLE DOMAIN

Free-space optical communication provides a useful intermediate path
between fiber and RF.

Possible uses include:

-   optical docking
-   dock-to-display
-   room-scale device-to-device transport
-   short-range high-bandwidth links
-   fixed or semi-fixed display links
-   Li-Fi-style networking

FSO remains subject to:

-   beam blockage
-   alignment
-   range
-   ambient-light conditions
-   environmental conditions

Therefore RF remains the continuity mechanism when optical wireless is
interrupted.

------------------------------------------------------------------------

21. CAMERA-TO-PBUA — “CAMERA SPEAKS A–Z”

The phrase does not mean the image sensor literally produces alphabet
letters.

The camera remains an image sensor and its internal electronics can
remain binary.

The pipeline is:

Camera sensor → image processing → PBUA Media Encoder → RADIX Mapper →
A–Z channel assignment → WDM/PAM → transport

The camera therefore becomes a structured PBUA media source.

Optional camera-side intelligence can identify:

-   motion
-   regions of interest
-   object boundaries
-   scene metadata
-   motion vectors
-   key-frame information

When wireless bandwidth is limited, prioritized information can be
transmitted first.

------------------------------------------------------------------------

22. AUDIO IS A PROTECTED MEDIA STREAM

Audio is treated as a protected timing stream rather than ordinary video
payload.

The system protects:

-   sample sequence
-   capture timestamp
-   presentation timestamp
-   synchronization information
-   clock relationship
-   FEC
-   priority

The priority order is:

1. Synchronization

2. Audio

3. Essential video

4. Enhancement video

When bandwidth collapses, enhancement video is sacrificed before the
audio timeline.

------------------------------------------------------------------------

23. AUDIO STILL ENDS AT A DAC AND SPEAKER

PBUA transports digital audio information.

The physical conversion remains:

digital samples → DAC → analog electrical signal → amplifier → speaker →
sound

PBUA does not claim that its optical alphabet itself produces sound.

The same principle applies to video:

PBUA information → framebuffer → display electronics → pixels.

------------------------------------------------------------------------

24. PMSE — PBUA MEDIA SYNCHRONIZATION ENGINE

The PBUA Media Synchronization Engine (PMSE) maintains the relationship
between:

-   capture time
-   audio sample time
-   frame time
-   transmission time
-   arrival time
-   reconstruction time
-   presentation time

A synchronization record can include:

Media Session ID → Source Clock ID → Frame ID → Audio Sample ID →
Capture Timestamp → Presentation Timestamp → Sequence Number → Payload →
FEC

Timing metadata can be attached to frame groups, audio blocks,
synchronization epochs, or transport transactions rather than every
pixel.

------------------------------------------------------------------------

25. CAPTURE TIME IS NOT PRESENTATION TIME

A camera may capture a frame at one time while the display presents it
later.

Likewise, an audio sample can be captured and presented at different
times.

PBUA explicitly models that difference so the architecture can measure
and control real end-to-end media delay.

This is essential to proving the latency claim.

------------------------------------------------------------------------

26. WAVELENGTH LOCKING AND THERMAL CONTROL

Twenty-six optical channels require stable wavelength separation.

The optical subsystem therefore requires:

-   wavelength monitoring
-   spectral locking
-   thermal feedback
-   guard bands
-   calibration
-   drift detection
-   channel health monitoring

The control loop becomes:

temperature → wavelength drift → signal quality → FEC burden →
modulation selection

If a channel becomes unstable, EL-40 can:

reduce power → lower PAM → lower symbol rate → deactivate channel →
redistribute traffic → switch domain

The recovery principle is:

REMOVE → REASSIGN → RECOVER

rather than allowing one weak wavelength to destabilize the entire
fabric.

------------------------------------------------------------------------

27. ERROR CORRECTION

The architecture uses layered error protection.

A possible implementation is:

outer Reed-Solomon-type protection + inner soft-decision LDPC or
polar-type protection

The exact coding architecture is a hardware-validation item.

A previously proposed post-FEC BER target such as <10^-15 must remain an
engineering target, not a demonstrated PBUA result.

EL-40 can use FEC correction burden as a link-quality signal.

Increasing correction burden can trigger:

PAM-8 → PAM-4

or

stronger FEC → lower symbol rate → wavelength reassignment → wireless
fallback.

------------------------------------------------------------------------

28. OPTICAL/WIRELESS DUPLICATION POLICY

The architecture does not continuously duplicate the complete
high-bandwidth video stream across every available link.

Instead, selective redundancy can protect:

-   audio
-   synchronization
-   control
-   critical metadata

Example:

Optical → primary video + audio

Wireless → synchronization/audio continuity

If the optical link fails, EL-40 can reduce video enhancement and
preserve the media session through wireless continuity.

This reduces redundant traffic and can reduce energy.

------------------------------------------------------------------------

29. UNIVERSAL PBUA GENERATION ADAPTER

The adapter becomes the compatibility membrane between generations.

It supports the conceptual sequence:

1.  legacy binary
2.  modern high-speed binary
3.  hybrid electrical/photonic
4.  PBUA optical
5.  free-space optical
6.  wireless continuity
7.  EL-40 coordinated PBUA

The display does not need to understand the A–Z transport language.

The adapter translates advanced PBUA transport into the framebuffer and
audio interfaces required by the output device.

------------------------------------------------------------------------

30. PUGC — PBUA UNIVERSAL GENERATION CONNECTOR

PUGC is a connector architecture rather than merely a new plug shape.

It can contain:

-   legacy electrical interface
-   high-speed electrical/hybrid interface
-   optical interface
-   wireless module interface
-   sideband control
-   power management
-   capability negotiation

The architecture can be implemented in:

-   display silicon
-   a display PCB
-   a docking station
-   an external adapter
-   a future photonic display controller
-   a replaceable module

------------------------------------------------------------------------

31. BACKWARD COMPATIBILITY — UPDATED TO THE MODERN ECOSYSTEM

The PBUA adapter should preserve compatibility with conventional display
and system interfaces.

The architecture should be designed to coexist with current interfaces
rather than pretending that they disappear immediately.

The 2026 baseline should account for modern high-speed interfaces
including:

-   HDMI 2.2
-   DisplayPort-family interfaces
-   eDP-family interfaces
-   PCI Express 7.0-class system interconnects
-   UCIe 3.0-class chiplet interconnects
-   Ethernet and other standardized network fabrics where applicable

HDMI 2.2 is currently the latest HDMI specification and defines up to 96
Gb/s signaling with next-generation FRL, while maintaining backward
compatibility with earlier HDMI technology. PCIe 7.0 was released in
2025 at 128 GT/s raw signaling and continues the PCIe focus on high
bandwidth, low power, and backward compatibility. UCIe 3.0 defines 48
and 64 GT/s data rates and adds power-management and low-latency
management features for chiplet systems.

PBUA should therefore be treated as an overlay/transport architecture
that can interface with these ecosystems, not as a replacement for their
standards.

------------------------------------------------------------------------

32. UNIVERSAL GENERATION NEGOTIATION

At connection time the source and adapter exchange:

-   generation
-   physical interface capability
-   RADIX mode
-   PAM capability
-   symbol rate
-   FEC profile
-   wavelength capability
-   timestamp capability
-   media format
-   audio capability
-   synchronization capability
-   power state

The highest mutually compatible mode is selected only when it satisfies
the actual deadline and energy constraints.

The newest mode is not automatically the best mode.

------------------------------------------------------------------------

33. UNIVERSAL FALLBACK LADDER

The conceptual fallback ladder becomes:

PBUA WDM + PAM-8

↓

PBUA WDM + PAM-4

↓

fewer active optical wavelengths

↓

hybrid optical/electrical

↓

FSO / Li-Fi

↓

Wi-Fi multi-link

↓

5G / future 6G

↓

HDMI / DisplayPort / eDP or other compatible electrical interface

↓

last-good-frame + protected audio

EL-40 can change the order based on measured conditions.

------------------------------------------------------------------------

34. FINAL DISPLAY RECEIVE PIPELINE

Advanced optical path:

WDM demultiplexing

↓

wavelength lock

↓

PAM detection

↓

A–Z/RADIX decoding

↓

FEC

↓

timestamp/sequence validation

↓

frame reconstruction

↓

DMA

↓

framebuffer

↓

pixel-format conversion if required

↓

display scanout

↓

panel

The objective is to minimize unnecessary copying and conversion between
transport and presentation.

------------------------------------------------------------------------

35. LEGACY DISPLAY PATH

A conventional source remains usable:

HDMI / DisplayPort / eDP

↓

receiver

↓

binary decode

↓

frame reconstruction

↓

DMA

↓

framebuffer

↓

display

PBUA photonic resources can remain powered down or in a low-power state
when they are not needed.

This is essential to prevent the universal adapter from consuming
unnecessary power merely because advanced hardware exists inside it.

------------------------------------------------------------------------

36. CURRENT STANDARD ALIGNMENT

The PBUA build-me-phase design should align its interfaces to real
standards wherever standards already exist.

Examples include:

PCIe 7.0 for high-speed system interconnect context.

UCIe 3.0 for chiplet-level interoperability and management.

HDMI 2.2 for modern high-bandwidth display compatibility.

DisplayPort/eDP families for display interoperability.

Wi-Fi multi-link and current IEEE WLAN generations for wireless
continuity.

5G and future 6G-compatible abstraction for cellular continuity.

The PBUA-specific portions remain proposed:

-   A–Z logical wavelength identities
-   26-channel PBUA mapping
-   EL-40 controller architecture
-   PBUA media encoding
-   PUGC connector architecture
-   PBUA universal frame representation
-   cross-domain optical/radio scheduling

------------------------------------------------------------------------

37. THE UPDATED PERFORMANCE CLAIM

The system is intended to target:

lower end-to-end latency

lower energy per delivered/presented bit or frame

higher aggregate throughput

lower serialization overhead

lower unnecessary memory movement

better media synchronization

graceful wireless fallback

These are targets.

The architecture must not present them as demonstrated facts until
measured in hardware.

------------------------------------------------------------------------

38. WHY THE CONCEPT CAN BE LOWER LATENCY

The proposed latency advantage comes from:

1.  Parallel WDM lanes reduce serialization.
2.  PAM increases information density per optical symbol.
3.  Dedicated hardware can reduce CPU intervention.
4.  DMA can reduce unnecessary copies.
5.  Hardware timestamps reduce timing uncertainty.
6.  EL-40 can reduce unnecessary queues and buffering.
7.  Adaptive FEC can prevent excessive correction delay.
8.  Selective redundancy avoids unnecessary traffic.
9.  Optical is preferred for high-volume fixed transport.
10. Wireless is used for continuity rather than forcing every workload
    through RF.

The important phrase is:

lower system latency, not faster-than-light propagation.

------------------------------------------------------------------------

39. WHY THE CONCEPT CAN BE LOWER ENERGY

The proposed energy advantage comes from:

1.  Optical transport for high-volume workloads where its measured
    joules/bit are favorable.
2.  Parallel completion that can shorten active time.
3.  Turning unused wavelengths off.
4.  Turning unused radio links off.
5.  Adaptive PAM and symbol rate.
6.  Adaptive radio MCS.
7.  Reduced retransmissions.
8.  Reduced memory copying.
9.  Direct DMA.
10. Selective redundancy.
11. Media-aware quality reduction.
12. Thermal-aware scheduling.

The correct metric is not merely peak power. It is total energy required
to successfully complete and present the workload.

------------------------------------------------------------------------

40. THE EL-40 ENERGY/LATENCY GOVERNOR

EL-40 continuously balances:

LATENCY + ENERGY + QUALITY + RELIABILITY + THERMAL STATE

A simplified optimization objective is:

minimize energy subject to the media deadline and required reliability.

If the lowest-power mode misses the deadline, EL-40 increases resources.

If a higher-power mode provides no useful deadline improvement, EL-40
reduces resources.

This makes lower energy a design objective rather than an accidental
benefit.

------------------------------------------------------------------------

41. WHAT HAPPENS WHEN BANDWIDTH COLLAPSES

PBUA does not simply fail from highest quality to nothing.

It degrades in layers:

enhancement video removed

→ resolution reduced

→ frame rate reduced if necessary

→ regions of interest prioritized

→ essential video preserved

→ audio and synchronization protected

→ last-good-frame maintained if necessary

This allows the media session to remain coherent even when the physical
transport changes.

------------------------------------------------------------------------

42. SYSTEM ARCHITECTURE DIAGRAM

                             CAMERA / MICROPHONE
                                      │
                                      ▼
                           BINARY-COMPATIBLE CAPTURE
                                      │
                                      ▼
                             PBUA MEDIA ENCODER
                                      │
                                      ▼
                                RADIX MAPPER
                                      │
                                      ▼
                             A–Z LOGICAL LAYER
                                      │
                                      ▼
                                EL-40 CONTROL
                                      │
                        ┌─────────────┴─────────────┐
                        │                           │
                        ▼                           ▼
                 OPTICAL STANDARD             WIRELESS OPTIONAL
                        │                           │
                  26 WDM LANES              QAM / MCS / MIMO
                        │                    OFDMA / MULTI-LINK
                   PAM-8 / PAM-4                    │
                        │                           │
                        └─────────────┬─────────────┘
                                      ▼
                               ADAPTIVE FEC
                                      │
                             HARDWARE TIMESTAMPS
                                      │
                                   PMSE
                                      │
                                      ▼
                         UNIVERSAL PBUA ADAPTER
                                      │
                                      ▼
                            FRAME RECONSTRUCTION
                                      │
                                      ▼
                                     DMA
                                      │
                                      ▼
                                FRAMEBUFFER
                                  │       │
                                  ▼       ▼
                               DISPLAY   AUDIO
                                            │
                                           DAC
                                            │
                                         AMPLIFIER
                                            │
                                         SPEAKER

------------------------------------------------------------------------

43. PUGC + UNIVERSAL ADAPTER HARDWARE BLOCKS

The proposed adapter contains:

A. Optical receiver/transmitter block

WDM source/demux, photodetectors, PAM detection, modulation, wavelength
monitoring.

B. Wireless module bay

Replaceable radio hardware for approved Wi-Fi/cellular/future
interfaces.

C. Legacy interface block

HDMI, DisplayPort, eDP and other supported interfaces.

D. EL-40 controller

Scheduling, power management, domain selection, telemetry and thermal
control.

E. PMSE block

Media clock and audio/video synchronization.

F. FEC/DSP block

Error correction, decoding, link-quality estimation and adaptive mode
control.

G. DMA/framebuffer block

Low-copy movement into the display pipeline.

H. Sideband/control block

Discovery, capability negotiation, firmware management, timing, power
state, emergency fallback.

------------------------------------------------------------------------

44. CHIPLET AND SYSTEM-IN-PACKAGE DIRECTION

The updated architecture should be compatible with modern chiplet design
rather than assuming one enormous monolithic PBUA die.

Possible partitions include:

-   optical source chiplet
-   micro-comb/resonator chiplet
-   modulator/detector photonic die
-   EL-40 control die
-   FEC/DSP die
-   wireless module
-   memory/DMA controller
-   display interface die

A UCIe-class package architecture provides a useful modern reference
point for modular chiplet integration, while PBUA-specific optical
interfaces would require their own PHY and packaging validation.

This modular strategy can improve development risk because individual
blocks can be tested independently.

------------------------------------------------------------------------

45. THERMAL ARCHITECTURE

PBUA remains a thermal system even though optical transport can reduce
resistive transport losses.

Heat can still be generated by:

-   laser/source electronics
-   modulators
-   driver electronics
-   photodetectors
-   DSP
-   FEC
-   memory
-   radio amplifiers
-   power-management circuits

EL-40 therefore monitors thermal state as a first-class variable.

If thermal margin falls, the controller can reduce:

optical power → PAM level → symbol rate → active wavelengths → DSP
workload → radio power

or shift traffic to another domain.

------------------------------------------------------------------------

46. THE “8G-CLASS” DESIGNATION

The architecture may be described as an 8G-class or
eighth-generation-style concept only as an architectural designation.

It is not an official telecommunications generation.

The concept is different from simply increasing cellular radio
frequency.

The proposed 8G-class idea is:

native high-radix organization + dense wavelength parallelism + adaptive
photonic transport + intelligent cross-domain scheduling.

The designation therefore describes the scale and architectural ambition
of the concept, not an existing industry standard.

------------------------------------------------------------------------

47. WHAT PBUA DOES NOT CLAIM

PBUA does not claim:

-   photons travel faster than light;
-   26 visible colors are naturally available as 26 channels;
-   26 wavelengths automatically equal a particular data rate;
-   PAM-8 automatically produces a particular throughput;
-   optical is always faster than radio;
-   optical is always more energy efficient than radio;
-   the PBUA architecture is already commercially standardized;
-   “8G” is already an official telecom generation;
-   existing Wi-Fi/5G hardware can directly decode A–Z optical
    wavelengths;
-   the full 26-channel architecture has already been demonstrated with
    the proposed EL-40 integration;
-   a particular latency or energy number has been proven without a
    prototype.

Every system-level performance advantage remains experimentally testable
rather than assumed.

------------------------------------------------------------------------

48. BUILD-ME PHASE — WHAT MUST ACTUALLY BE BUILT

The project remains in the build-me phase.

A practical development sequence is:

Phase 1 — Logical prototype

Implement the A–Z logical mapping, framing, synchronization, fallback
states, and media priorities in software.

Phase 2 — Single optical lane

Demonstrate PAM-4/PAM-8 transport, FEC, timestamping, thermal
monitoring, and reconstruction.

Phase 3 — Multi-wavelength prototype

Expand from a small number of wavelength lanes toward the 26-channel
target while measuring crosstalk, drift, power, and FEC burden.

Phase 4 — EL-40 control prototype

Close the control loop around wavelength selection, PAM selection, FEC,
power, thermal state, and deadlines.

Phase 5 — Adapter prototype

Implement PUGC/Universal PBUA Adapter with legacy electrical and optical
inputs.

Phase 6 — Dual-domain prototype

Add FSO and wireless continuity and verify that domain switching does
not duplicate or corrupt the media stream.

Phase 7 — Display/audio prototype

Measure source-to-framebuffer and source-to-speaker timing.

Phase 8 — Benchmarking

Compare the prototype against modern electronic and optical baselines
using identical workloads.

------------------------------------------------------------------------

49. REQUIRED BENCHMARKS

The prototype must measure:

-   end-to-end presentation latency
-   99th-percentile latency
-   energy per frame
-   energy per bit
-   energy per successfully delivered workload
-   throughput
-   BER
-   FEC correction rate
-   optical power
-   number of stable wavelengths
-   PAM-4 performance
-   PAM-8 performance
-   thermal drift
-   channel crosstalk
-   wavelength stability
-   retransmission rate
-   CPU utilization
-   memory-copy count
-   DMA utilization
-   audio/video synchronization error
-   domain-switch time
-   recovery time after optical blockage

These measurements determine whether PBUA actually achieves its intended
lower-latency/lower-energy outcome.

------------------------------------------------------------------------

50. MODERN INTERFACE TARGETS

The PBUA adapter should be designed around the contemporary ecosystem
rather than an outdated interface baseline.

The 2026 design reference includes:

HDMI 2.2 — current HDMI specification with up to 96 Gb/s and modern
high-resolution/high-refresh AV support.

PCIe 7.0 — current PCI-SIG base specification with 128 GT/s raw
signaling.

UCIe 3.0 — current open chiplet interconnect specification with 48/64
GT/s data rates and improved management/power features.

Wi-Fi multi-link architectures — wireless continuity and adaptive radio
transport.

5G and future 6G interfaces — mobile continuity.

DisplayPort/eDP ecosystems — display compatibility.

PBUA remains an overlay architecture rather than a replacement for these
standards.

------------------------------------------------------------------------

51. FINAL ENGINEERING PRINCIPLES

Light when light is available.

Radio when mobility or blockage requires it.

Use the simplest PHY that satisfies the deadline.

Use parallel optical channels for bulk transport.

Use PAM for optical modulation.

Use QAM/MCS for radio modulation.

Do not force 26 optical wavelength lanes onto conventional radio
spectrum.

Protect synchronization and audio before video enhancement.

Turn off unused wavelengths, radio links, and processing resources.

Reduce serialization and unnecessary memory movement.

Measure end-to-end presentation latency rather than photon propagation
speed.

Optimize total energy per successful presentation, not only peak power.

Maintain backward compatibility while introducing the new transport
layer.

------------------------------------------------------------------------

52. FINAL ARCHITECTURAL IDENTITY

PBUA DUAL-DOMAIN FABRIC

Optical Standard, Wireless Optional (OS/WO)

The final proposed system consists of:

-   EL-40 Adaptive Control
-   A–Z higher-radix logical layer
-   26 logical optical wavelength identities
-   WDM parallel transport
-   PAM-4/PAM-8 optical modulation
-   adaptive FEC
-   wavelength locking
-   thermal feedback
-   hardware timestamping
-   PBUA Media Synchronization Engine
-   protected audio transport
-   camera-to-PBUA encoding
-   free-space optical continuity
-   Wi-Fi/cellular wireless continuity
-   QAM/MCS radio adaptation
-   PUGC Universal Generation Connector
-   Universal PBUA Generation Adapter
-   direct DMA frame reconstruction
-   framebuffer translation
-   HDMI/DisplayPort/eDP compatibility
-   modern system/chiplet interoperability targets
-   adaptive power management
-   universal fallback

The system is not a claim that every existing communication technology
disappears.

It is a proposed unifying transport architecture in which:

photonic transport becomes the preferred high-capacity fabric; wireless
becomes the mobility and continuity layer; legacy electrical interfaces
remain available; and EL-40 decides how much hardware and which physical
domain should be active.

------------------------------------------------------------------------

53. FINAL ONE-LINE DEFINITION

PBUA Dual-Domain Fabric is a proposed post-binary transport architecture
in which EL-40 organizes information through a 26-symbol A–Z logical
photonic layer, transports high-volume data through parallel WDM with
adaptive PAM, uses QAM/MCS-based wireless links for mobility and
fallback, and translates every generation through a Universal PBUA
Adapter while optimizing end-to-end latency, energy, reliability,
synchronization, and compatibility.

------------------------------------------------------------------------

54. STATUS — BUILD-ME PHASE

Concept status: active architectural concept.

Target window: 2026–2030 for progressive prototypes and validation.

Current technology foundation: silicon photonics, silicon nitride
photonics, WDM, micro-comb research, PAM signaling, FEC, high-speed
chiplet interconnects, hardware timing, DMA, wireless adaptive
modulation, modern display interfaces, and optical networking.

Proposed integration: the complete PBUA A–Z logical layer, 26-channel
mapping, EL-40 adaptive domain control, PUGC/Universal Adapter, PMSE,
cross-domain media scheduling, and the lower-latency/lower-energy
optimization architecture.

Performance status: unproven until hardware benchmarking.

Material status: lower-hazard-material direction compared with the
earlier exotic implementation, not a claim of zero toxicity.

8G status: architectural/visionary designation, not an official telecom
generation.

26-color status: visual representation of 26 wavelength-defined logical
channels, not a claim of 26 natural visible colors.

Core development objective: build a measurable photonic transport system
that can demonstrate whether parallel higher-radix optical transport
plus EL-40 adaptive control actually reduces end-to-end latency and
energy for defined workloads.

------------------------------------------------------------------------

55. CURRENT STANDARD REFERENCES USED FOR THE REBUILD

The standards alignment in this revision was updated against current
official specification information available in 2026.

-   HDMI 2.2 is the latest HDMI specification and supports up to 96 Gb/s
    with next-generation Fixed Rate Link.
-   PCI Express 7.0 is the current approved PCIe Base Specification
    revision and defines 128 GT/s raw signaling.
-   UCIe 3.0 is the current UCIe specification and defines 48 and 64
    GT/s data rates plus enhanced manageability and power-saving
    functions.

These standards are references for interoperability and design context.
They do not establish PBUA itself as a standard.

------------------------------------------------------------------------

FINAL PROJECT STATEMENT

PBUA remains a concept in the build-me phase. The updated system keeps
the original A–Z post-binary vision but rebuilds it around a realistic
distinction between logical radix and physical wavelength, modern
silicon/silicon-nitride photonics, PAM-4/PAM-8, adaptive FEC, EL-40
scheduling, protected audio/video timing, Universal PBUA compatibility,
and the new PBUA Dual-Domain Fabric rule: optical is the preferred
high-capacity standard path, wireless is the optional
mobility/continuity path, and EL-40 activates only the resources
required to meet the deadline.

PBUA DUAL-DOMAIN FABRIC — FINAL CONCEPTUAL REBUILD

Optical Standard, Wireless Optional (OS/WO)

Updated Post-Binary A–Z Photonic System — High-Radix PAM / EL-40 Architecture

Conceptual 2026–2030 Development Target | Build-Me-Phase Specification

STATUS: CONCEPT / ARCHITECTURAL DESIGN IN BUILD-ME PHASE

This document defines a proposed architecture, not a completed product or established industry standard. Individual technologies used by the 
architecture are real and commercially or experimentally established, but the complete PBUA integration, exact 26-channel A–Z mapping, EL-40
control model, adapter architecture, and claimed system-level latency/energy advantages still 
require engineering, fabrication, interoperability testing, and benchmarking.

1. INTRODUCTION — THE UPDATED POST-BINARY PBUA CONCEPT

The Post-Binary Unified Architecture (PBUA) is a proposed higher-radix transport and media architecture intended to move beyond the limitations of 
heavily serialized binary data transport without requiring the immediate replacement of binary computing itself.

The original vision is retained: information can be organized as an A–Z logical photonic alphabet, represented by 26 distinct optical channel 
identities, with multiple amplitude states on each channel. The updated architecture makes that vision more practical by separating the logical
alphabet from the physical implementation.

The system is therefore not literally a computer in which every transistor stops using binary 0 and 1. CPUs, GPUs, memory, sensors, DACs,
operating systems, and conventional peripherals can remain binary internally. The proposed post-binary transition occurs primarily in the 
way high-volume information is organized, transported, synchronized, and reconstructed.

The updated architecture is built around one central idea:

Use parallel photonic transport when it provides the best path; use wireless when mobility or blockage requires it; and let EL-40 select
the simplest physical configuration that meets the media deadline with the lowest practical energy cost.

This becomes the PBUA Dual-Domain Fabric — Optical Standard, Wireless Optional (OS/WO).

The system is deliberately being rebuilt as a realistic 2026–2030 development concept rather than presented as an already manufactured 8G product.

2. WHAT “POST-BINARY” MEANS IN THIS ARCHITECTURE

PBUA uses “post-binary” as an architectural term.

The conventional model is dominated by binary digital representation and serialized transport:

binary data → serializer → electrical link → receiver → reconstruction

PBUA proposes:

binary-compatible source → higher-radix mapper → parallel optical/wireless PHY → synchronized reconstruction → conventional media output

The key change is therefore not the disappearance of binary logic. It is the movement of high-bandwidth data through a higher-radix, parallel,
adaptive transport layer.

The PBUA system can consequently coexist with existing binary computers. A conventional computer can send HDMI, DisplayPort, PCIe-class,
Ethernet, USB, or other supported data into the PBUA adapter. A PBUA-capable source can instead use the proposed A–Z/WDM/PAM transport. 
The receiver translates the result back into ordinary pixels, audio samples, or application data where required.

3. THE UPDATED CENTRAL ARCHITECTURE

The complete system is organized as:

SOURCE → PBUA MEDIA/TRANSPORT ENCODER → RADIX MAPPER → EL-40 → DUAL-DOMAIN PHY → FEC/TIMING → UNIVERSAL PBUA ADAPTER → FRAME/AUDIO RECONSTRUCTION → OUTPUT

The dual-domain PHY contains:

Optical Standard Port

Free-Space Optical continuity option

Wireless Optional Port

Legacy electrical/high-speed compatibility port

Control sideband

The optical domain is preferred for high-volume data when a suitable path exists.

The wireless domain is not a second copy of the 26-channel optical system. It is a continuity and mobility layer using appropriate radio PHYs such as
QAM/MCS, MIMO, OFDMA, carrier aggregation, and multi-link operation where supported.

4. PBUA DUAL-DOMAIN FABRIC — THE NEW SYSTEM-WIDE RULE

The updated PBUA rule is:

OPTICAL WHEN AVAILABLE.

Use guided photonics, integrated silicon photonics, optical docking, or another appropriate optical path for large data transfers when the measured
link can satisfy the deadline and energy budget.

WIRELESS WHEN MOBILITY OR BLOCKAGE REQUIRES IT.

Use Wi-Fi, cellular, or another approved wireless PHY when the user is mobile, the optical path is unavailable, the beam is blocked, or
untethered operation is required.

DO NOT FORCE THE 26 A–Z OPTICAL WDM CHANNELS INTO CONVENTIONAL RADIO SPECTRUM.

The wireless system translates the PBUA information representation into its native radio modulation and coding system.

This separation makes the architecture more realistic and prevents the optical and radio portions from being treated as if they were physically
identical technologies.

5. ONE ELECTROMAGNETIC FAMILY — DIFFERENT PHYSICAL DOMAINS

Optical photons and radio photons belong to the same electromagnetic family. They differ in frequency, wavelength, propagation environment,
hardware, and application.

The architecture therefore uses a hierarchy of physical transport domains:

Domain

Approximate region

PBUA role

Guided optical

Telecom infrared, e.g. 1310–1550 nm class

Preferred high-capacity fabric

Free-space optical

IR or visible optical bands

Short-range optical wireless / docking

Wi-Fi / cellular

RF, microwave, mmWave and future bands

Mobility and blocked-path continuity

Display/camera optics

Visible optical band

Human media capture/presentation

The system does not claim that one photon type is inherently faster. The optimization concerns the total system path: serialization, queueing, 
encoding, FEC, memory movement, retransmission, presentation timing, and power.

6. THE A–Z ALPHABET — UPDATED COLOR TERMINOLOGY

The original visual language used 26 colors. The engineering version must distinguish the visual metaphor from the physical implementation.

A–Z represents 26 logical optical channel identities.

Each identity is assigned to a stabilized wavelength channel in the optical implementation.

Therefore:

A = optical channel 1
B = optical channel 2
...
Z = optical channel 26

The diagrams may color-code these channels for human understanding. Those colors are a visualization of the channel identities. They are not a 
claim that the physical device contains exactly 26 naturally occurring visible colors.

The preferred physical implementation is a set of wavelength-defined optical channels, potentially in telecom infrared regions, with the exact
wavelengths, spacing, guard bands, source architecture, and channel count determined by optical engineering and standards compatibility.

This correction preserves the original A–Z idea while making it technically precise.

7. HIGH-RADIX ORGANIZATION

The A–Z layer is a higher-radix logical organization.

A 26-symbol alphabet has:

log2(26) ≈ 4.70 bits per logical symbol

before coding, framing, modulation, synchronization, and implementation overhead.

PBUA then separates three concepts:

RADIX — how information is organized logically.

WDM — how multiple wavelength-defined channels are transported in parallel.

PAM — how amplitude states are represented within each optical channel.

This separation is central to the updated architecture.

The system does not require one optical carrier to distinguish 26 fragile amplitude levels.

Instead:

26 stabilized wavelength lanes + PAM-4/PAM-8 per lane + FEC + parallel detection.

8. PAM-4 AND PAM-8

PAM provides multiple amplitude states on each optical lane.

PAM-4 provides four amplitude states and is the more conservative operating mode.

PAM-8 provides eight amplitude states and is the higher-capacity proposed mode.

The system therefore has adaptive optical modulation:

PAM-8 → PAM-4 → lower symbol rate / fewer channels → alternate domain

when signal quality, thermal state, FEC burden, or power constraints require it.

The architecture does not assume PAM-8 is always superior. A lower-order mode can be preferable when it reduces errors, retransmissions, DSP work, or 
energy per successfully delivered frame.

9. MICRO-COMB / SILICON-NITRIDE IMPLEMENTATION DIRECTION

The preferred conceptual source architecture is a silicon-photonics or silicon-nitride photonics platform using integrated wavelength generation 
rather than a large independent laser array.

A micro-comb can provide a set of evenly spaced optical lines from a pumped resonator. In the PBUA concept, the usable subset would be selected
and stabilized to create the desired A–Z channel grid.

The architecture may use:

silicon photonics

silicon nitride photonics

integrated micro-combs

minimal heterogeneous III–V or other high-performance gain/source material where necessary

conventional semiconductor doping and control structures

integrated modulators

photodetectors

wavelength monitoring

thermal control

This is a proposed implementation direction, not a claim that a production-ready 26-channel PBUA micro-comb chip already exists.

10. MATERIAL AND MANUFACTURING OBJECTIVE

The updated concept deliberately moves away from earlier exotic-crystal assumptions.

The bulk platform is intended to rely on silicon/silicon-nitride photonics and established semiconductor processing. Minimal specialized III–V or
other gain/source material may still be required.

The objective is to reduce dependence on large volumes of high-hazard or scarce optical source materials and to simplify manufacturing compared
with an architecture built around extensive exotic photonic materials.

The system must not be described as non-toxic. Semiconductor and photonic manufacturing still involves hazardous chemicals, high-temperature 
processing, cleaning, deposition, etching, and waste-management requirements.

The defensible goal is:

lower material-hazard and scarcity burden relative to the earlier proposed architecture, while retaining practical photonic functionality.

11. WHY PARALLELISM IS CENTRAL TO LOWER LATENCY

The lower-latency concept does not depend on photons traveling faster than light.

It depends on reducing the amount of information that must wait in a serialized pipeline.

A single serialized path resembles:

A → B → C → D → E → F → ...

PBUA proposes multiple wavelength lanes operating simultaneously:

λ1 | λ2 | λ3 | ... | λ26

The workload can be divided across independently recoverable groups. This attacks serialization and can increase aggregate transport capacity.

However, 26 channels do not automatically create 26× lower latency. Actual latency depends on source processing, encoding, modulation, 
propagation, FEC, receiver DSP, memory, scheduling, and display presentation.

The correct target is therefore:

lower end-to-end presentation latency.

12. THE COMPLETE LATENCY MODEL

PBUA defines six measurable latency components:

Source processing

Encode / RADIX mapping

Physical transport

Decode / FEC / reconstruction

Presentation

Wireless contention / retransmission tail

The sixth component becomes especially important in wireless operation because average latency can look acceptable while occasional
retransmission events create large spikes.

The system should therefore optimize not only mean latency but also:

95th percentile latency

99th percentile latency

and, where relevant, higher tail percentiles.

13. THE LOWER-LATENCY DESIGN STRATEGY

PBUA attacks latency through several independent mechanisms:

parallel wavelength transport

reduced serialization

hardware timestamping

dedicated optical PHY processing

direct DMA pathways

reduced memory copies

controlled buffering

adaptive FEC

adaptive modulation

deadline-aware scheduling

selective redundancy

direct framebuffer reconstruction

media-aware prioritization

The intended advantage is therefore architectural and system-level.

PBUA does not claim that photons travel faster than light.

14. THE LOWER-ENERGY DESIGN STRATEGY

Energy becomes a first-class EL-40 variable rather than an afterthought.

The architecture attempts to reduce:

unnecessary optical channels

unnecessary radio links

excessive modulation complexity

unnecessary FEC processing

memory copies

duplicate transmission

retransmission

CPU intervention

idle laser/modulator power

unnecessary thermal-management load

The primary proposed metric is:

joules per successfully presented frame

and for audio:

joules per successfully presented sample interval.

This is more meaningful than simply comparing transmitter wattage.

15. POWER-AWARE RESOURCE ACTIVATION

EL-40 can conceptually operate the photonic fabric as a variable-size resource pool.

Heavy video:

more wavelengths active

Normal video:

fewer wavelengths where possible

Audio-only:

minimal protected transport resources

Idle:

unused optical/RF/DSP resources parked

The previously discussed 0.5–2 mW per active optical wavelength should remain an engineering investigation target, not a demonstrated result.

16. EL-40 — THE ADAPTIVE CONTROL LAYER

EL-40 is the system's domain-neutral control and optimization layer.

It monitors:

optical link quality

wavelength stability

PAM mode

symbol rate

FEC correction burden

thermal state

power state

available bandwidth

wireless SNR/RSSI

radio MCS

retransmissions

mobility

frame deadlines

audio deadlines

synchronization state

interface capabilities

EL-40 does not need to perform every low-level PHY operation itself. It coordinates specialized hardware engines and selects their operating states.

Its central question is:

Which available physical configuration can deliver the required information reliably within the required deadline and energy budget?

17. EL-40 DOMAIN SELECTION POLICY

Conceptually:

if optical_link_stable and deadline_ok:
    use optical for bulk media
    protect audio + synchronization
elif optical_available_but_constrained:
    reduce wavelengths or PAM level
    preserve protected media timing
elif free_space_optical_is_viable:
    use FSO for appropriate short-range traffic
elif wireless_available:
    use compressed/adaptive wireless transport
    protect audio + timestamps
    reduce enhancement video
else:
    preserve last-good-frame
    maintain audio if possible

The exact state machine remains an engineering task.

The principle is fixed:

use the simplest PHY that reliably satisfies the deadline.

18. WIRELESS IS THE OPTIONAL CONTINUITY DOMAIN

The wireless system is deliberately not a 26-color WDM radio system.

Instead, the PBUA logical data representation is translated into the appropriate radio PHY.

Conceptual mapping:

Optical PBUA

Wireless equivalent

26 wavelength lanes

MIMO streams / carrier aggregation / multi-link

PAM-4/PAM-8

QAM + MCS selection

wavelength locking

frequency/beam/link tracking

WDM allocation

channel/OFDMA resource allocation

optical FEC

wireless FEC families

protected audio

QoS/priority flow

hardware timestamps

network time synchronization

sleep unused wavelengths

disable unused links/streams

optical power control

RF transmit-power control

This lets the wireless system inherit the adaptive philosophy of PBUA without pretending that radio hardware can directly decode the optical A–Z 
wavelength grid.

19. QAM IS THE RADIO-SIDE COUNTERPART TO PAM

The two modulation families remain separate.

Optical: PAM-4 / PAM-8

Radio: QAM / MCS

PAM changes optical intensity levels. QAM changes radio constellation states and, through MCS selection, combines modulation and coding choices 
appropriate to the radio link.

EL-40 treats them as PHY-specific tools beneath the same media scheduler.

20. FREE-SPACE OPTICAL — THE MIDDLE DOMAIN

Free-space optical communication provides a useful intermediate path between fiber and RF.

Possible uses include:

optical docking

dock-to-display

room-scale device-to-device transport

short-range high-bandwidth links

fixed or semi-fixed display links

Li-Fi-style networking

FSO remains subject to:

beam blockage

alignment

range

ambient-light conditions

environmental conditions

Therefore RF remains the continuity mechanism when optical wireless is interrupted.

21. CAMERA-TO-PBUA — “CAMERA SPEAKS A–Z”

The phrase does not mean the image sensor literally produces alphabet letters.

The camera remains an image sensor and its internal electronics can remain binary.

The pipeline is:

Camera sensor → image processing → PBUA Media Encoder → RADIX Mapper → A–Z channel assignment → WDM/PAM → transport

The camera therefore becomes a structured PBUA media source.

Optional camera-side intelligence can identify:

motion

regions of interest

object boundaries

scene metadata

motion vectors

key-frame information

When wireless bandwidth is limited, prioritized information can be transmitted first.

22. AUDIO IS A PROTECTED MEDIA STREAM

Audio is treated as a protected timing stream rather than ordinary video payload.

The system protects:

sample sequence

capture timestamp

presentation timestamp

synchronization information

clock relationship

FEC

priority

The priority order is:

1. Synchronization

2. Audio

3. Essential video

4. Enhancement video

When bandwidth collapses, enhancement video is sacrificed before the audio timeline.

23. AUDIO STILL ENDS AT A DAC AND SPEAKER

PBUA transports digital audio information.

The physical conversion remains:

digital samples → DAC → analog electrical signal → amplifier → speaker → sound

PBUA does not claim that its optical alphabet itself produces sound.

The same principle applies to video:

PBUA information → framebuffer → display electronics → pixels.

24. PMSE — PBUA MEDIA SYNCHRONIZATION ENGINE

The PBUA Media Synchronization Engine (PMSE) maintains the relationship between:

capture time

audio sample time

frame time

transmission time

arrival time

reconstruction time

presentation time

A synchronization record can include:

Media Session ID → Source Clock ID → Frame ID → Audio Sample ID → Capture Timestamp → Presentation Timestamp → Sequence Number → Payload → FEC

Timing metadata can be attached to frame groups, audio blocks, synchronization epochs, or transport transactions rather than every pixel.

25. CAPTURE TIME IS NOT PRESENTATION TIME

A camera may capture a frame at one time while the display presents it later.

Likewise, an audio sample can be captured and presented at different times.

PBUA explicitly models that difference so the architecture can measure and control real end-to-end media delay.

This is essential to proving the latency claim.

26. WAVELENGTH LOCKING AND THERMAL CONTROL

Twenty-six optical channels require stable wavelength separation.

The optical subsystem therefore requires:

wavelength monitoring

spectral locking

thermal feedback

guard bands

calibration

drift detection

channel health monitoring

The control loop becomes:

temperature → wavelength drift → signal quality → FEC burden → modulation selection

If a channel becomes unstable, EL-40 can:

reduce power → lower PAM → lower symbol rate → deactivate channel → redistribute traffic → switch domain

The recovery principle is:

REMOVE → REASSIGN → RECOVER

rather than allowing one weak wavelength to destabilize the entire fabric.

27. ERROR CORRECTION

The architecture uses layered error protection.

A possible implementation is:

outer Reed-Solomon-type protection + inner soft-decision LDPC or polar-type protection

The exact coding architecture is a hardware-validation item.

A previously proposed post-FEC BER target such as <10^-15 must remain an engineering target, not a demonstrated PBUA result.

EL-40 can use FEC correction burden as a link-quality signal.

Increasing correction burden can trigger:

PAM-8 → PAM-4

or

stronger FEC → lower symbol rate → wavelength reassignment → wireless fallback.

28. OPTICAL/WIRELESS DUPLICATION POLICY

The architecture does not continuously duplicate the complete high-bandwidth video stream across every available link.

Instead, selective redundancy can protect:

audio

synchronization

control

critical metadata

Example:

Optical → primary video + audio

Wireless → synchronization/audio continuity

If the optical link fails, EL-40 can reduce video enhancement and preserve the media session through wireless continuity.

This reduces redundant traffic and can reduce energy.

29. UNIVERSAL PBUA GENERATION ADAPTER

The adapter becomes the compatibility membrane between generations.

It supports the conceptual sequence:

legacy binary

modern high-speed binary

hybrid electrical/photonic

PBUA optical

free-space optical

wireless continuity

EL-40 coordinated PBUA

The display does not need to understand the A–Z transport language.

The adapter translates advanced PBUA transport into the framebuffer and audio interfaces required by the output device.

30. PUGC — PBUA UNIVERSAL GENERATION CONNECTOR

PUGC is a connector architecture rather than merely a new plug shape.

It can contain:

legacy electrical interface

high-speed electrical/hybrid interface

optical interface

wireless module interface

sideband control

power management

capability negotiation

The architecture can be implemented in:

display silicon

a display PCB

a docking station

an external adapter

a future photonic display controller

a replaceable module

31. BACKWARD COMPATIBILITY — UPDATED TO THE MODERN ECOSYSTEM

The PBUA adapter should preserve compatibility with conventional display and system interfaces.

The architecture should be designed to coexist with current interfaces rather than pretending that they disappear immediately.

The 2026 baseline should account for modern high-speed interfaces including:

HDMI 2.2

DisplayPort-family interfaces

eDP-family interfaces

PCI Express 7.0-class system interconnects

UCIe 3.0-class chiplet interconnects

Ethernet and other standardized network fabrics where applicable

HDMI 2.2 is currently the latest HDMI specification and defines up to 96 Gb/s signaling with next-generation FRL, while maintaining backward 
compatibility with earlier HDMI technology. PCIe 7.0 was released in 2025 at 128 GT/s raw signaling and continues the PCIe focus on high bandwidth,
low power, and backward compatibility. UCIe 3.0 defines 48 and 64 GT/s data rates and adds power-management and low-latency management features for
chiplet systems.

PBUA should therefore be treated as an overlay/transport architecture that can interface with these ecosystems, not as a replacement for their standards.

32. UNIVERSAL GENERATION NEGOTIATION

At connection time the source and adapter exchange:

generation

physical interface capability

RADIX mode

PAM capability

symbol rate

FEC profile

wavelength capability

timestamp capability

media format

audio capability

synchronization capability

power state

The highest mutually compatible mode is selected only when it satisfies the actual deadline and energy constraints.

The newest mode is not automatically the best mode.

33. UNIVERSAL FALLBACK LADDER

The conceptual fallback ladder becomes:

PBUA WDM + PAM-8

↓

PBUA WDM + PAM-4

↓

fewer active optical wavelengths

↓

hybrid optical/electrical

↓

FSO / Li-Fi

↓

Wi-Fi multi-link

↓

5G / future 6G

↓

HDMI / DisplayPort / eDP or other compatible electrical interface

↓

last-good-frame + protected audio

EL-40 can change the order based on measured conditions.

34. FINAL DISPLAY RECEIVE PIPELINE

Advanced optical path:

WDM demultiplexing

↓

wavelength lock

↓

PAM detection

↓

A–Z/RADIX decoding

↓

FEC

↓

timestamp/sequence validation

↓

frame reconstruction

↓

DMA

↓

framebuffer

↓

pixel-format conversion if required

↓

display scanout

↓

panel

The objective is to minimize unnecessary copying and conversion between transport and presentation.

35. LEGACY DISPLAY PATH

A conventional source remains usable:

HDMI / DisplayPort / eDP

↓

receiver

↓

binary decode

↓

frame reconstruction

↓

DMA

↓

framebuffer

↓

display

PBUA photonic resources can remain powered down or in a low-power state when they are not needed.

This is essential to prevent the universal adapter from consuming unnecessary power merely because advanced hardware exists inside it.

36. CURRENT STANDARD ALIGNMENT

The PBUA build-me-phase design should align its interfaces to real standards wherever standards already exist.

Examples include:

PCIe 7.0 for high-speed system interconnect context.

UCIe 3.0 for chiplet-level interoperability and management.

HDMI 2.2 for modern high-bandwidth display compatibility.

DisplayPort/eDP families for display interoperability.

Wi-Fi multi-link and current IEEE WLAN generations for wireless continuity.

5G and future 6G-compatible abstraction for cellular continuity.

The PBUA-specific portions remain proposed:

A–Z logical wavelength identities

26-channel PBUA mapping

EL-40 controller architecture

PBUA media encoding

PUGC connector architecture

PBUA universal frame representation

cross-domain optical/radio scheduling

37. THE UPDATED PERFORMANCE CLAIM

The system is intended to target:

lower end-to-end latency

lower energy per delivered/presented bit or frame

higher aggregate throughput

lower serialization overhead

lower unnecessary memory movement

better media synchronization

graceful wireless fallback

These are targets.

The architecture must not present them as demonstrated facts until measured in hardware.

38. WHY THE CONCEPT CAN BE LOWER LATENCY

The proposed latency advantage comes from:

Parallel WDM lanes reduce serialization.

PAM increases information density per optical symbol.

Dedicated hardware can reduce CPU intervention.

DMA can reduce unnecessary copies.

Hardware timestamps reduce timing uncertainty.

EL-40 can reduce unnecessary queues and buffering.

Adaptive FEC can prevent excessive correction delay.

Selective redundancy avoids unnecessary traffic.

Optical is preferred for high-volume fixed transport.

Wireless is used for continuity rather than forcing every workload through RF.

The important phrase is:

lower system latency, not faster-than-light propagation.

39. WHY THE CONCEPT CAN BE LOWER ENERGY

The proposed energy advantage comes from:

Optical transport for high-volume workloads where its measured joules/bit are favorable.

Parallel completion that can shorten active time.

Turning unused wavelengths off.

Turning unused radio links off.

Adaptive PAM and symbol rate.

Adaptive radio MCS.

Reduced retransmissions.

Reduced memory copying.

Direct DMA.

Selective redundancy.

Media-aware quality reduction.

Thermal-aware scheduling.

The correct metric is not merely peak power. It is total energy required to successfully complete and present the workload.

40. THE EL-40 ENERGY/LATENCY GOVERNOR

EL-40 continuously balances:

LATENCY + ENERGY + QUALITY + RELIABILITY + THERMAL STATE

A simplified optimization objective is:

minimize energy subject to the media deadline and required reliability.

If the lowest-power mode misses the deadline, EL-40 increases resources.

If a higher-power mode provides no useful deadline improvement, EL-40 reduces resources.

This makes lower energy a design objective rather than an accidental benefit.

41. WHAT HAPPENS WHEN BANDWIDTH COLLAPSES

PBUA does not simply fail from highest quality to nothing.

It degrades in layers:

enhancement video removed

→ resolution reduced

→ frame rate reduced if necessary

→ regions of interest prioritized

→ essential video preserved

→ audio and synchronization protected

→ last-good-frame maintained if necessary

This allows the media session to remain coherent even when the physical transport changes.

42. SYSTEM ARCHITECTURE DIAGRAM

                         CAMERA / MICROPHONE
                                  │
                                  ▼
                       BINARY-COMPATIBLE CAPTURE
                                  │
                                  ▼
                         PBUA MEDIA ENCODER
                                  │
                                  ▼
                            RADIX MAPPER
                                  │
                                  ▼
                         A–Z LOGICAL LAYER
                                  │
                                  ▼
                            EL-40 CONTROL
                                  │
                    ┌─────────────┴─────────────┐
                    │                           │
                    ▼                           ▼
             OPTICAL STANDARD             WIRELESS OPTIONAL
                    │                           │
              26 WDM LANES              QAM / MCS / MIMO
                    │                    OFDMA / MULTI-LINK
               PAM-8 / PAM-4                    │
                    │                           │
                    └─────────────┬─────────────┘
                                  ▼
                           ADAPTIVE FEC
                                  │
                         HARDWARE TIMESTAMPS
                                  │
                               PMSE
                                  │
                                  ▼
                     UNIVERSAL PBUA ADAPTER
                                  │
                                  ▼
                        FRAME RECONSTRUCTION
                                  │
                                  ▼
                                 DMA
                                  │
                                  ▼
                            FRAMEBUFFER
                              │       │
                              ▼       ▼
                           DISPLAY   AUDIO
                                        │
                                       DAC
                                        │
                                     AMPLIFIER
                                        │
                                     SPEAKER

43. PUGC + UNIVERSAL ADAPTER HARDWARE BLOCKS

The proposed adapter contains:

A. Optical receiver/transmitter block

WDM source/demux, photodetectors, PAM detection, modulation, wavelength monitoring.

B. Wireless module bay

Replaceable radio hardware for approved Wi-Fi/cellular/future interfaces.

C. Legacy interface block

HDMI, DisplayPort, eDP and other supported interfaces.

D. EL-40 controller

Scheduling, power management, domain selection, telemetry and thermal control.

E. PMSE block

Media clock and audio/video synchronization.

F. FEC/DSP block

Error correction, decoding, link-quality estimation and adaptive mode control.

G. DMA/framebuffer block

Low-copy movement into the display pipeline.

H. Sideband/control block

Discovery, capability negotiation, firmware management, timing, power state, emergency fallback.

44. CHIPLET AND SYSTEM-IN-PACKAGE DIRECTION

The updated architecture should be compatible with modern chiplet design rather than assuming one enormous monolithic PBUA die.

Possible partitions include:

optical source chiplet

micro-comb/resonator chiplet

modulator/detector photonic die

EL-40 control die

FEC/DSP die

wireless module

memory/DMA controller

display interface die

A UCIe-class package architecture provides a useful modern reference point for modular chiplet integration, while PBUA-specific optical interfaces 
would require their own PHY and packaging validation.

This modular strategy can improve development risk because individual blocks can be tested independently.

45. THERMAL ARCHITECTURE

PBUA remains a thermal system even though optical transport can reduce resistive transport losses.

Heat can still be generated by:

laser/source electronics

modulators

driver electronics

photodetectors

DSP

FEC

memory

radio amplifiers

power-management circuits

EL-40 therefore monitors thermal state as a first-class variable.

If thermal margin falls, the controller can reduce:

optical power → PAM level → symbol rate → active wavelengths → DSP workload → radio power

or shift traffic to another domain.

46. THE “8G-CLASS” DESIGNATION

The architecture may be described as an 8G-class or eighth-generation-style concept only as an architectural designation.

It is not an official telecommunications generation.

The concept is different from simply increasing cellular radio frequency.

The proposed 8G-class idea is:

native high-radix organization + dense wavelength parallelism + adaptive photonic transport + intelligent cross-domain scheduling.

The designation therefore describes the scale and architectural ambition of the concept, not an existing industry standard.

47. WHAT PBUA DOES NOT CLAIM

PBUA does not claim:

photons travel faster than light;

26 visible colors are naturally available as 26 channels;

26 wavelengths automatically equal a particular data rate;

PAM-8 automatically produces a particular throughput;

optical is always faster than radio;

optical is always more energy efficient than radio;

the PBUA architecture is already commercially standardized;

“8G” is already an official telecom generation;

existing Wi-Fi/5G hardware can directly decode A–Z optical wavelengths;

the full 26-channel architecture has already been demonstrated with the proposed EL-40 integration;

a particular latency or energy number has been proven without a prototype.

Every system-level performance advantage remains experimentally testable rather than assumed.

48. BUILD-ME PHASE — WHAT MUST ACTUALLY BE BUILT

The project remains in the build-me phase.

A practical development sequence is:

Phase 1 — Logical prototype

Implement the A–Z logical mapping, framing, synchronization, fallback states, and media priorities in software.

Phase 2 — Single optical lane

Demonstrate PAM-4/PAM-8 transport, FEC, timestamping, thermal monitoring, and reconstruction.

Phase 3 — Multi-wavelength prototype

Expand from a small number of wavelength lanes toward the 26-channel target while measuring crosstalk, drift, power, and FEC burden.

Phase 4 — EL-40 control prototype

Close the control loop around wavelength selection, PAM selection, FEC, power, thermal state, and deadlines.

Phase 5 — Adapter prototype

Implement PUGC/Universal PBUA Adapter with legacy electrical and optical inputs.

Phase 6 — Dual-domain prototype

Add FSO and wireless continuity and verify that domain switching does not duplicate or corrupt the media stream.

Phase 7 — Display/audio prototype

Measure source-to-framebuffer and source-to-speaker timing.

Phase 8 — Benchmarking

Compare the prototype against modern electronic and optical baselines using identical workloads.

49. REQUIRED BENCHMARKS

The prototype must measure:

end-to-end presentation latency

99th-percentile latency

energy per frame

energy per bit

energy per successfully delivered workload

throughput

BER

FEC correction rate

optical power

number of stable wavelengths

PAM-4 performance

PAM-8 performance

thermal drift

channel crosstalk

wavelength stability

retransmission rate

CPU utilization

memory-copy count

DMA utilization

audio/video synchronization error

domain-switch time

recovery time after optical blockage

These measurements determine whether PBUA actually achieves its intended lower-latency/lower-energy outcome.

50. MODERN INTERFACE TARGETS

The PBUA adapter should be designed around the contemporary ecosystem rather than an outdated interface baseline.

The 2026 design reference includes:

HDMI 2.2 — current HDMI specification with up to 96 Gb/s and modern high-resolution/high-refresh AV support.

PCIe 7.0 — current PCI-SIG base specification with 128 GT/s raw signaling.

UCIe 3.0 — current open chiplet interconnect specification with 48/64 GT/s data rates and improved management/power features.

Wi-Fi multi-link architectures — wireless continuity and adaptive radio transport.

5G and future 6G interfaces — mobile continuity.

DisplayPort/eDP ecosystems — display compatibility.

PBUA remains an overlay architecture rather than a replacement for these standards.

51. FINAL ENGINEERING PRINCIPLES

Light when light is available.

Radio when mobility or blockage requires it.

Use the simplest PHY that satisfies the deadline.

Use parallel optical channels for bulk transport.

Use PAM for optical modulation.

Use QAM/MCS for radio modulation.

Do not force 26 optical wavelength lanes onto conventional radio spectrum.

Protect synchronization and audio before video enhancement.

Turn off unused wavelengths, radio links, and processing resources.

Reduce serialization and unnecessary memory movement.

Measure end-to-end presentation latency rather than photon propagation speed.

Optimize total energy per successful presentation, not only peak power.

Maintain backward compatibility while introducing the new transport layer.

52. FINAL ARCHITECTURAL IDENTITY

PBUA DUAL-DOMAIN FABRIC

Optical Standard, Wireless Optional (OS/WO)

The final proposed system consists of:

EL-40 Adaptive Control

A–Z higher-radix logical layer

26 logical optical wavelength identities

WDM parallel transport

PAM-4/PAM-8 optical modulation

adaptive FEC

wavelength locking

thermal feedback

hardware timestamping

PBUA Media Synchronization Engine

protected audio transport

camera-to-PBUA encoding

free-space optical continuity

Wi-Fi/cellular wireless continuity

QAM/MCS radio adaptation

PUGC Universal Generation Connector

Universal PBUA Generation Adapter

direct DMA frame reconstruction

framebuffer translation

HDMI/DisplayPort/eDP compatibility

modern system/chiplet interoperability targets

adaptive power management

universal fallback

The system is not a claim that every existing communication technology disappears.

It is a proposed unifying transport architecture in which:

photonic transport becomes the preferred high-capacity fabric; wireless becomes the mobility and continuity layer; legacy electrical interfaces
remain available; and EL-40 decides how much hardware and which physical domain should be active.

53. FINAL ONE-LINE DEFINITION

PBUA Dual-Domain Fabric is a proposed post-binary transport architecture in which EL-40 organizes information through a 26-symbol A–Z logical
photonic layer, transports high-volume data through parallel WDM with adaptive PAM, uses QAM/MCS-based wireless links for mobility and fallback,
and translates every generation through a Universal PBUA Adapter while optimizing end-to-end latency, energy, reliability, synchronization, and compatibility.

54. STATUS — BUILD-ME PHASE

Concept status: active architectural concept.

Target window: 2026–2030 for progressive prototypes and validation.

Current technology foundation: silicon photonics, silicon nitride photonics, WDM, micro-comb research, PAM signaling, FEC, high-speed chiplet 
interconnects, hardware timing, DMA, wireless adaptive modulation, modern display interfaces, and optical networking.

Proposed integration: the complete PBUA A–Z logical layer, 26-channel mapping, EL-40 adaptive domain control, PUGC/Universal Adapter, PMSE,
cross-domain media scheduling, and the lower-latency/lower-energy optimization architecture.

Performance status: unproven until hardware benchmarking.

Material status: lower-hazard-material direction compared with the earlier exotic implementation, not a claim of zero toxicity.

8G status: architectural/visionary designation, not an official telecom generation.

26-color status: visual representation of 26 wavelength-defined logical channels, not a claim of 26 natural visible colors.

Core development objective: build a measurable photonic transport system that can demonstrate whether parallel higher-radix optical transport
plus EL-40 adaptive control actually reduces end-to-end latency and energy for defined workloads.

55. CURRENT STANDARD REFERENCES USED FOR THE REBUILD

The standards alignment in this revision was updated against current official specification information available in 2026.

HDMI 2.2 is the latest HDMI specification and supports up to 96 Gb/s with next-generation Fixed Rate Link.

PCI Express 7.0 is the current approved PCIe Base Specification revision and defines 128 GT/s raw signaling.

UCIe 3.0 is the current UCIe specification and defines 48 and 64 GT/s data rates plus enhanced manageability and power-saving functions.

These standards are references for interoperability and design context. They do not establish PBUA itself as a standard.

FINAL PROJECT STATEMENT

PBUA remains a concept in the build-me phase. The updated system keeps the original A–Z post-binary vision but rebuilds it around a realistic 
distinction between logical radix and physical wavelength, modern silicon/silicon-nitride photonics, PAM-4/PAM-8, adaptive FEC, EL-40 scheduling,
protected audio/video timing, Universal PBUA compatibility, and the new PBUA Dual-Domain Fabric rule: optical is the preferred high-capacity 
standard path, wireless is the optional mobility/continuity path, and EL-40 activates only the resources required to meet the deadline.
THE UPDATED POST-BINARY A–Z PHOTONIC SYSTEM

High-Radix PAM / PBUA Dual-Domain Edition

2026–2030 Build-Me-Phase Concept

STATUS: CONCEPTUAL / IN BUILD-ME PHASE. This document defines a proposed photonic architecture. The component technologies exist,
but the complete 26-channel A–Z implementation, EL-40 integration, universal adapter, and system-level performance claims require 
prototype construction and measurement.

1. THE UPDATED VISION

Imagine a computer transport system that does not depend on moving every high-bandwidth workload through one heavily serialized binary path.
Instead, information is organized into a higher-radix A–Z logical alphabet and carried through multiple wavelength-defined optical lanes. 
Each lane can use PAM-4 or PAM-8 amplitude states. The result is a proposed parallel photonic transport fabric intended to reduce serialization, 
unnecessary processing, and energy per delivered workload.

The important correction is that the 26 “colors” are not 26 natural visible colors. They are 26 logical identities assigned to 
stabilized optical wavelength channels. Diagrams can display those identities as colors for readability.

The system remains binary-compatible internally. CPUs, GPUs, memories, sensors and conventional interfaces can remain binary.
PBUA is post-binary primarily at the transport and symbol-organization layer.

2. WHY THE SYSTEM IS BEING REBUILT

The earlier concept is rebuilt around technologies that are closer to practical semiconductor and photonic manufacturing:

silicon photonics

silicon-nitride photonics

micro-comb wavelength generation

minimal heterogeneous optical gain/source material where needed

integrated modulators

photodetectors

PAM-4/PAM-8

WDM

FEC

thermal feedback

hardware timestamps

DMA

adaptive power management

EL-40 domain control

The goal is not to claim that a finished PBUA chip already exists. The goal is to define a credible build path from existing
technologies toward the proposed architecture.

3. MATERIAL AND TOXICITY DIRECTION

The updated platform favors silicon/silicon-nitride photonics with minimized specialized optical-source material. This can 
reduce reliance on large volumes of high-hazard or scarce materials compared with earlier exotic implementations.

It does not mean the chip is non-toxic. Semiconductor manufacturing still uses hazardous processing chemicals and requires
controlled fabrication and waste handling.

The correct claim is:

a lower-hazard-material design direction, not zero-toxicity manufacturing.

4. A–Z HIGH-RADIX LAYER

The logical alphabet contains 26 symbols:

A, B, C, ... Z

A 26-symbol alphabet represents approximately 4.70 bits of information per ideal symbol before overhead.

PBUA separates:

RADIX = logical organization

WDM = wavelength parallelism

PAM = amplitude states on each wavelength

This prevents the architecture from requiring one laser to distinguish 26 extremely close amplitude states.

5. 26 WDM CHANNELS

The target optical implementation contains 26 stabilized wavelength-defined channels.

A conceptual mapping is:

A → λ1
B → λ2
C → λ3
...
Z → λ26

The exact wavelength grid, channel spacing, guard bands, source technology, detector architecture and packaging must be
selected through engineering validation.

The physical wavelengths may be in telecom infrared regions rather than the visible spectrum.

6. MICRO-COMB SOURCE ARCHITECTURE

A silicon-nitride or silicon-photonics micro-comb can serve as a conceptual wavelength-generation mechanism. One pump
source can generate a comb of optical lines, from which a controlled subset can be used for the PBUA wavelength grid.

The system then adds the required:

filtering

stabilization

modulation

monitoring

detection

thermal control

The 26-channel target remains a PBUA design requirement, not a statement that every current micro-comb automatically
provides the exact production-ready PBUA channel grid.

7. PAM-4 / PAM-8 PER CHANNEL

Each wavelength channel can use:

PAM-4 — robust operating mode.

PAM-8 — higher-capacity operating mode.

EL-40 can select between them based on:

signal quality

thermal state

FEC burden

power budget

deadline

wavelength stability

The adaptive sequence can be:

PAM-8 → PAM-4 → lower symbol rate → fewer active wavelengths → alternate domain.

8. WHY THIS CAN REDUCE SERIALIZATION

The architecture does not rely on one stream carrying the entire workload sequentially. Multiple wavelength lanes can
transport independently recoverable groups at the same time.

For a high-resolution video frame, groups can be distributed across lanes. The exact mapping is dynamic rather than
permanently assigning a letter to one region of a picture.

The goal is:

more parallel transport and less waiting behind a single serial path.

This does not guarantee 26× lower latency. The complete system must be measured.

9. WHY THIS CAN REDUCE ENERGY

The target is not simply high optical power. EL-40 activates only the resources required by the workload.

Heavy video may use more wavelengths.

Normal video may use fewer.

Audio-only operation can use a protected low-bandwidth configuration.

Unused optical lanes, radio links, DSP blocks and other resources can enter low-power states.

The relevant metric is:

energy per successfully presented frame/sample interval.

10. THE NEW EL-40 ROLE

EL-40 is the adaptive control layer above the optical PHY.

It observes:

channel quality

wavelength drift

PAM mode

symbol rate

FEC corrections

temperature

power

frame deadline

audio deadline

synchronization

available optical lanes

wireless availability

It chooses the operating state rather than forcing maximum performance at all times.

The governing rule is:

use the lowest-energy configuration that can reliably satisfy the required deadline.

11. THE PBUA DUAL-DOMAIN UPGRADE

The photonic system is now part of a larger architecture called:

PBUA DUAL-DOMAIN FABRIC

Optical Standard, Wireless Optional (OS/WO)

The optical fabric is the preferred high-capacity transport when available.

Wireless is the mobility/continuity layer.

The wireless side does not recreate 26 optical wavelength channels in radio spectrum.

Instead, the same logical information is translated into native radio PHYs:

QAM

MCS adaptation

MIMO

OFDMA

carrier aggregation

multi-link operation

QoS

wireless FEC

Thus:

PAM = optical PHY

QAM/MCS = radio PHY

12. OPTICAL / FSO / RADIO HIERARCHY

The transport family becomes:

guided optical → preferred bulk path

FSO/Li-Fi → short-range optical wireless option

Wi-Fi/cellular → mobile or blocked-path continuity

The same PBUA media representation can cross these domains.

13. CAMERA-TO-PBUA PATH

The camera remains a conventional image sensor.

The complete path is:

camera sensor → image processor → PBUA media encoder → RADIX mapper → A–Z channel organization → WDM → PAM → optical transport

Optional camera-side intelligence can identify motion, regions of interest, objects, metadata and other useful information for adaptive transmission.

14. AUDIO PROTECTION

Audio receives protected scheduling because synchronization errors can be more disruptive than loss of video enhancement.

Priority order:

synchronization

audio

essential video

enhancement video

Digital audio still ultimately follows:

samples → DAC → amplifier → speaker.

PBUA transports the data; it does not replace the physical audio transducer.

15. PMSE — MEDIA SYNCHRONIZATION

The PBUA Media Synchronization Engine tracks:

source clock

capture timestamp

frame ID

audio sample ID

sequence number

arrival timestamp

reconstruction time

presentation timestamp

This lets the system measure real end-to-end presentation latency rather than assuming that optical propagation alone determines latency.

16. SIX-PART LATENCY MODEL

PBUA measures:

source processing

encoding/RADIX mapping

physical flight

decode/FEC/reconstruction

presentation

wireless contention/retransmission tail

The target is lower end-to-end and especially lower tail latency.

The architecture makes no claim that photons travel faster than light.

17. ERROR CORRECTION

A possible layered implementation is:

outer Reed-Solomon-type protection + inner soft-decision LDPC or polar-type protection.

Exact coding remains a hardware-validation task.

A post-FEC BER such as 10^-15 is an engineering target, not a demonstrated PBUA result.

18. WAVELENGTH LOCKING

The 26-channel fabric requires:

spectral monitoring

thermal feedback

guard bands

calibration

drift detection

channel health monitoring

When a channel becomes unstable:

remove → reassign → recover.

19. THERMAL CONTROL

Optical transport can reduce some electrical transport losses, but the complete module still produces heat through drivers, 
lasers, modulators, detectors, DSP, FEC and power electronics.

EL-40 therefore treats temperature as part of transport selection.

A thermal event can trigger:

lower optical power → lower PAM → lower symbol rate → fewer channels → alternate path.

20. UNIVERSAL PBUA ADAPTER

The PBUA Adapter is the bridge between generations.

It accepts, conceptually:

legacy binary

modern high-speed binary

hybrid electrical/photonic

PBUA optical

FSO

wireless continuity

EL-40 coordinated PBUA

The display does not need to understand A–Z photonic symbols. The adapter reconstructs a conventional framebuffer and audio stream.

21. PUGC

PUGC — PBUA Universal Generation Connector — is a connector architecture containing:

legacy electrical interfaces

high-speed interfaces

optical interface

wireless module interface

control sideband

power management

capability negotiation

It can be implemented as a PCB, chiplet, docking station, external adapter or integrated display controller.

22. MODERN STANDARDS COMPATIBILITY

The updated PBUA concept is designed to coexist with current standards rather than replace them immediately.

The 2026 design context includes HDMI 2.2, DisplayPort/eDP families, PCIe 7.0, UCIe 3.0, current Wi-Fi multi-link architectures 
and 5G/future 6G connectivity.

HDMI 2.2 currently defines up to 96 Gb/s with next-generation FRL and retains backward compatibility. PCIe 7.0 defines 128 GT/s raw 
signaling. UCIe 3.0 defines 48/64 GT/s chiplet data rates and enhanced management/power capabilities.

PBUA-specific functionality remains an overlay architecture and must be validated independently.

23. PERFORMANCE TARGETS — CAREFUL WORDING

The system is intended to target:

lower end-to-end latency

lower energy per presented frame

high aggregate bandwidth

lower serialization overhead

fewer unnecessary memory copies

stable audio/video synchronization

graceful optical-to-wireless fallback

These are engineering targets, not demonstrated results.

The earlier speculative “sub-10 ns” figure should therefore be treated as a possible local/interconnect design target for selected paths,
not a claim about total camera-to-display latency across the complete system. Total latency must include encoding, FEC, memory, scheduling and presentation.

Likewise, terabit-class throughput remains a design objective that depends on actual baud rate, channel count, coding overhead, packaging, 
optical loss, crosstalk and receiver capability.

24. BUILD-ME PHASE

The proposed build sequence is:

Phase 1: software A–Z/RADIX model.

Phase 2: single-channel PAM/FEC optical demonstrator.

Phase 3: multi-wavelength optical demonstrator.

Phase 4: 26-channel wavelength-grid prototype.

Phase 5: EL-40 closed-loop controller.

Phase 6: Universal PBUA Adapter/PUGC prototype.

Phase 7: FSO and wireless continuity.

Phase 8: camera/audio/display end-to-end demonstration.

Phase 9: comparative energy/latency benchmarking.

25. WHAT MUST BE PROVEN

The prototype must establish:

number of stable wavelengths

aggregate throughput

PAM-4/PAM-8 performance

optical power

BER

FEC burden

thermal drift

crosstalk

energy/bit

energy/frame

end-to-end latency

99th-percentile latency

audio/video synchronization error

domain-switch time

recovery after optical blockage

26. FINAL POST-BINARY DEFINITION

The updated Post-Binary A–Z Photonic System is a proposed higher-radix transport architecture in which 26 logical A–Z identities 
are mapped onto stabilized optical wavelength channels, each using adaptive PAM-4/PAM-8 signaling, while EL-40 dynamically manages wavelength
allocation, FEC, timing, thermal state, power and physical-domain selection. The optical system is the preferred high-capacity fabric;
FSO and QAM/MCS-based wireless are optional continuity domains; and the Universal PBUA Adapter preserves compatibility with conventional
binary computers and modern display/system interfaces.

27. FINAL STATUS

Concept: active.

Development state: build-me phase.

Target period: 2026–2030 for progressive prototypes.

Official standard status: PBUA itself is not an established industry standard.

8G status: architectural designation only.

26-color status: 26 logical wavelength identities, visually represented as colors; not 26 natural visible colors.

Core objective: experimentally determine whether the integrated PBUA architecture can achieve lower end-to-end latency and lower energy
per successfully delivered workload than appropriate contemporary baselines.

FINAL STATEMENT

The PBUA concept is now rebuilt around one coherent rule: parallel photonics is the preferred high-capacity transport fabric,
wireless is the optional mobility/continuity layer, and EL-40 continuously chooses the least complex and least energy-intensive 
configuration that can still meet the required media deadline.
