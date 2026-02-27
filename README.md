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

# CMOS Circuit Design & SPICE Simulation using Sky130nm Technology

## L1: Why Do We Need SPICE Simulations?

Modern digital circuits are built using complementary MOS (CMOS) technology, where PMOS and NMOS transistors are interconnected to form fundamental logic gates—NAND, NOR, OR, AND, and the most basic building block, the **inverter**.

`[Insert Inverter Circuit Image]`

The inverter's performance characteristics—particularly **propagation delay**—determine how fast a circuit can operate. Through SPICE simulations, engineers extract critical parameters like delay and determine the optimal **W/L (width-to-length) ratios** for transistors, directly impacting circuit speed and power consumption.

`[Insert Delay Characteristics Image]`

### The Critical Role of SPICE in VLSI Design

SPICE (Simulation Program with Integrated Circuit Emphasis) forms the backbone of modern digital design flows. Without accurate SPICE simulations:

- **Clock Tree Synthesis (CTS)** would operate blindly, unable to account for real-world delays
- **Timing analysis** would be impossible, making timing closure a guessing game
- **Crosstalk analysis**—critical for signal integrity—would lack meaningful data

`[Insert CTS Circuit Image]`

Consider a typical clock tree with buffers driving different capacitive loads. SPICE simulations generate comprehensive **delay tables** that capture the relationship between:

- **Input slew rate** (how fast the signal transitions)
- **Output load capacitance** (what the buffer drives)

`[Insert Delay Tables Image]`

The intersection of these parameters determines the actual cell delay—information that flows directly into Static Timing Analysis (STA) tools. Every standard cell library in existence derives its timing and power characteristics from thousands of SPICE simulations.

---

## L2: Introduction to the NMOS Transistor

### Device Structure

The NMOS transistor is fabricated on a **p-type silicon substrate** with two heavily doped **n+ regions** forming the source and drain terminals. A thin **silicon dioxide (SiO₂) layer** electrically isolates the **polysilicon or metal gate** from the underlying channel region. Shallow Trench Isolation (STI) surrounds each device, preventing unwanted electrical interaction between adjacent transistors.

`[Insert NMOS Cross-Section Image]`

### Threshold Voltage Fundamentals

The **threshold voltage (Vt)** is arguably the most critical parameter in MOS transistor characterization—virtually every aspect of device behavior depends on it.

**Case 1: Zero Gate Voltage (Vgs = 0V)**

With source, drain, and body all grounded, the p-substrate and n+ regions form reverse-biased PN junctions. The result: **extremely high resistance** between source and drain, with **no conducting channel** beneath the gate. The transistor remains in its OFF state.

`[Insert Vgs=0 Image]`

**Case 2: Positive Gate Voltage (Vgs > 0V)**

Applying a positive potential to the gate attracts **negative charge carriers (electrons)** to the semiconductor surface beneath the oxide. This initial accumulation of charges marks the beginning of channel formation.

`[Insert Vgs>0 Image]`

---

## L3: Strong Inversion and Threshold Voltage

### From Depletion to Inversion

As gate voltage increases, the following sequence occurs:

1. **Accumulation**: Negative charges gather at the oxide-semiconductor interface
2. **Depletion**: Majority carriers (holes) are repelled, creating a **depletion region** devoid of mobile charge carriers

`[Insert Depletion Region Image]`

3. **Strong Inversion**: At a critical gate voltage, the surface layer **inverts** from p-type to n-type. This threshold condition—where the electron concentration at the surface equals the hole concentration in the bulk—defines the **threshold voltage (Vt)** .

`[Insert Strong Inversion Image]`

### Channel Formation

Beyond threshold, further increasing Vgs no longer attracts additional charges from the substrate (all available carriers are already depleted). Instead, electrons from the **n+ source region** are drawn into the inverted channel, creating a continuous **conductive path** between source and drain.

`[Insert Channel Formation Images]`

However, with Vds = 0V, electrons remain stationary despite the existing channel. This state is termed the **cut-off region**—a channel exists, but no current flows.

`[Insert Cut-off Region Image]`

### The Body Effect

