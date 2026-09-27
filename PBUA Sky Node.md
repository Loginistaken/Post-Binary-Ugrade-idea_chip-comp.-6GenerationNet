Conceptual engineering architecture

PBUA Sky Node

A part-by-part explanation of a network satellite built around a common PBUA language: 
ordinary bits can travel electronically, as infrared ON/OFF pulses, or as multiple wavelength 
“colors” when an optical trunk is strong. The satellite widens the path behind ordinary towers 
instead of asking phones to become optical terminals.

The letters are protocol roles, not necessarily 26 wavelengths "COLORS". A role may be assigned a wavelength when 
the optical profile supports it; otherwise several roles can share the single blink bearer or move over RF.
(Not visible wavelength colors but IR wavelengths assigned colors, colors assigned letters A-Z) 

“When an optical trunk is strong” means that the infrared optical communication path has enough signal quality to reliably carry the higher-capacity WDM connection. “Strong” does not simply mean the laser is brighter; it means the received optical power, signal-to-noise ratio, pointing accuracy, link margin, atmospheric conditions, wavelength separation, and detector performance are all good enough for reliable communication. In good conditions, several wavelengths can operate simultaneously—for example, D data at 1560 nm, G gateway traffic at 1570 nm, and E health data at 1530 nm. If the optical path weakens because of distance, pointing problems, clouds, fog, atmospheric scattering, or other losses on a satellite-to-ground path, PBUA can step down from multi-wavelength WDM to a single 1550 nm IR ON/OFF channel, where 1 = IR ON and 0 = IR OFF; if usable optical communication is no longer possible, it can fall back to RF while preserving the same logical data and payload.

PBUA 3.0 foundation IR ON/OFF + ASCII teaching mode WDM optical trunk RF fall-back-gate-way + satellite relay concept, not a telecom standard

Design rule: the large audience remains on familiar wireless and local networks. The sky node is a 
trunk and relay behind those networks. This keeps the concept expandable without claiming that one spacecraft becomes a nationwide cell tower.

1 · Mission2 · Generations3 · Bits4 · PBUA5 · Colors6 · Hardware7 · Modes8 · Fallback9 · Network10 · Build11 · Limits12 · Summary   

01 · Mission
The satellite is a network node in the sky
The core idea is simple: a phone or PC does not need to point an optical terminal upward. 
It continues to use the access network available to it. A ground gateway gathers that traffic,
the sky node carries it across a long trunk, and another gateway gives it back to ordinary terrestrial networks.

“Tower in the sky” and "Node in the Sky" . Means the satellite acts as a network relay/trunk node in space that can connect multiple ground networks together. A trunk is the high-capacity long-distance part of a communications network that carries aggregated traffic between smaller networks; in this PBUA Sky Node idea, the satellite trunk is the long-distance communications path carried through the spacecraft, using inter-satellite optical links, satellite-to-ground optical links, or RF when optical is unavailable. The network expands to more people because the satellite does not have to communicate directly with every phone: phones continue using ordinary 4G/5G-class towers or local networks, those networks connect to ground gateways, the gateways send their combined traffic through the Sky Node trunk, and another gateway delivers it to distant towers or networks. Adding more gateways allows more communities, rural areas, ships, remote sites, and other networks to connect; adding more satellites creates a constellation, extending the trunk across larger geographic areas and allowing traffic to move from satellite to satellite. So the basic expansion is more ground gateways → more connected local networks → more people, while more satellites → longer and more continuous sky-trunk coverage.

Phone / PC
ordinary access

→

Tower / local network
last hop stays radio or wire

→

Ground gateway
PBUA adapter

→

PBUA Sky Node
optical or RF trunk

→
Far gateway / node
unpack + handoff
→
Far towers / networks
people receive normal bytes

The phrase “tower in the sky” is therefore a shorthand for trunk in the sky: one node can help multiple ground networks, 
and a constellation can extend the coverage and continuity of that trunk.

RECOMMENDATION ADD ON: define the satellite as a store-and-forward / relay-capable node from the start. That gives the
concept a useful role even before continuous constellation coverage exists.

02 · Forward and backward evolution

