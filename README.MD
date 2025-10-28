# IC-Characterization
This repository provides practical experience in Analog IC characterization using open-source tools like **NGSpice**, **Xschem**, and the **SKY130 PDK**. It includes examples, simulations, and steps for designing and analyzing analog circuits.

## What is Analog IC Characterization ?
Analog IC characterization means testing and analyzing analog circuits to see how they perform under different real-world conditions. The process measures important parameters like gain, bandwidth, offset, and noise, making sure the circuit works correctly before and after fabrication. Characterization is usually done using simulation tools (such as Ngspice or Xschem) and focuses on three main “corners”:

- **Process Corners:** Variations that happen during manufacturing (e.g., TT, FF, SS).
- **Voltage Corners:** Operating circuits at minimum and maximum supply voltages.
- **Temperature Corners:** Testing performance across a range of temperatures (e.g., -40°C to 125°C).

These checks help ensure your analog IC design works reliably in any situation.


## Contents

- [1. Linear Elements](#1-linear-elements)
  - [1.1 Resistors](#11-resistors)
  - [1.2 Capacitors](#12-capacitors)
  - [1.3 RC Circuits](#13-rc-circuits)     
- [2. MOSFET Circuits](#2-mosfet-circuits)
  - [2.1 NMOS Analysis](#21-nmos-analysis)
  - [2.2 PMOS Analysis](#22-pmos-analysis)
- [3. Single Stage Amplifiers](#3-single-stage-amplifiers)
  - [3.1 Common Source Amplifier using NMOS](#31-common-source-amplifier-using-NMOS)
    - [3.1.1 Common Source Amplifier using Resistve load](#311-common-source-amplifier-using-resistive-load)
  - [3.2 Common Drain Amplifier using NMOS](#33-common-drain-amplifier-using-NMOS)
  - [3.3 Common Gate Amplifier using NMOS](#35-common-gate-amplifier-using-NMOS)
 

# 1. Linear Elements

## 1.1 Resistors

# 3. Single Stage Amplifiers

## 3.1 Common Source Amplifier using NMOS

### 3.1.1 Common Source Amplifier using Resistive load

<img src="simulation%20results/ngspice/1.png" width="600" />

**DC Simulation Output**  
<img src="simulation%20results/ngspice/2.png" width="600" height="400" />

The DC analysis for the common source amplifier

- When $$V_{GS} < V_T $$, the MOSFET is in the **cutoff region**; it acts like an open switch, so no current flows and the output voltage ($$V_{out} $$) remains at the supply voltage ($$V_{DD} $$).
- As $$V_{GS} $$ increases past $$ V_T $$, the MOSFET turns on and enters the **saturation region**. Now current starts to flow, the output voltage starts dropping across the drain resistor, and the MOSFET behaves like an active device with stable amplification.
- Whenever $$V_{DS} > V_{GS} - V_T $$, the transistor stays in saturation: drain current mainly depends on gate voltage.
- Eventually, if $$ V_{GS} $$ continues to increase and $$V_{DS} < V_{GS} - V_T $$, the MOSFET enters the **linear (triode) region**; it acts like a voltage-controlled resistor and $$ V_{out} $$ drops further.
- These regions are visible in the DC sweep plot: first as a flat line at high $$V_{out} $$ (cutoff), then a sharp drop (saturation), then a gentle downward slope (linear).

**Transient Simulation Output**  
<img src="simulation%20results/ngspice/3.png" width="600" height="400" />

**AC Simulation Output**  
<img src="simulation%20results/ngspice/4.jpg" width="600" />

The AC analysis for the common source amplifier reveals the following key points:

- The midband gain of the amplifier is approximately 13 dB.
- At the -3 dB bandwidth (the -3 dB frequency, or S<sub>p</sub>), the gain drops to 10 dB, indicating the cutoff point for the amplifier’s frequency response. Beyond this frequency, the gain slope decreases at a rate of 20 dB per decade.
- In the phase plot, the phase shift at the -3 dB point (S<sub>p</sub> = 2 MHz) drops to -46.36°, which is characteristic of a single-pole amplifier.
- If the frequency is increased tenfold above the SP (i.e., at 20 MHz), the phase decreases by approximately 81.91° from its midband value.
- Conversely, at one-tenth the SP frequency (0.2 MHz), the phase shift is much smaller, about 5.97°.

These results confirm the expected single-pole frequency response of the common source amplifier, with a steady gain and phase behavior characteristic of this topology.