Applying a positive potential to the source relative to the body (Vsb > 0) widens the depletion region beneath the channel.

`[Insert Body Effect Images]`

This expanded depletion region consumes some of the induced channel charges, effectively **delaying the onset of strong inversion**. Consequently, a higher gate voltage is required to form the channel—this phenomenon is known as the **body effect**, and it's characterized by the **body effect parameter (γ or Gamma)** .

---

## L4: Threshold Voltage with Positive Substrate Potential

### Understanding Body Bias

When the source-body junction is reverse-biased (Vsb > 0), two key changes occur:

1. The depletion region widens significantly
2. Mobile charges from the forming channel are partially depleted by this expanded region

`[Insert Body Bias Comparison Image]`

### Impact on Threshold Voltage

The result is straightforward but important: **surface inversion requires additional gate voltage** compared to the zero-bias condition. The threshold voltage increases according to:

**Vt = Vt0 + γ(√(2φF + Vsb) - √(2φF))**

Where:
- **Vt0** = Zero-bias threshold voltage
- **γ (Gamma)** = Body effect coefficient (provided by foundries)
- **φF** = Fermi potential
- **Vsb** = Source-to-body voltage

`[Insert Vt Equation Image]`

Foundries characterize these parameters through extensive silicon measurements and provide them in SPICE model files. This allows designers to accurately simulate circuit behavior under various bias conditions.

---

## NMOS Resistive and Saturation Regions

## L1: Resistive Region Operation with Small Drain Voltage

### Building on Cut-off Understanding

Previously, we examined the cut-off region (Vgs < Vt). Now we explore what happens when both gate and drain voltages are applied—specifically, the **resistive (or linear) region**.

### Channel Formation with Drain Bias

With Vgs > Vt, a continuous inversion layer forms beneath the gate. The channel's conductivity—and thus its ability to carry current—depends on the **net induced charge**, which is proportional to **(Vgs - Vt)** .

`[Insert Channel Width Image]`

### Voltage Gradient Along the Channel

Applying a small drain voltage (Vds << Vgs - Vt) creates a **voltage gradient** along the channel length:

- Near the **source** (x=0): Channel voltage = Vgs
- Near the **drain** (x=L): Channel voltage = Vgs - Vds

`[Insert Voltage Gradient Image]`

This gradient means the effective gate-to-channel voltage varies with position, directly influencing the local charge density and, consequently, the drain current.

### Effective Channel Length

A critical observation: the electrical **effective channel length** is significantly shorter than the physical drawn length due to lateral diffusion of source/drain regions under the gate.

`[Insert Effective Length Image]`

This reduction—modeled as **ΔL**—becomes increasingly important in modern short-channel devices and affects current drive capability.

---

## L2: Drift Current Theory

### Position-Dependent Channel Voltage

Let's analyze a concrete example:
- Vgs = 1.0V
- Vds = 0.05V (small)
- Vt = 0.45V

At the **source end** (x=0): Vgs - V(x) = 1.0V - 0V = **1.0V**
At the **drain end** (x=L): Vgs - V(x) = 1.0V - 0.05V = **0.95V**

`[Insert Channel Voltage Profile Image]`

The induced charge density varies along the channel because it's proportional to this position-dependent voltage.

### Drift vs. Diffusion

MOSFET operation in the linear region is dominated by **drift current**—carrier motion under the influence of an electric field. Diffusion current (carrier motion due to concentration gradients) becomes significant primarily in the subthreshold region.

`[Insert Drift Current Illustration Image]`

### Deriving Drain Current

To obtain the drain current equation, we examine the transistor from a **top-down perspective**:

`[Insert Top View Image]`

The current at any point x is given by:
**Id = -W · Qn(x) · v(x)**

Where:
- **W** = Channel width
- **Qn(x)** = Inversion layer charge density at position x
- **v(x)** = Carrier velocity at position x

---

## L3: Drain Current Model for Linear Region Operation

### Velocity-Field Relationship

Carrier velocity depends on mobility (μ) and the lateral electric field (dV/dx):
**v(x) = μn · dV/dx**

Combining with the charge density expression yields the fundamental differential equation for drain current.