How 4th-, 5th-, and 6th-generation ideas connect
“4G,” “5G,” and “6G” should not be treated as three kinds of electricity. They are generations of communications systems. 
At the information level, all of them can carry bits. The physical carrier changes: electronic processing, radio-frequency
modulation, antennas, optical links, and photonic components can all participate.

Layer

Conceptual role in this canvas

What is preserved

4G-class access

Radio last hop and established packet networking

ordinary bytes and IP-style networking

5G-class access

Higher-capacity radio access and modern network cores

ordinary devices remain ordinary radio users

Photonic trunk

Free-space IR or fiber-connected optical gateway

the same payload bytes

PBUA 3.0 blink stair

One IR carrier; ON = 1, OFF = 0

binary and ASCII-compatible teaching/control traffic

WDM stair

Several wavelengths in one optical path

frames, roles, data, and control remain identifiable

Forward compatibility means the packet can move upward into a richer physical layer when the hardware and link permit it.
Backward compatibility means the same payload can move downward to a simpler optical or RF bearer without changing the application’s underlying data.

Engineering distinction: the proposed photonic fabric is a conceptual architecture, not a definition of the official 6G standard. 
6G specifications, spectrum allocations, modulation schemes, and certification requirements are determined by standards bodies and industry programs.

03 · The common language

Binary is the bridge between computers and photons

Computers ultimately process information as states represented by bits. An ASCII character is normally 8 bits. For example, 
the ASCII byte for H is 01001000. The physical link does not need to know that those eight bits spell H; it only needs to preserve the bit sequence.

HELLO as a teaching example

01001000

The visualizer shows the first byte, H = 01001000. A pulse train can represent these states: light during a slot = 1; no light during a slot = 0.

More bits per character: a conceptual symbol alphabet can reduce how many symbols are needed to represent a message,
but it does not automatically make ASCII characters contain more information. Base-26 has
log₂(26) ≈ 4.70 bits of ideal symbol capacity, while an 8-bit ASCII byte carries up to 8 bits. 
A practical PBUA system could use larger symbols, wavelength channels, or higher-order modulation 
to increase throughput, but real efficiency also depends on framing, error correction, synchronization, coding, and signal quality.

RECOMMENDATION ADD ON: keep the binary layer explicit. It makes the architecture testable: an FPGA, 
photodetector, or radio modem can be judged by whether the same bytes emerge after a mode change.

04 · PBUA 3.0 foundation

One payload, several physical forms

The design separates what the data is from how the link carries it. A PBUA frame can identify a role
such as data, control, health, gateway traffic, or inter-node traffic. The bearer can then be optical WDM, one-color ON/OFF, or RF.

Data identity D identifies user data in this concept. The payload is still ordinary bytes.

Physical bearer The same D payload may ride an assigned IR wavelength, a 1550 nm blink, or an RF link.

Adapter boundary The ground adapter translates between PBUA framing and the network equipment already used by a tower or gateway.

This separation is the central compatibility mechanism: the color is rented by the link; the data identity remains in the frame.

05 · Wavelength as “color”

Letters name traffic roles; wavelengths are physical optical channels

Infrared is invisible, but engineers can use the word “color” as a mental model for different wavelengths.
A receiver with suitable filters or wavelength-selective components can separate those channels. 
The letter is not literally the wavelength; it is a label that the protocol uses to associate a traffic role with a chosen optical channel.

Letter

Conceptual role

Example optical appointment

A

acquisition / beacon / handshake

850 nm beacon

B

default home / blink carrier

1550 nm

C

control and signaling

1540 nm

D

user data

1560 nm

E

node health / telemetry

1530 nm

G

gateway backhaul

1570 nm

I

inter-satellite trunk

1590 nm

U

helper toward a radio user cell

RF bearer in this concept

Z

safe RF-only posture

laser/optical data path off

These wavelengths are conceptual appointments for the architecture, not a claim that a flight system 
should use these exact channels. Real optical terminals must satisfy atmospheric transmission, detector 
response, eye-safety where applicable, laser-source availability, pointing, spectral spacing, filtering, thermal limits, and regulatory requirements.

RECOMMENDATION ADD ON: treat the wavelength table as a negotiable profile. A future implementation can 
publish several profiles rather than hard-coding one set of wavelengths into every spacecraft.

