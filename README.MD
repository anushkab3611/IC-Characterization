# IC-Characterization
This GitHub repository is created to provide hands-on experience in Analog IC Characterization using open-source tools such as **NGSpice**, **Xschem**, and the **SKY130 PDK**.
## What is Analog IC Characterization ?
Analog IC characterization means testing and analyzing analog circuits to see how they perform under different real-world conditions. The process measures important parameters like gain, bandwidth, offset, and noise, making sure the circuit works correctly before and after fabrication. Characterization is usually done using simulation tools (such as Ngspice or Xschem) and focuses on three main “corners”:

- **Process Corners:** Variations that happen during manufacturing (e.g., TT, FF, SS).
- **Voltage Corners:** Operating circuits at minimum and maximum supply voltages.
- **Temperature Corners:** Testing performance across a range of temperatures (e.g., -40°C to 125°C).

These checks help ensure your analog IC design works reliably in any situation.


## Contents

- [1. Linear Elements](#3-linear-elements)
  - [1.1 Resistors](#31-resistors)
  - [1.2 Capacitors](#32-capacitors)
  - [1.3 RC Circuits](#33-rc-circuits)
     - [1.3.1 Transient Analysis](#331-transient-analysis)
     - [1.3.2 AC Analysis](#332-ac-analysis)
  - [1.4 CR Circuits](#34-cr-circuits)
     - [1.4.1 Transient Analysis](#341-transient-analysis)
     - [1.4.2 AC Analysis](#342-ac-analysis)
- [2. MOSFET Circuits](#4-mosfet-circuits)
  - [2.1 NMOS Analysis](#41-nmos-analysis)
  - [2.2 PMOS Analysis](#42-pmos-analysis)