`[Insert Derivation Steps Image]`

### Integration Across the Channel

Integrating from source (x=0, V=0) to drain (x=L, V=Vds):

**Id = μn · Cox · (W/L) · [(Vgs - Vt) · Vds - (1/2) · Vds²]**

`[Insert Final Equation Image]`

### Key Parameters

This equation reveals the technology-dependent parameters:
- **Cox** = Gate oxide capacitance per unit area
- **μn** = Electron mobility
- **W/L** = Transistor aspect ratio (designer-controlled)
- **Vt** = Threshold voltage

### Linear Region Validity Condition

The device operates in the linear (or triode) region when:
**(Vgs - Vt) ≥ Vds**

Under this condition, the drain current shows **quadratic dependence** on Vds—not purely linear despite the region's name.

`[Insert Linear Region Plot Image]`

---

## L4: SPICE Conclusions for Resistive Operation

### Design Variables and Their Impact

To fully characterize NMOS behavior, we must understand how drain current responds to both control voltages:

1. **Gate-source voltage (Vgs)** : Controls channel conductivity
2. **Drain-source voltage (Vds)** : Drives current through the channel

### The Simulation Challenge

The key question becomes: *How do we systematically determine Id across all combinations of Vgs and Vds while ensuring operation remains within the linear region?*

For each Vgs value, we must:
1. Identify the valid Vds range: 0 ≤ Vds ≤ (Vgs - Vt)
2. Sweep Vds across this range
3. Apply the linear region equation
4. Record the resulting Id-Vds characteristics

`[Insert Simulation Flow Image]`

This is precisely where **SPICE simulation becomes indispensable**—manually performing these calculations for multiple bias points would be impractical, especially when considering process variations, temperature effects, and statistical mismatches.

---

## L5: Pinch-off Region Condition

### Entering Saturation

When drain voltage exceeds (Vgs - Vt), the device enters a different operating regime—the **saturation region**.

### Channel Voltage Analysis

Recall that the local channel voltage at any point is Vgs - V(x). At the drain end (x=L), V(x) = Vds, so the effective gate-overdrive at the drain is **(Vgs - Vds)** .

`[Insert Channel Voltage Profile Image]`

### Three Key Conditions

**Case 1: Vgs - Vds > Vt**
The entire channel is inverted—continuous conducting path exists from source to drain.

**Case 2: Vgs - Vds = Vt**
At the drain terminal, the gate-overdrive exactly equals threshold voltage. The inversion layer **just begins to disappear** at the drain—this is the **pinch-off point**.

`[Insert Pinch-off Onset Image]`

**Case 3: Vgs - Vds < Vt**
The drain end of the channel has **lost its inversion layer**. The channel is "pinched off" near the drain, with carriers injected into the depletion region and swept to the drain by the strong electric field.

`[Insert Pinch-off Condition Image]`

### Saturation Region Defined

When pinch-off occurs, the MOSFET is said to be in **saturation**—further increases in Vds no longer significantly increase drain current because the voltage at the pinch-off point remains approximately constant at (Vgs - Vt).

`[Insert Saturation Region Image]`

---

## L6: Drain Current Model for Saturation Region Operation

### Constant Channel Voltage Approximation

In saturation, the voltage at the pinch-off point remains fixed at (Vgs - Vt). Substituting this into the linear region equation by replacing Vds with (Vgs - Vt) yields the **saturation current equation**:

**Id(sat) = (μn · Cox)/2 · (W/L) · (Vgs - Vt)²**

`[Insert Saturation Equation Image]`

### Ideal Current Source Behavior

According to this equation, drain current in saturation **should be independent of Vds**—the MOSFET behaves as an ideal voltage-controlled current source.

`[Insert Ideal Current Source Plot Image]`

### Channel Length Modulation (CLM)

However, real devices deviate from this ideal behavior. As Vds increases beyond Vdsat, the depletion region at the drain expands, effectively **reducing the channel length** (L → L - ΔL).

`[Insert CLM Illustration Image]`

Since current is inversely proportional to channel length (Id ∝ 1/L), this reduction causes a **slight increase** in drain current with increasing Vds—manifesting as finite output resistance in saturation.

