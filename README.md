# CMOS-Circuit-Design-Spice-Simulation-using-Sky130nm-technology
This repository contains a comprehensive series of SPICE simulation labs and tutorials for CMOS circuit design using the open-source Sky130nm PDK (Process Design Kit). The content is structured across five days of progressively complex topics, from basic NMOS characteristics to complete CMOS inverter robustness analysis.
##  Table of Contents

### **NgspiceSky130-Day1: Basics of NMOS Drain Current (Id) vs Drain-to-source Voltage (Vds)**

#### Introduction to Circuit Design and Spice Simulations
- [ ] L1: Why do we need SPICE simulations?
- [ ] L2: Introduction to basic element in circuit design - NMOS
- [ ] L3: Strong inversion and threshold voltage
- [ ] L4: Threshold voltage with positive substrate potential

#### NMOS Resistive Region and Saturation Region of Operation
- [ ] L1: Resistive region of operation with small drain-source voltage
- [ ] L2: Drift current theory
- [ ] L3: Drain current model for Linear region of operation
- [ ] L4: SPICE conclusion to resistive operation
- [ ] L5: Pinch-off region condition
- [ ] L6: Drain current model for saturation region of operation

#### Introduction to SPICE
- [ ] L1: Basic SPICE setup
- [ ] L2: Circuit description in SPICE syntax
- [ ] L3: Define Technology parameters
- [ ] L4: First SPICE simulation
- [ ] L5: SPICE lab with Sky130 models

---

### **NgspiceSky130-Day2: Velocity Saturation and Basics of CMOS Inverter VTC**

#### SPICE Simulation for Lower Nodes and Velocity Saturation Effect
- [ ] L1: SPICE simulation for lower nodes
- [ ] L2: Drain current vs gate voltage for long and short channel device
- [ ] L3: Velocity saturation at lower and higher electric fields
- [ ] L4: Velocity saturation drain current model
- [ ] L5: Labs Sky130 Id-Vgs
- [ ] L6: Labs Sky130 Vt

#### CMOS Voltage Transfer Characteristics (VTC)
- [ ] L1: MOSFET as a switch
- [ ] L2: Introduction to standard MOS voltage current parameters
- [ ] L3: PMOS/NMOS drain current vs drain voltage
- [ ] L4: Step 1 - Convert PMOS gate-source-voltage to Vin
- [ ] L5: Step 2 & 3 - Convert PMOS and NMOS drain-source-voltage to Vout
- [ ] L6: Step 4 - Merge PMOS-NMOS load curves and plot VTC

---

### **NgspiceSky130-Day3: CMOS Switching Threshold and Dynamic Simulations**

#### Voltage Transfer Characteristics - SPICE Simulations
- [ ] L1: SPICE deck creation for CMOS inverter
- [ ] L2: SPICE simulation for CMOS inverter
- [ ] L3: Labs Sky130 SPICE simulation for CMOS

#### Static Behaviour Evaluation - CMOS Inverter Robustness (Switching Threshold)
- [ ] L1: Switching Threshold (Vm)
- [ ] L2: Analytical expression of Vm as a function of (W/L)n and (W/L)p
- [ ] L3: Analytical expression of (W/L)n and (W/L)p as a function of Vm
- [ ] L4: Static and Dynamic simulation of CMOS inverter
- [ ] L5: Static and Dynamic simulation of CMOS inverter with increased PMOS width
- [ ] L6: Applications of CMOS inverter in clock network and STA

---

### **NgspiceSky130-Day4: CMOS Noise Margin Robustness Evaluation**

#### Static Behaviour Evaluation - CMOS Inverter Robustness (Noise Margin)
- [ ] L1: Introduction to Noise Margin
- [ ] L2: Noise Margin voltage parameters
- [ ] L3: Noise margin equation and summary
- [ ] L4: Noise margin variation with respect to PMOS width
- [ ] L5: Sky130 Noise margin labs

---

### **NgspiceSky130-Day5: CMOS Power Supply and Device Variation Robustness Evaluation**

#### Static Behaviour Evaluation - CMOS Inverter Robustness (Power Supply Variation)
- [ ] L1: Smart SPICE simulations for power supply variations
- [ ] L2: Advantages and disadvantages using low supply voltage
- [ ] L3: Sky130 Supply variation Labs

#### Static Behaviour Evaluation - CMOS Inverter Robustness (Device Variation)
- [ ] L1: Sources of variation - Etching process
- [ ] L2: Sources of variation - Oxide thickness
- [ ] L3: Smart SPICE simulation for device variations
- [ ] L4: Conclusion
- [ ] L5: Sky130 device variations labs
