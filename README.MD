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
     - [1.3.1 Transient Analysis](#131-transient-analysis)
     - [1.3.2 AC Analysis](#132-ac-analysis)
  - [1.4 CR Circuits](#14-cr-circuits)
     - [1.4.1 Transient Analysis](#141-transient-analysis)
     - [1.4.2 AC Analysis](#142-ac-analysis)
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

- A **resistor** is a passive electrical component that resists the flow of electric current, producing a voltage drop across its terminals according to **Ohm's Law**:   `` V = I * R ``
- The resistance R of a material depends on its physical properties and geometry, given by the formula: `` R = ρL / A ``
- In the **Skywater SKY130 PDK**, multiple resistor types are available for analog and digital IC design, offering different resistance values, temperature characteristics, and area trade-offs.

# 3. Single Stage Amplifiers

## 3.1 Common Source Amplifier using NMOS

### 3.1.1 Common Source Amplifier using Resistive load

<img src="simulation%20results/ngspice/1.png" width="600" />

**DC Simulation Output**  
<img src="simulation%20results/ngspice/2.png" width="600" height="400" />

**Transient Simulation Output**  
<img src="simulation%20results/ngspice/3.png" width="600" height="400" />

**AC Simulation Output**  
<img src="simulation%20results/ngspice/4.jpg" width="600" />
The AC analysis for the common source amplifier reveals the following key points:

- The midband gain of the amplifier is approximately 13 dB.
- At the -3 dB bandwidth (the -3 dB frequency, or S_p), the gain drops to 10 dB, indicating the cutoff point for the amplifier’s frequency response. Beyond this frequency, the gain slope decreases at a rate of 20 dB per decade.
- In the phase plot, the phase shift at the -3 dB point (S_p = 2 MHz) drops to -45°, which is characteristic of a single-pole amplifier.
- If the frequency is increased tenfold above the SP (i.e., at 20 MHz), the phase decreases by approximately 81.91° from its midband value.
- Conversely, at one-tenth the SP frequency (0.2 MHz), the phase shift is much smaller, about 5.97°.

These results confirm the expected single-pole frequency response of the common source amplifier, with a steady gain and phase behavior characteristic of this topology.