The modified equation becomes:
**Id(sat) = (μn · Cox)/2 · (W/L) · (Vgs - Vt)² · (1 + λ · Vds)**

Where **λ (lambda)** is the channel length modulation parameter.

`[Insert Real I-V Plot Image]`

---

## Key Takeaways

| Concept | Key Insight |
|--------|-------------|
| **SPICE Role** | Enables delay characterization, timing analysis, and cell library development |
| **Threshold Voltage** | Critical parameter determining device turn-on; affected by body bias |
| **Linear Region** | (Vgs-Vt) ≥ Vds; current shows quadratic Vds dependence |
| **Saturation Region** | (Vgs-Vt) < Vds; current ideally constant, but shows CLM effects |
| **Channel Length Modulation** | Finite output resistance in saturation due to effective channel length reduction |

---

## Next Steps

Proceed to **Day 2** where we explore velocity saturation effects and CMOS inverter voltage transfer characteristics.

# Introduction to SPICE

## L1: Basic SPICE Setup

### Understanding the SPICE Simulation Flow

Before diving into simulations, it's essential to understand the complete SPICE setup and how various components interact to produce meaningful results.

`[Insert SPICE Setup Overview Image]`

### Fixed Parameters from Foundries

Certain parameters are **process-dependent constants** provided directly by the foundry. These are derived from extensive silicon characterization and do not require designer derivation. Key parameters include:

- **Oxide capacitance (Cox)**
- **Carrier mobility (μn, μp)**
- **Threshold voltage (Vt) parameters**
- **Process corner variations**

`[Insert Circled Parameters Image]`

### The Simulation Workflow

The SPICE simulation engine requires two primary inputs to generate device characteristics:

1. **SPICE Model Parameters** - The technology file containing device physics equations and constants
2. **SPICE Netlist** - The circuit description defining connectivity, component values, and analysis types

`[Insert Simulation Flow Diagram Image]`

When these inputs are processed, the output provides comprehensive **device characteristics**—typically current-voltage (I-V) relationships such as Id vs. Vds for multiple Vgs values.

### MOSFET Circuit Representation

For simulation purposes, every MOSFET is represented by an **equivalent circuit model** that captures:
- Intrinsic transistor behavior
- Parasitic capacitances
- Series resistances
- Body diode effects

`[Insert MOSFET Equivalent Circuit Image]`

---

## L2: Circuit Description in SPICE Syntax

### Step-by-Step Netlist Creation

Writing a SPICE netlist requires a systematic approach. Follow these steps to create error-free circuit descriptions:

#### Step 1: Define Nodes

Every connection point in the circuit must be assigned a unique node identifier. Nodes can be:
- **Numbers** (0, 1, 2, 3...)
- **Names** (VDD, GND, OUT, IN...)

`[Insert Node Definition Image]`

#### Step 2: Assign Meaningful Names

Use descriptive names for clarity:
- **VDD** - Power supply
- **GND** - Ground (always node 0)
- **IN** - Input signal
- **OUT** - Output node
- **D, G, S, B** - Drain, Gate, Source, Body terminals

`[Insert Named Nodes Image]`

#### Step 3: Write the Component Statements

**MOSFET Syntax:**

# Day 2: Velocity Saturation and CMOS Inverter Voltage Transfer Characteristics (VTC)

## SPICE Simulation for Lower Nodes and Velocity Saturation Effect

### L1: SPICE Simulation for Lower Technology Nodes

#### Review of Long-Channel MOSFET Behavior

In Day 1, we examined the Id vs. Vds characteristics for long-channel devices. The family of curves revealed three distinct regions of operation:

- **Cut-off region** (Vgs < Vt): No current flows
- **Linear region** (Vds < Vgs - Vt): Current increases approximately linearly with Vds
- **Saturation region** (Vds ≥ Vgs - Vt): Current ideally becomes constant

`[Insert Long-Channel Id-Vds Curve Image]`

The boundary between linear and saturation regions is defined by the condition:
**Vdsat = Vgs - Vt**

