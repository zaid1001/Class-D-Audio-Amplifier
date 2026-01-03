# Class-D-Audio-Amplifier
Class-D audio amplifier using basic and discrete components only, without relying on any dedicated Class-D amplifier IC.

Author: Mohd Abdul Zaid Qureshi

Degree: B.Tech – Electronics & Telecommunication (2026)

Tools Used: LTspice, EasyEDA, KiCad (optional), Git

Application: Embedded Hardware Developer – Vicharak

1. Objective

The objective of this project is to design, simulate, and lay out a Class-D audio amplifier using basic and discrete components only, without relying on any dedicated Class-D amplifier IC.

The design demonstrates:
Fundamental analog and digital electronics concepts
PWM generation and signal conditioning
MOSFET gate driving and power stage design
Output LC filtering
Practical PCB layout considerations

2. System Overview

The complete Class-D amplifier is divided into the following functional blocks:

PWM Generator (Carrier Signal)
Audio Signal Conditioning
Comparator / PWM Modulator
MOSFET Gate Driver
Full-Bridge Power Stage
LC Output Filter
Load (Speaker / Resistive Load)

3. PWM Generation (Timer IC – NE555)

A 555 timer is configured in astable mode to generate a high-frequency triangular/sawtooth waveform.
This waveform acts as the carrier for PWM modulation.
Frequency is selected such that:
Much higher than audio band
Low enough to be filtered by an LC filter
Why 555?
Simple, Well understood, Demonstrates timing analysis and RC selection

4. Audio Signal Conditioning (Op-Amp Stage)

Input audio is conditioned using an operational amplifier:
Gain adjustment
DC offset control
Signal centering for comparator operation
Why Op-Amp?
Demonstrates analog signal processing, Gain and offset selection using resistive networks, Required for proper PWM modulation depth

5. PWM Modulation (Comparator)

The conditioned audio signal is compared with the high-frequency carrier waveform.
Output is a PWM signal whose duty cycle follows the audio amplitude.
Key Points:
Comparator threshold selection
Avoiding saturation
Clean transitions for gate driver compatibility

6. MOSFET Gate Driver (LTC4446)

A dedicated MOSFET gate driver is used to:
Provide fast gate charge/discharge
Reduce switching losses
Isolate control and power stages

Why a Gate Driver?

Op-amps and comparators cannot drive MOSFET gates directly
Proper rise/fall times are critical in Class-D amplifiers

7. Power Stage (Full-Bridge MOSFETs)

Complementary MOSFET configuration:
High-side and low-side switching
Generates high-power PWM waveform at the switching node
Design Considerations:
Logic-level MOSFETs
Gate resistors for ringing control
Dead-time considerations (implicit via driver behavior)

8. LC Output Filter

To recover the analog audio signal from the PWM waveform, an LC low-pass filter is used.

Component Values Used:
Inductors: L1 = 11 µH, L2 = 11 µH
Capacitors: C = 19 µF (multiple stages)
Purpose:
Attenuate switching frequency
Pass audio frequency band
Reduce ripple and EMI

9. Simulation (LTspice)

Complete system simulated in LTspice
Observed:
PWM waveform at switching node
Filtered sine-like output waveform
Phase delay introduced by LC filter

Simulation validates:
Correct PWM modulation
Effective ripple reduction
Stable operation

10. PCB Design (EasyEDA)

Schematic captured in EasyEDA
Two-layer PCB:
Top and bottom copper
Proper separation between: Signal ground and Power ground
Short, wide traces for: MOSFET drains Supply paths Decoupling capacitors placed close to ICs