06 · Build the spacecraft

Part by part: what makes the node work

1. Power subsystem Solar arrays and battery supply the computer, RF electronics, optical terminal, pointing hardware, thermal control, and housekeeping.

2. Flight computer Runs PBUA framing, routing, scheduling, mode selection, health monitoring, encryption interfaces, and link negotiation.

3. RF transceiver Provides the robust floor for telemetry, command, gateway service, and fallback when optical service is unavailable.

4. Optical terminal Produces and receives an aimed IR beam for ground gateways or other satellites.

5. Wavelength selector A conceptual combination of sources, filters, multiplexers/demultiplexers,
6. and detectors that separates the appointed optical channels.

7. Pointing system Keeps the optical terminal and service antennas aligned with their partners.
8. Fine pointing is a major engineering challenge for free-space optical links.

9. PBUA adapter Wraps ordinary bytes in the project’s frame structure and removes the wrapper at the far end.

10. Timing + synchronization Provides clocks, slot boundaries, beacon acquisition, and recovery from drift or interruptions.

11. Error protection Adds practical forward-error correction, integrity checks, retransmission or
12.  erasure handling so a few bad photons do not corrupt an entire file.

13. Security layer Encryption and authentication protect traffic regardless of whether the bearer is optical or RF.

14. Thermal system Removes heat from processors, laser sources, RF power amplifiers, detectors, and power electronics.

15. Routing table Decides whether a packet goes to a ground gateway, another satellite, a radio gateway, or a safe fallback path.

The spacecraft is therefore not one magic transmitter. It is a coordinated stack: power → compute → framing → link selection →
pointing → physical transmission → error recovery → routing → handoff.

07 · Three operating modes

The staircase: WDM → IR ON/OFF → RF

Strong opticalWeak opticalNo usable optical

Mode 1 — strong optical / WDM

Several wavelengths share one aimed beam. Traffic roles can be separated into parallel optical channels. 
This is the highest-capacity conceptual stair and the place where the “color” metaphor becomes physically useful.

Example: D data at 1560 nm while G gateway traffic is 1570 nm and E health is 1530 nm.

08 · Forward / backward compatibility

How the signal changes without changing the file

Imagine a file entering at a gateway. Its bytes are unchanged as the network chooses different physical bearers. 
Only the wrapping and transmission method change.

Bytes
application data

→

PBUA frame
role + payload + checks

→
WDM
many colors

→

ON/OFF
one color, 1/0

→

RF
radio floor
→

Bytes again
same payload

Forward: when a compatible optical terminal and good link margin appear, the system can add wavelength channels.
Backward: when margin falls, the same logical traffic collapses to one optical carrier or RF. The receiving adapter reconstructs the original bytes.

RECOMMENDATION ADD ON: make every mode advertise its capability and measured link margin.
A node should never assume that “optical available” means “WDM safe.” It should negotiate the highest mode that the measured link can actually sustain.

09 · Network behavior

How a constellation becomes a larger audience

A useful audience comes from many endpoints and many gateways, not from pretending one spacecraft directly serves every handset.

Ground gateway Connects PBUA optical or RF service to terrestrial fiber, towers, data centers, ships, or remote networks.

Sky-to-ground Moves traffic between a gateway and the spacecraft. Optical can be selected in clear conditions; RF is the fallback.

Inter-satellite Uses letter I to identify a node-to-node trunk. In vacuum, atmospheric cloud is not the limiting factor on the same path.

Far gateway Unwraps the PBUA frame and passes ordinary traffic to a distant network.

Radio user A handset remains a radio endpoint. It does not need a PBUA IR terminal.

Rural / maritime / emergency site A gateway can extend a disconnected or isolated network toward a larger backbone.

For continuous service, a constellation needs handoffs, routing, orbital planning, gateway diversity, timing, authentication, 
spectrum coordination, and enough spacecraft to maintain useful geometry. A single node can demonstrate the architecture; a network requires multiple nodes.

10 · Build path

How the concept could be developed in stages

Stage

Demonstration

Purpose

1

Software PBUA framing

Prove that bytes can be wrapped, checked, routed, and reconstructed independent of bearer.