For long-channel devices, this relationship holds true across all bias conditions.

#### The Scaling Challenge

Now consider what happens when we scale the transistor dimensions. If we maintain the same **W/L ratio** but reduce both W and L proportionally, classical theory suggests the drain current should remain unchanged:

**Id ∝ (W/L)**

However, **real devices deviate significantly** from this idealized behavior as channel lengths shrink below 1μm.

`[Insert Scaling Comparison Image]`

#### Simulation Setup for Short-Channel Devices

Let's examine a SPICE deck comparing long and short-channel devices while keeping W/L constant:

Despite identical W/L ratios, the simulation results will reveal fundamental differences in behavior due to short-channel effects.

L2: Drain Current vs. Gate Voltage for Long and Short Channel Devices
Comparative Analysis
When we overlay the characteristics of long and short-channel devices, several important observations emerge:

[Insert Long vs Short Channel Comparison Image]

Observation 1: Different Vgs Dependencies

For long-channel devices, the drain current shows a quadratic dependence on gate voltage in saturation:

Id(sat) ∝ (Vgs - Vt)²

[Insert Long-Channel Id-Vgs Quadratic Plot Image]

For short-channel devices at the same Vds = 2.5V, the current increases linearly with Vgs due to velocity saturation:

Id(sat) ∝ (Vgs - Vt) (linear dependence)

[Insert Short-Channel Id-Vgs Linear Plot Image]

Understanding the Simulation Syntax
The SPICE syntax for generating Id vs. Vgs characteristics:

spice
* Id vs Vgs simulation
.dc Vgs 0 1.8 0.1 Vds 0.5 2.5 0.5
This means: "For every value of Vds (0.5V, 1.0V, 1.5V, 2.0V, 2.5V), sweep Vgs from 0 to 1.8V in 0.1V steps."

[Insert Id-Vgs Family Curves Image]

Short-Channel Device Characteristics
For L = 0.25μm devices, the Id-Vgs relationship reveals the transition from quadratic to linear behavior as Vds increases:

[Insert Short-Channel Id-Vgs Image]

At low Vds, the device still exhibits quadratic behavior. At high Vds, velocity saturation dominates, producing linear Id-Vgs dependence.

L3: Velocity Saturation at Lower and Higher Electric Fields
The Physics of Velocity Saturation
In short-channel devices, the lateral electric field (E = Vds/L) becomes extremely high—often exceeding 10⁵ V/cm. Under these conditions, carrier transport deviates from the simple drift model.

Classical drift model:
v = μE

Where:

v = Carrier velocity

μ = Mobility (constant)

E = Electric field

Reality at high fields:
Velocity increases linearly with E only up to a critical field (Ec), beyond which it saturates due to:

Optical phonon scattering

Carrier heating effects

Reduced mobility at high fields

[Insert Velocity vs Electric Field Plot Image]

Four Regions of Operation for Short-Channel Devices
Due to velocity saturation, short-channel MOSFETs exhibit four distinct operating regions:

Region	Condition	Characteristics
Cut-off	Vgs < Vt	No channel, Id ≈ 0
Linear	Vds < Vdsat	Normal resistive behavior
Saturation	Vds ≥ Vdsat	Classical pinch-off
Velocity Saturation	High Vgs, high Vds	Current limited by carrier velocity
[Insert Four Regions Diagram Image]

Impact on Device Characteristics
Velocity saturation becomes increasingly pronounced at higher gate-source voltages:

[Insert Velocity Saturation Effect Image]

Key observations:

At low Vgs, normal quadratic behavior persists

At high Vgs, current is linear with Vgs

Peak current is lower than long-channel predictions

Device enters saturation at lower Vds

L4: Velocity Saturation Drain Current Model
Modified Current Equations
Let's define Vgt = Vgs - Vt (gate overdrive voltage). For short-channel devices in saturation, the current equation becomes:

Id(sat) = W · vsat · Cox · (Vgt - Vdsat/2)

Where:

vsat = Saturation velocity (~10⁷ cm/s for silicon)

Vdsat = Saturation voltage at which velocity saturation occurs

[Insert Velocity Saturation Equation Image]

Understanding Vdsat
The saturation voltage in the presence of velocity saturation is given by:

Vdsat = (Ec · L) · (√(1 + 2Vgt/(Ec · L)) - 1)

For very short channels (L → 0), Vdsat approaches Ec · L.

[Insert Vdsat Derivation Images]

Counterintuitive Scaling Behavior
Traditional scaling theory predicts that reducing channel length increases current drive:

Id ∝ 1/L

However, velocity saturation fundamentally changes this relationship:

[Insert Current vs Channel Length Plot Image]

Observation 2: Reduced Saturation Current

For deeply scaled nodes, the saturation current is lower than expected rather than higher. This occurs because:

Velocity saturation causes the device to saturate earlier (at lower Vds)

The peak current is limited by vsat, not mobility

Short-channel effects further degrade current drive

[Insert Peak Current Comparison Image]

L5: Sky130 Id-Vgs Simulation Labs
Setting Up Short-Channel Simulations
Navigate to the Day 2 design directory:

text
$ cd sky130CircuitDesignWorkshop/design/day2
[Insert Day2 Directory Image]

NMOS Id-Vds Simulation for Short Channel
Create a simulation deck for L = 0.15μm (minimum channel length for Sky130):

spice
* Sky130 Short-Channel NMOS Id-Vds
.include '../../models/lib.spice'

* Using minimum channel length device
M1 D G 0 0 sky130_fd_pr__nfet_01v8__tt W=0.39u L=0.15u

* Bias conditions
Vgs G 0 DC 1.8V
Vds D 0 DC 0V

* Sweep Vds for multiple Vgs values
.dc Vds 0 1.8 0.01 Vgs 0.2 1.8 0.2

* Output
.plot dc I(M1)
.option plotwinsize=0
.end
[Insert Simulation Deck Images]

Analyzing Short-Channel Id-Vds Characteristics
Run the simulation:

text
$ ngspice nfet_idvd_short.spice
[Insert Ngspice Run Image]

The resulting plot shows distinct behavior:

[Insert Short-Channel Id-Vds Plot Image]

Key observations:

At low Vgs (0.2V - 0.8V): Curves show quadratic behavior

At high Vgs (1.0V - 1.8V): Curves become linear due to velocity saturation

Extracting Peak Current
To find the maximum drain current at Vgs = 1.8V:

Left-click on the curve corresponding to Vgs = 1.8V

The cursor displays the current value at any Vds point

Peak current occurs at Vds = 1.8V

[Insert Peak Current Extraction Image]

For W = 0.39μm, L = 0.15μm, the peak current is approximately 198μA.

Id-Vgs Transfer Characteristics
Now examine Id vs. Vgs with constant Vds:

spice
* Sky130 Short-Channel Id-Vgs
.include '../../models/lib.spice'

M1 D G 0 0 sky130_fd_pr__nfet_01v8__tt W=0.39u L=0.15u
Vds D 0 DC 1.8V
Vgs G 0 DC 0V

.dc Vgs 0 1.8 0.01
.plot dc I(M1)
.end
[Insert Id-Vgs Simulation Images]

The resulting transfer characteristic reveals:

[Insert Id-Vgs Plot Image]

Subthreshold region (Vgs < 0.5V): Exponential current increase

Quadratic region (0.6V < Vgs < 1.2V): Classical square-law behavior

Linear region (Vgs > 1.2V): Velocity saturation dominates

L6: Sky130 Threshold Voltage (Vt) Extraction
Determining Threshold Voltage
The threshold voltage (Vt) is a critical parameter defined as the gate voltage at which significant conduction begins. Several extraction methods exist:

Method 1: Maximum Transconductance Method

Plot Id vs. Vgs

Find the point of maximum slope (maximum gm)

Extrapolate the tangent line to Id = 0

The intercept is Vt

[Insert Vt Extraction Diagram Image]

Practical Vt Extraction
For our Sky130 short-channel device:

spice
* Vt Extraction
.include '../../models/lib.spice'

M1 D G 0 0 sky130_fd_pr__nfet_01v8__tt W=0.39u L=0.15u
Vds D 0 DC 0.1V  * Use small Vds for linear region
Vgs G 0 DC 0V