2

Electronic/RF adapter

Connect the concept to conventional networking equipment and demonstrate fallback first.

3

Single IR ON/OFF link

Demonstrate pulse/no-pulse binary transport and recovery of known test payloads.

4

Wavelength-separated optical testbed

Demonstrate multiplexing, filtering, synchronization, and role-to-channel negotiation.

5

Ground gateway field test

Test pointing, atmospheric margin, error correction, and automatic mode changes.

6

Space demonstration node

Validate the flight computer, RF fallback, optical terminal, thermal behavior, and operations.

7

Two-node optical trunk

Demonstrate inter-satellite routing and a longer network path.

8

Small constellation

Test continuous coverage, handoff, routing, gateway diversity, and real audience expansion.

RECOMMENDATION ADD ON: make the first demonstrations terrestrial. A lab can verify the protocol, blink stair, WDM separation,
and fallback logic before the cost and complexity of space qualification.



11 · What the concept can and cannot claim

Engineering boundaries that keep the idea credible

Can claim

A common logical frame can be designed to survive changes in physical bearer.

Can claim

Infrared ON/OFF can represent binary information when a suitable source, detector, timing system, and link budget exist.

Can claim

WDM can create multiple optical channels in a suitable optical system.

Cannot claim yet

That the proposed alphabet or wavelength map is an adopted 6G standard.

Cannot claim yet

That IR ON/OFF is automatically faster than electronic signaling. Throughput depends on symbol rate, bandwidth, coding, SNR, and hardware.

Cannot claim yet

That one satellite can replace the entire terrestrial access network for a large population.

The design is best described as a conceptual hybrid communications architecture. It can borrow established technologies—RF 
networking, optical communications, WDM, satellite backhaul, error correction, encryption, and gateway routing—while proposing a
particular common framing and fallback philosophy.

12 · Complete system

One continuous picture of how PBUA Sky Node works

A computer or phone creates ordinary data. A local tower or network carries that data to a gateway. The gateway adapter 
places the payload into a PBUA frame with a role letter, checks, sequencing, and the information needed to negotiate its physical bearer.
The sky node receives the frame, measures the link, identifies the partner, and chooses the highest compatible stair.

If the optical path is strong, wavelengths act like parallel colored lanes. A letter such as D can identify the user-data role while 
the optical profile assigns that role a wavelength. Control, health, gateway traffic, and inter-satellite traffic can have their own
optical appointments. This is the rich photonic layer.

If the optical path weakens, the node removes the extra colors instead of immediately abandoning the optical family. One home
wavelength remains and the signal becomes a timed binary blink: ON is 1 and OFF is 0. ASCII is an easy demonstration because 
every character can be represented by a known 8-bit pattern, but the same bit transport can carry arbitrary binary files and packets.

If the optical path disappears, the frame falls back to RF. The payload remains the same. The wavelength field can be empty or zero, 
while the logical role letters still describe the traffic. The phone remains a radio device, and the tower remains the access point for the crowd.



At the far side, the process reverses: receive the bearer, synchronize, correct errors, authenticate and decrypt as required, 
reconstruct the PBUA frame, recover the payload bytes, and hand those bytes to ordinary network equipment. A person on a phone
therefore experiences a normal network service even though the long trunk behind the tower may have used radio, one-color infrared, 
or several optical wavelengths.

Final architecture: ordinary bytes → PBUA frame → WDM optical / IR ON-OFF / RF → sky relay → reverse conversion → 
ordinary bytes. The forward path adds richer physical options. The backward path preserves service by stepping down to simpler bearers.

The concept’s central engineering question is therefore not “Can a satellite be a 6G phone tower?” It is 
“Can a satellite node carry the same network traffic across progressively richer or poorer physical links
while preserving compatibility at the edges?” That is the testable architecture this canvas describes.

Reference context: This canvas is structured around the PBUA 3.0 / infrared ON-OFF ASCII compatibility concept supplied for this project, then extended into a network-node architecture. Related photonic networking concepts commonly use hybrid photonic/electronic bridges and fallback between optical and electronic transport; this canvas keeps those ideas as engineering context rather than treating the project as an established standard. cite marker omitted in preview source text