.dc Vgs 0 1.8 0.001
.plot dc I(M1)
.end
[Insert Vt Extraction Simulation Image]

Extraction Steps:

Identify the linear region of the Id-Vgs curve (where current rises steeply)

Draw a tangent at the point of maximum slope

Extend the tangent to intersect the Vgs axis (Id = 0)

Read Vt at the intersection point

[Insert Tangent Method Image]

For the Sky130 short-channel NMOS with W=0.39μm, L=0.15μm, the extracted Vt is approximately 0.76V.

Factors Affecting Vt
Factor	Effect on Vt
Channel Length	Shorter channels → Lower Vt (Vt roll-off)
Drain Voltage	Higher Vds → Lower Vt (DIBL effect)
Temperature	Higher temp → Lower Vt
Body Bias	Reverse bias → Higher Vt
CMOS Voltage Transfer Characteristics (VTC)
L1: MOSFET as a Switch
The Switch Analogy
To understand CMOS inverter operation, it's helpful to view each MOSFET as an ideal voltage-controlled switch:

[Insert MOSFET Switch Analogy Image]

Switch Operation:

When |Vgs| < |Vt|: MOSFET is OFF → Acts as open switch

[Insert Open Switch Image]

When |Vgs| > |Vt|: MOSFET is ON → Acts as closed switch with finite resistance

[Insert Closed Switch Image]

Switch Model Parameters
For circuit analysis, the ON resistance (Ron) is given by:

Ron = 1/[μ·Cox·(W/L)·(Vgs - Vt)]

This resistance determines how quickly a MOSFET can charge or discharge a capacitive load.

L2: Standard MOS Voltage and Current Parameters
CMOS Inverter Structure
The CMOS inverter consists of a complementary pair:

Pull-up network: PMOS transistor connected to VDD

Pull-down network: NMOS transistor connected to VSS (GND)

[Insert CMOS Inverter Structure Image]

Operating States
Case 1: Vin = HIGH (VDD)

PMOS: Vsg = 0V → Vsg < |Vtp| → PMOS OFF

NMOS: Vgs = VDD → Vgs > Vtn → NMOS ON

[Insert Vin High Equivalent Circuit Image]

Current flows from the output load through the NMOS to ground, discharging the capacitor.

Case 2: Vin = LOW (0V)

PMOS: Vsg = VDD → Vsg > |Vtp| → PMOS ON

NMOS: Vgs = 0V → Vgs < Vtn → NMOS OFF

[Insert Vin Low Equivalent Circuit Image]

Current flows from VDD through the PMOS to charge the output capacitor.

Current Relationships
In steady-state DC operation:

Idsn = -Idsp

The currents are equal in magnitude but opposite in direction.

[Insert Current Direction Image]

L3: PMOS and NMOS Drain Current vs. Drain Voltage
Individual Device Characteristics
NMOS Characteristics:

Idsn vs. Vdsn for various Vgsn

Vgsn = Vin (since source is grounded)

[Insert NMOS Id-Vds Family Image]

PMOS Characteristics:

Idsp vs. Vdsp for various Vsgp

Note: PMOS currents are negative (conventional current flows from source to drain)

[Insert PMOS Id-Vds Family Image]

Complementary Nature
When combined in an inverter:

NMOS conducts when Vin is HIGH

PMOS conducts when Vin is LOW

Both conduct during the switching transition

L4: Step 1 - Convert PMOS Gate-Source Voltage to Input Voltage (Vin)
From Internal to External Voltages
Users cannot directly observe internal transistor voltages—only Vin and Vout are accessible. We must express all device voltages in terms of these external quantities.

Assumptions for this analysis:

Long-channel devices

VDD = 2.0V

Symmetric threshold voltages (|Vtp| = Vtn)

PMOS Voltage Relationships
For the PMOS transistor:

Vgsp = Vin - VDD

Vin (V)	Vgsp (V)
0.0	-2.0
0.5	-1.5
1.0	-1.0
1.5	-0.5
2.0	0.0
[Insert Vgsp Conversion Table Image]

Plotting PMOS Characteristics in Terms of Vin
We can now replot the PMOS Id-Vdsp curves with Vin as the parameter:

[Insert PMOS Curves with Vin Parameter Image]

Each curve corresponds to a specific Vin value, making it easier to analyze the combined inverter operation.

L5: Step 2 & 3 - Convert PMOS and NMOS Drain-Source Voltage to Output Voltage (Vout)
PMOS Drain-Source Voltage Conversion
For PMOS:

Vdsp = Vout - VDD

This represents a shift of the voltage axis. When Vout = VDD, Vdsp = 0V. When Vout = 0V, Vdsp = -VDD.

[Insert Vdsp to Vout Conversion Image]

Example interpretation:

When Vout = 2V: Vdsp = 0V → PMOS has zero current (consistent with cut-off)

When Vout = 0V: Vdsp = -2V → PMOS can conduct maximum current

PMOS Load Curves
By applying this transformation, we obtain the PMOS load curves:

[Insert PMOS Load Curves Image]

These curves show the current the PMOS can deliver at each Vout for a given Vin.

NMOS Direct Mapping
For NMOS, the mapping is straightforward:

Vgsn = Vin
Vdsn = Vout

[Insert NMOS Direct Mapping Image]

The NMOS load curves are simply the standard Id-Vds characteristics with Vin as the parameter.

[Insert NMOS Load Curves Image]

L6: Step 4 - Merge PMOS and NMOS Load Curves to Plot VTC
Superposition of Load Curves
The voltage transfer characteristic is found by superimposing the PMOS and NMOS load curves and finding the intersection points for each Vin.

[Insert Merged Load Curves Image]

For each Vin value, we find the Vout where:
Idsn(Vin, Vout) = -Idsp(Vin, Vout)

This is the DC operating point of the inverter.

Complete VTC Analysis
Vin = 0V:

NMOS: Cut-off (Idsn = 0)

PMOS: Linear region, maximum current

Vout = 2V (PMOS pulls output to VDD)

[Insert Vin=0 Operating Point Image]

Vin = 0.5V:

NMOS: Saturation region (just turning on)

PMOS: Linear region (still strongly on)

Vout ≈ 1.8V (slightly below VDD)

Vin = 1.0V:

NMOS: Saturation region

PMOS: Saturation region

Vout ≈ 1.0V (both devices in saturation, midpoint)

Vin = 1.5V:

NMOS: Linear region (strongly on)

PMOS: Saturation region (just turning off)

Vout ≈ 0.2V (near ground)

Vin = 2.0V:

NMOS: Linear region, maximum current

PMOS: Cut-off (Idsp = 0)

Vout = 0V (NMOS pulls output to ground)

Summary of Operating Regions
Vin Range	Vout Range	NMOS Region	PMOS Region
0V	2V	Cut-off	Linear
0V - 0.5V	1.5V - 2V	Saturation	Linear
0.5V - 1.5V	0.5V - 1.5V	Saturation	Saturation
1.5V - 2V	0V - 0.5V	Linear	Saturation
2V	0V	Linear	Cut-off
Final VTC Plot
Connecting all operating points yields the classic inverting voltage transfer characteristic:

[Insert Complete VTC Plot Image]

Key VTC Parameters:

VOH = Maximum output voltage (≈ VDD)

VOL = Minimum output voltage (≈ GND)

VIL = Input voltage where gain = -1 (beginning of transition)

VIH = Input voltage where gain = -1 (end of transition)

VM = Switching threshold (Vout = Vin)

Gain = ΔVout/ΔVin (maximum in transition region)

Key Takeaways for Day 2
Concept	Key Insight
Velocity Saturation	Limits current in short-channel devices; causes linear Id-Vgs at high Vgs
Four Operating Regions	Short-channel devices add velocity saturation to classical regions
Vt Extraction	Tangent method yields Vt ≈ 0.76V for Sky130 short-channel NMOS
VTC Construction	Merge PMOS and NMOS load curves by expressing all voltages in terms of Vin, Vout
Operating Regions	CMOS inverter passes through all regions during switching
