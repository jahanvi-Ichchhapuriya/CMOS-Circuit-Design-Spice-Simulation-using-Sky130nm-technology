# CMOS-Circuit-Design-Spice-Simulation-using-Sky130nm-technology
This repository contains a comprehensive series of SPICE simulation labs and tutorials for CMOS circuit design using the open-source Sky130nm. The content is structured across five days of progressively complex topics, from basic NMOS characteristics to complete CMOS inverter robustness analysis.
## Table Of Contents
- [Day1-Basics of NMOS Drain Current(Id) vs Drain-to-source Voltage(Vds)](#Day1-Basics-of-NMOS-Drain-Current(Id)-vs-Drain-to-source-Voltage(Vds))
  - [Introduction to Circuit Design and Spice Simulations](#Introduction-to-Circuit-Design-and-Spice-Simulations)
    - [L1 Why do we need SPICE simulations?](#L1-Why-do-we-need-SPICE-simulations?)
    - [L2 Introduction to basic element in circuit design-NMOS](#L2-Introduction-to-basic-element-in-circuit-design-NMOS)
    - [L3 Strong inversion and threshold voltage](#L3-Strong-inversion-and-threshold-voltage)
    - [L4 Threshold voltage with positive substrate potential](#L4-Threshold-voltage-with-positive-substrate-potential)
  - [NMOS resistive region and Saturation region of operation](#NMOS-resistive-region-and-Saturation-region-of-operation)
    - [L1 Resistive region of operation with small drain-source voltage](#L1-Resistive-region-of-operation-with-small-drain-source-voltage)
    - [L2 Drift current theory](#L2-Drift-current-theory)
    - [L3 Drain current model for Linear region of operation](#L3-Drain-current-model-for-Linear-region-of-operation)
    - [L4 SPICE conclusion to resistive operation](#L4-SPICE-conclusion-to-resistive-operation)
    - [L5 Pinch-off region condition](#L5-Pinch-off-region-condition)
    - [L6 Drain current model for saturation region of operation](#L6-Drain-current-model-for-saturation-region-of-operation)
  - [Introduction to SPICE](#Introduction-to-SPICE)
    - [L1 Basic SPICE setup](#L1-Basic-SPICE-setup)
    - [L2 Circuit description in SPICE syntax](#L2-Circuit-description-in-SPICE-syntax)
    - [L3 Define Technology parameters](#L3-Define-Technology-parameters)
    - [L4 First SPICE simulation](#L4-First-SPICE-simulation)
    - [L5 SPICE lab with Sky130 models](#L5-SPICE-lab-with-Sky130-models)
- [Day2-Velocity saturation and basics of CMOS inverter VTC](#Day2-Velocity-saturation-and-basics-of-CMOS-inverter-VTC)
  - [SPICE simulation for lower nodes and velocity saturation effect](#SPICE-simulation-for-lower-nodes-and-velocity-saturation-effect)
    - [L1 SPICE simulation for lower nodes](#L1-SPICE-simulation-for-lower-nodes)
    - [L2 Drain current vs gate voltage for long and short channel device](#L2-Drain-current-vs-gate-voltage-for-long-and-short-channel-device)
    - [L3 Velocity saturation at lower and higher electric fields](#L3-Velocity-saturation-at-lower-and-higher-electric-fields)
    - [L4 Velocity saturation drain current model](#L4-Velocity-saturation-drain-current-model)
    - [L5 Labs Sky130 Id-Vgs](#L5-Labs-Sky130-Id-Vgs)
    - [L6 Labs Sky130 Vt](#L6-Labs-Sky130-Vt)
  - [CMOS voltage transfer characteristics (VTC)](#CMOS-voltage-transfer-characteristics-(VTC))
    - [L1 MOSFET as a switch](#L1-MOSFET-as-a-switch)
    - [L2 Introduction to standard MOS voltage current parameters](#L2-Introduction-to-standard-MOS-voltage-current-parameters)
    - [L3 PMOS/NMOS drain current vs drain voltage](#L3-PMOS/NMOS-drain-current-vs-drain-voltage)
    - [L4 Step1- Convert PMOS gate-source-voltage to Vin](#L4-Step1--Convert-PMOS-gate-source-voltage-to-Vin)
    - [L5 Step2 & Step3- Convert PMOS and NMOS drain-source-voltage to Vout](#L5-Step2-&-Step3--Convert-PMOS-and-NMOS-drain-source-voltage-to-Vout)
    - [L6 Step4- Merge PMOS-NMOS load curves and plot VTC](#L6-Step4--Merge-PMOS-NMOS-load-curves-and-plot-VTC)
- [Day3-CMOS switching threshold and dynamic simulations](#Day3-CMOS-switching-threshold-and-dynamic-simulations)
  - [Voltage transfer characteristics-SPICE simulations](#Voltage-transfer-characteristics-SPICE-simulations)
    - [L1 SPICE deck creation for CMOS inverter](#L1-SPICE-deck-creation-for-CMOS-inverter)
    - [L2 SPICE simulation for CMOS inverter](#L2-SPICE-simulation-for-CMOS-inverter)
    - [L3 Labs Sky130 SPICE simulation for CMOS](#L3-Labs-Sky130-SPICE-simulation-for-CMOS)
  - [Static behaviour evaluation-CMOS inverter robustness-Switching Threshold](#Static-behaviour-evaluation-CMOS-inverter-robustness-Switching-Threshold)
    - [L1 Switching Threshold, Vm](#L1-Switching-Threshold,-Vm)
    - [L2 Analytical expression of Vm as a function of (W/L)n and (W/L)p](#L2-Analytical-expression-of-Vm-as-a-function-of-(W/L)n-and-(W/L)p)
    - [L3 Analytical expression of (W/L)n and (W/L)p as a function of Vm](#L3-Analytical-expression-of-(W/L)n-and-(W/L)p-as-a-function-of-Vm)
    - [L4 Static and Dynamic simulation of CMOS inverter](#L4-Static-and-Dynamic-simulation-of-CMOS-inverter)
    - [L5 Static and Dynamic simulation of CMOS inverter with increased PMOS width](#L5-Static-and-Dynamic-simulation-of-CMOS-inverter-with-increased-PMOS-width)
    - [L6 Applications of CMOS inverter in clock network and STA](#L6-Applications-of-CMOS-inverter-in-clock-network-and-STA)
- [Day4-CMOS Noise Margin robustness evaluation](#Day4-CMOS-Noise-Margin-robustness-evaluation)
  - [Static behaviour evaluation-CMOS inverter robustness-Noise Margin](#Static-behaviour-evaluation-CMOS-inverter-robustness-Noise-Margin)
    - [L1 Introduction to Noise Margin](#L1-Introduction-to-Noise-Margin)
    - [L2 Noise Margin voltage paramters](#L2-Noise-Margin-voltage-paramters)
    - [L3 Noise margin equation and summary](#L3-Noise-margin-equation-and-summary)
    - [L4 Noise margin variation with respect to PMOS width](#L4-Noise-margin-variation-with-respect-to-PMOS-width)
    - [L5 Sky130 Noise margin labs](#L5-Sky130-Noise-margin-labs)
- [Day5-CMOS power supply and device variation robustness evaluation](#Day5-CMOS-power-supply-and-device-variation-robustness-evaluation)
  - [Static behaviour evaluation-CMOS inverter robustness-Power supply variation](#Static-behaviour-evaluation-CMOS-inverter-robustness-Power-supply-variation)
    - [L1 Smart SPICE simulations for power supply variations](#L1-Smart-SPICE-simulations-for-power-supply-variations)
    - [L2 Advantages and disadvantages using low supply voltage](#L2-Advantages-and-disadvantages-using-low-supply-voltage)
    - [L3 Sky130 Supply variation Labs](#L3-Sky130-Supply-variation-Labs)
  - [Static behaviour evaluation-CMOS inverter robustness-Device variation](#Static-behaviour-evaluation-CMOS-inverter-robustness-Device-variation)
    - [L1 Sources of variation - Etching process](#L1-Sources-of-variation---Etching-process)
    - [L2 Sources of variation - Oxide thickness](#L2-Sources-of-variation---Oxide-thickness)
    - [L3 Smart SPICE simulation for device variations](#L3-Smart-SPICE-simulation-for-device-variations)
    - [L4 Conclusion](#L4-Conclusion)
    - [L5 Sky130 device variations labs](#L5-Sky130-device-variations-labs)

# Day1-Basics of NMOS Drain Current(Id) vs Drain-to-source Voltage(Vds)

## Introduction to Circuit Design and Spice Simulations

### L1 Why do we need SPICE simulations?
Modern digital circuits are built using complementary MOS (CMOS) technology, where PMOS and NMOS transistors are interconnected to form fundamental logic gates—NAND, NOR, OR, AND, and the most basic building block, the **inverter**.
</br>

<img width="547" height="487" alt="image" src="https://github.com/user-attachments/assets/fa0a416d-73b5-4060-80ee-60ca0b97e0ae" />

Through SPICE simulations, we characterize this inverter's delay behavior and derive the appropriate W/L ratios for both PMOS and NMOS transistors.</br>

**WHy do we need SPICE?**</br>
SPICE simulations are the bedrock of three critical aspects of digital design:
- **Clock Tree Synthesis (CTS)** : Requires delay information for buffer placement and sizing
- **Timing Analysis**: Depends on accurate cell delay characterization
- **Crosstalk Analysis**: Needs delay variations to assess signal integrity

Without SPICE, we cannot determine delays. Without delays, the physical design flow operates blindly, and crosstalk analysis becomes meaningless..</br>

Let us say we have done some Clock Tree Synthesis of the circuit shown below with bufffers with different capacitive load at the output.</br>
<img width="386" height="359" alt="image" src="https://github.com/user-attachments/assets/8358dc5f-2b2b-49ae-8d8c-daf22c37fb90" />

**Let us assume C1 = C2 = C3 = C4 = 25fF**</br>
How about creating a buffer tree at node 'A'</br>
Let us assume Cbuf1 = Cbuf2 = 30fF</br>
Therefore, total Cap at node 'A' => 60fF</br>
Therefore, total Cap at node 'B' => 50fF</br>
Therefore, total Cap at node 'C' => 50fF</br>

**Here Observations are**</br>
* 2 levels of buffering
At every level, each node driving same load
* Identical buffer at same level

After the SPICE simulation we get a "Delay Table", which includes input slew and output load. The intersection value of Input slew and Output load is considered as Delay. Delay tables for both level 1 and level 2 buffers have been shown. This is calculated by circuit design and simulation</br>

<img width="1055" height="261" alt="image" src="https://github.com/user-attachments/assets/8ff27026-f0d6-4c02-99d4-ea3703a00461" />

The source of the above Delay Tables comes from circuit design using SPICE simulations. SPICE simulations involves characterisation of any CMOS logic.</br>

### L2 Introduction to basic element in circuit design-NMOS
An NMOS transistor consist of P-type substrate, heavily doped with n+ region. There is an isolated region which isolates the transistor from other transistors. The n+regions are Source and Drain. Above itthere is an oxide layer, and top of it is metal deposition which is the GAte termianal.</br>

<img width="558" height="490" alt="image" src="https://github.com/user-attachments/assets/4ca9adc2-2c44-4f11-98e7-0ad0cd42485a" />

## NMOS
* 4 terminal Device
* Consists of P-Substrate
* Isolation Region (SiO2)
* n+ Diffusion Region
* Gate Oxide
* Poly-Si or metal gate
* G -Gate
* S - Source
* D - Drain
* B - Body


**Threshold Voltage**</br>
This is a very important term, all the characterisation depends on threshold voltage.</br>
At first we will keep the Vgs=0, means source and drain terminal both are grounded. Body is also ground. P-substrate and n+ act as PN junction diode and as there is no potential so there is a high resistance. No channel formation is there.</br>
<img width="499" height="429" alt="image" src="https://github.com/user-attachments/assets/9d3deabe-d57f-4ab8-82ac-be1101c5ff63" />

Now we will apply a positive potential; Vgs>0. We will see gate is now positively charged and due to this there will be Accumulation of negative charges at the surface of substrate.</br>
<img width="713" height="368" alt="image" src="https://github.com/user-attachments/assets/21ae5a87-783c-43ba-b1ed-90eab1c08dc0" />

### L3 Strong inversion and threshold voltage
Due to Accumulation of negatuve charges, there will be formation of Depletion Region, depleting of it's majority carriers i.e positive carriers here.</br>

<img width="831" height="402" alt="image" src="https://github.com/user-attachments/assets/335a3525-699e-4c66-8161-2201df2b9070" />

Now we will increase the Gate voltage further, we will see that the positive charge carriers will be repelled and there will be increase of Depletion Width. On further increase of Gate voltage we will reach at a point where the surface gets inverted into an n-type material, this is called "Surface Inversion" or "Strong Inversion". The gate voltage of Vgs voltage where "Strong Inversion" happens is called "Threshold Voltage".</br>

<img width="732" height="411" alt="image" src="https://github.com/user-attachments/assets/24694a9d-523c-4363-bcd0-95eb5f3c2cd4" />

What will happen if we further increase Vgs? As there are no more negative charges that will be attracted towards the positive Vgs, The negative charges from n+ region will get attracted and so there will be a formation of channel at the surface.</br>

<img width="482" height="446" alt="image" src="https://github.com/user-attachments/assets/c5805eb4-1587-4426-b747-e6f1b65c9d56" />

**Threshold Voltage**</br>
* Vgs = 0
* Drain, Source, Bulk connected to GND
* Substrate-Source (B-S) and Substrate-Drain (B-D) form p-n junction diode
* Both junctions are 'off' due to OV bias
* Hence, S-D resistance is 'high'
Apply +ve Vgs voltage
* Increase gate voltage "Vgs'
* This phenomenon is called 'strong inversion'
* The "Vgs' voltage at which 'strong inversion' occurs is called threshold vge (Vt)
* Further, increase "Vgs'
* No Change in depletion layer width
* Electrons from heavily doped 'n+' source region are drawn in region under gate 'G'

<img width="492" height="433" alt="image" src="https://github.com/user-attachments/assets/bcd6cba0-7eb7-4d8b-a6a3-aab44d5a526f" />


<img width="485" height="448" alt="image" src="https://github.com/user-attachments/assets/0aaf8167-cdb8-429a-bc0f-75b4afe5a301" />

**Threshold Voltage**</br>
* Vgs = 0
* Drain, Source, Bulk connected to GND
* Substrate-Source (B-S) and Substrate-Drain (B-D) form p-n junction diode
* Both junctions are 'off' due to OV bias
* Hence, S-D resistance is 'high'
* Apply +ve Vgs voltage
* Increase gate voltage 'Vgs'
* This phenomenon is called 'strong inversion'
* The "Vgs' voltage at which 'strong inversion' occurs is called threshold vge (Vt)
* Further, increase 'Vgs'
* No Change in depletion layer width
* Electrons from heavily doped 'n+' source region are drawn in region under gate 'G'
Continuous n-channel formation from
S-D, whose conductivity is modulated by 'Vgs

Now there is a possibility of current from Source to Drain. The channel has bridged the gap between source to drain regions. But as there is no Drain voltage so the elctrons will not move, this is "Cut Off Region" now.</br>

We will see what happens when we change the potential of Body terminal.</br>

<img width="1311" height="532" alt="image" src="https://github.com/user-attachments/assets/0aa83b1f-12c2-4765-bd3f-caa35daac877" />

There will be increase in depletion region between source and body terminal. </br>

<img width="1283" height="607" alt="image" src="https://github.com/user-attachments/assets/1dd9f64e-5345-4dc9-98b2-6dcde19765ef" />

### L4 Threshold voltage with positive substrate potential
If we increase Vgs, we will see that the depletion region increase in both the cases. But, in second case as there is Vsb +ve, few charges from channel will be pulled towards the source.</br>
![WhatsApp Image 2026-02-27 at 5 41 57 PM](https://github.com/user-attachments/assets/c4ea3c2d-16e2-43ab-8d95-19425d1a8473)

<img width="895" height="694" alt="image" src="https://github.com/user-attachments/assets/864013fc-8998-4a45-8607-ebc5bda062ab" />

Due to this the surface inversion will be slower in second case. Therefore some extra potential has to be apllied in second case to create inversion.</br>

<img width="1356" height="658" alt="image" src="https://github.com/user-attachments/assets/98b3483c-2c33-4244-b96d-6098ee9b0163" />


The parameters such as Gamma comes from foundaries after simulation of which in SPICE we get the value for Vt (Threshold Voltage).</br>

<img width="1327" height="643" alt="image" src="https://github.com/user-attachments/assets/8955fdc9-1230-4562-b513-4eca06eb5d3c" />

## NMOS resistive region and Saturation region of operation

### L1 Resistive region of operation with small drain-source voltage
Previously, we saw Cut Off region operation, now we will see the "Resistive region"/"Linear Region" of operation by applying Drain-source voltage.
If we keep on increasing the Gate-source voltage, the channel width keeps on increasing.</br>

<img width="1305" height="508" alt="image" src="https://github.com/user-attachments/assets/29f349a8-c77e-4d13-a323-82b1fa6bfb74" />

This shows that the net Induced charges is propotional to (Vgs-Vt). Now let's apply very small Vds at start. And keep Vt=0.45V, Vgs also small initially.</br>

<img width="1317" height="567" alt="image" src="https://github.com/user-attachments/assets/aed1572f-fd2b-492d-82ca-bd1ce4a94b1e" />

We can see that the source is grounded and Drain is at some potential, so there will be a voltage gradient accross the channel.</br>

<img width="1318" height="577" alt="image" src="https://github.com/user-attachments/assets/bf52a8c7-5553-4c74-888c-cdb43b09e3bc" />

Also, the Effective channel length is much lesser than the original channel length.</br>

<img width="797" height="510" alt="image" src="https://github.com/user-attachments/assets/c35a777b-b625-495c-bb37-9f92dfd92a64" />

Here, y axis represents the width of transistor and x axis is the voltage across the channel.</br>
On applying Vds, every point on x axis will vary w.r.t to Vgs-V(x), this will decide the current equation.</br>

<img width="817" height="558" alt="image" src="https://github.com/user-attachments/assets/a472661e-b9bd-4cfb-8437-ea5be2474fe2" />

### L2 Drift current theory
We know the effective channel voltage will vary w.r.t x, for example at x=0, Vgs=1V and V(x)=0, So the Vgs-Vx=1V. At x=Vds=0.05V, Vgs-Vx=0.95V. Now if we see the induced chagre equation, it is proportional to the effective channel voltage.</br>

<img width="411" height="150" alt="image" src="https://github.com/user-attachments/assets/f303fe6e-388f-4395-9650-e7121cd5aff4" />

<img width="390" height="451" alt="image" src="https://github.com/user-attachments/assets/14f8c404-0d02-4d21-8d67-b20ff1801eae" />

There are two types of currents; Dift and Diffusion current, Here there is Drift current as there is potential difference across the channel.</br>

<img width="1285" height="618" alt="image" src="https://github.com/user-attachments/assets/e1ba1c63-b342-4377-9fe8-1a2e58c93e02" />

To get the drain current, we will see the top view of transistor.</br>

<img width="1311" height="687" alt="image" src="https://github.com/user-attachments/assets/6c473806-a163-4120-974a-73e11da97839" />

### L3 Drain current model for Linear region of operation
As there is change of voltage across the channel length, this will result in change of velocity which is a function of mobility and electrci field.</br>

<img width="448" height="651" alt="image" src="https://github.com/user-attachments/assets/6518460a-1e4c-481f-8341-d99a1fa9a376" />

We will integrate the above equation, where limits of dV will be from 0 to Vds and limits of dx will be from 0 to L.</br>

<img width="442" height="428" alt="image" src="https://github.com/user-attachments/assets/382f07af-71b5-4f00-894d-bdab05e92d0e" />

<img width="377" height="48" alt="image" src="https://github.com/user-attachments/assets/f6f5158c-850f-4272-b381-0b57dc30e7a9" />

Here, Cox, W/L, Vgs, un and Vt are the 'technology parameters', we will simulate usinf SPICE and find out the characteristics.</br>

<img width="387" height="211" alt="image" src="https://github.com/user-attachments/assets/ee457e12-6af7-4389-a11a-036ba5a4b652" />

But, here we cannot say that it is in Linear region, since the Drain current is the quadratic function of Vds. We will calculate the Id with the given values.</br>

<img width="708" height="432" alt="image" src="https://github.com/user-attachments/assets/853ed5fa-0257-4a73-91dd-09007f16d273" />

When (Vgs-Vt)>=Vds, It is in "Linear region".</br>

<img width="683" height="443" alt="image" src="https://github.com/user-attachments/assets/bdfa5383-5b3b-452f-b437-0768814f2551" />

### L4 SPICE conclusion to resistive operation
We need to find the impact of Vgs and Vds on the drain current equation. We will consider different values of Vgs and Vds. If we consider different values of Vgs, under what condition the device will remain in Linear region depends on (Vgs-Vt) should be greater than Vds.</br>

<img width="591" height="172" alt="image" src="https://github.com/user-attachments/assets/d9735c9f-3a26-49aa-bc9b-62e64d65babe" />

Now the main question arises, How do we calculate Id for different values of 'Vgs' and at every value of 'Vgs', sweep Vds till (Vgs-Vt) using linear equation for Id?</br>
For this we need to do SPICE simulations.</br>

### L5 Pinch-off region condition
There is also a Region of operation when Drain-source voltage exceeds the value (Vgs-Vt), the region of operation is called "Saturation Region".
We know the channel voltage is Vgs-Vds. Now, we will increase the Vds.</br>

<img width="1367" height="625" alt="image" src="https://github.com/user-attachments/assets/d29ecff9-3641-49c7-9348-fa7537ff7118" />

When Vgs-Vds is greater than Vt, there will be a conducting channel.</br>
When Vgs-Vds is equal to Vt, we will see at drain side, just Inversion has happened as it is equal to Vt, so channel will start disappearing at drain side.</br>

<img width="1380" height="611" alt="image" src="https://github.com/user-attachments/assets/b51e39ef-093f-463d-8faa-7c6bb23cc68d" />
<img width="1352" height="621" alt="image" src="https://github.com/user-attachments/assets/8d325d80-10d4-47e3-aed0-2caaf0715a36" />

Now when the channel starts to disappear, is termed as "Pinch off region"</br>

<img width="1492" height="602" alt="image" src="https://github.com/user-attachments/assets/40146460-641e-4f89-a950-acebeba103e3" />

When Vgs-Vds<Vt, we will not see any channel present at drain side.</br>

<img width="1310" height="582" alt="image" src="https://github.com/user-attachments/assets/e62baac0-53e1-4c61-a9d6-e26a0a4b8ec1" />

This condition is termed as "Saturation region", when the mosfet is saturated and cannot do anything further.</br>

<img width="391" height="102" alt="image" src="https://github.com/user-attachments/assets/4c0aca6a-e230-47d1-9e30-9416785487be" />

### L6 Drain current model for saturation region of operation
In saturation region, the channel voltage will remain constant as 'Vgs-Vt', and the drain current will not depend on Vds.</br>
To get drain current equation in saturation region we will replace Vds as Vgs-Vt.</br>

<img width="467" height="360" alt="image" src="https://github.com/user-attachments/assets/3df0adef-9616-499c-97de-477da403178b" />

We can now see that according to the equation, the mosfet acts as perfect current source. But this is not true, when we increase Vds we will that Depletion region at drain increases and so channel length further reduces.Therefore, we see a slight dependency of Vds over Id</br>

<img width="1476" height="586" alt="image" src="https://github.com/user-attachments/assets/899bf2cb-f752-43ad-8750-5fc9d6b62f50" />

This is called "Channel Length Modulation".</br>

<img width="876" height="168" alt="image" src="https://github.com/user-attachments/assets/b3d388c1-7074-49c9-a019-7d0ff212271f" />

## Introduction to SPICE

### L1 Basic SPICE setup
First let us look into the SPICE setup.</br>

![WhatsApp Image 2026-02-27 at 2 16 43 PM](https://github.com/user-attachments/assets/706d9976-836f-4e25-a1cf-776cd8468d1b)

Some parameters are constant, and directly coming from the foundaries we don't have to derive them. These are circiled in yellow.</br>

So, when we feed the SPICE model parameters and SPICE netlist intp the SPICE software, we get the device characteristics in terms of Id vs Vds with different values of Vgs.</br>

**SPICE Netlist**
We need to feed the device into SPICE engine in certain manner, the circuit equivalent of given mosfet is as shown below. </br>

### L2 Circuit description in SPICE syntax
Now we will write the syntax for this particular circuit in SPICE netlist. To do that we need to follow some steps-
* **Define Nodes**
* **Give names to the node**
* **Write the code**
  `since modfet has 4 terminals, it is lying between 4 different nodes, similarly resistor is lying between 2 nodes.`

![WhatsApp Image 2026-02-27 at 12 49 26 PM](https://github.com/user-attachments/assets/30d95df1-109c-4306-a6b1-894b7b0a1a3b)

The fashion in which it is written is "Drain", "Gate", "Source", and "Substrate" (DGSS).</br>
Similarly we can write for Resistor.</br>

![WhatsApp Image 2026-02-27 at 2 28 48 PM](https://github.com/user-attachments/assets/5292f483-739f-42dd-8e41-0f5bd14e4559)


### L3 Define Technology parameters
Now we will look for model of this particular NMOS. For this we have model paramters, and it becomes easy to model from the parameters. That is where the technology file comes into picture. The models for the name NMOs will be found in file which has the attribute of the similar name.</br>


Inside the brackets, technology paramteters will exist. Similarly for pmos also.</br>


Now, we just plug in this packaged file in `.mod` file and call this file in top level SPICE netlist.</br>


In the above image, the highlighted part is comment in SPICE.</br>
Now, we need to sweep the Vgs and Vds for SPICE simulations.</br>

### L4 First SPICE simulation
* Open Virtual box
* Type `cd`
* `git clone https://github.com/kunalg123/sky130CircuitDesignWorkshop.git`
 
  inside the `sky130_fd_pr` directory we will see cells, models and tech files.</br>

 
  Inside the `cells` files we will see `nfet` and `pfet` cells, these cells we will be using.</br>

  Inside `nfet` we will see spice libraries at different corners, we will select one such typical corner.</br>
 
  
  We will see all the model paramteres required for the process.</br>
  
 
  We have different W and L values which pre-described. For simulation we need to take any one value which is present inside the library.</br>

  
  Now go inside `models` --> `lib.spice` file. We will see library files which are present for nfet and pfet. The corner files are present, include Typical, slow-fast and fast-fast corner files.</br>

  
Inside `design` --> open day1 file.</br>

Above we see Vdd varying from 0 to 1.8 volts with step size of 0.1V and Vgs sweeping from 0 to 1.8V and with step size of 0.2V

Let us do the spice simulations:

We will get the plot of Id vs Vds at different Vgs values.</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/cb0bccce-ff20-4727-8062-962df8aa8017" />

To check the value of Id for corresponding Vds and Vgs, just left click and see.</br>

<img width="308" height="155" alt="image" src="https://github.com/user-attachments/assets/264c0ac3-955c-49b3-86f3-447e93e8e452" />

### L5 SPICE lab with Sky130 models
If we go inside `models` folder, we will see `all.spice` file. If we open it we will see the scale of Width and Length.</br>
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/0f6dfb1f-7668-466a-8ba7-c9ac5beacb77" />

We can see that W and L values are in microns.</br>

# Day2-Velocity saturation and basics of CMOS inverter VTC

## SPICE simulation for lower nodes and velocity saturation effect

### L1 SPICE simulation for lower nodes
We have seen the curve for Id vs Vds, for different values of Vgs.</br>

<img width="1297" height="658" alt="image" src="https://github.com/user-attachments/assets/c10158ab-7588-4862-96a0-19125d4a3e25" />

**Graph Regions (Long Channel):**

- Left of Vds = Vgs-Vt → Linear region</br>
- Right of Vds = Vgs-Vt → Saturation region (slight slope due to velocity saturation)</br>
- Below → Cut-off region</br>
**Key Point:** If W/L ratio is same, Id should be same in theory. But in practice, it changes due to short-channel effects.</br>

<img width="872" height="442" alt="image" src="https://github.com/user-attachments/assets/09eec98c-92a0-409e-a6c5-5b2a18e8289d" />

### L2 Drain current vs gate voltage for long and short channel device
Let us compare the two simulations we did.

<img width="1385" height="547" alt="image" src="https://github.com/user-attachments/assets/0dd21cb8-3868-4074-909f-accde3fa2556" />

**There are some Observations:**
* **Observation 1**- If we see Id values for different Vgs and for Vds=2.5V, there is a quadratic dependency of Id on Vgs. Whereas for short channel device, at Vds=2.5V, the current is increasing linearly due to velocity saturation.</br>

<img width="1385" height="547" alt="image" src="https://github.com/user-attachments/assets/3eb690d9-a38c-4c97-a9b2-2b0b5148ff63" />
<img width="747" height="540" alt="image" src="https://github.com/user-attachments/assets/7f388d3d-9e7c-45ad-b70b-65a1d846f961" />

Now we will plot graph of Id vs Vgs and sweeping Vds or keeping Vds constant = 2.5V.</br>

<img width="855" height="442" alt="image" src="https://github.com/user-attachments/assets/658d2ba4-4e01-4e20-9a01-e949f3f88cb9" />

The syntax explains that what will be there on left hand side will be sweeped at every value on right hand side. For example here for every value of Vdd, Vin will be sweeped. The plot we get is quadratic, it is only when Vds=2.5V </br>

<img width="776" height="641" alt="image" src="https://github.com/user-attachments/assets/fd8321e8-6235-4c84-aa42-411747b0f599" />

Let us see the same effect for short channel device. For L=0.25 micron.
<img width="1332" height="592" alt="image" src="https://github.com/user-attachments/assets/ffba63a2-5ce1-42c5-a7f0-0f61fe194d12" />

### L3 Velocity saturation at lower and higher electric fields
For short channel we will see more of a linear behaviour as the Vgs increases. This is due to velocity saturation effect.</br>

<img width="1332" height="592" alt="image" src="https://github.com/user-attachments/assets/95aa490e-3dc0-4875-b74a-836c1ae07486" />
So, for lower node we will have 4 regions of operations: **Cut Off, Linear, Saturation and Velocity Saturation**

**Velocity Saturation:**

- **v = μE** (velocity = mobility × electric field)
- At low E → v increases linearly
- At high E → v saturates (stops increasing)
- Reason: Scattering at high fields → mobility decreases

![WhatsApp Image 2026-02-27 at 2 52 16 PM](https://github.com/user-attachments/assets/0638d759-085a-4f20-b3c8-954263d7c095)

Velocity saturation happens for higher gate-source voltages.</br>

<img width="1011" height="470" alt="image" src="https://github.com/user-attachments/assets/bf8911ed-1708-4c95-adc1-f6816f66a689" />

### L4 Velocity saturation drain current model
<img width="987" height="473" alt="image" src="https://github.com/user-attachments/assets/cbe1cdbb-8b18-4c19-97c6-be3e4244fb34" />

**Step 1: Define Overdrive Voltage**
- Let **Vgt = Vgs - Vt**
- We use this because we are analyzing large Vgs values
- Vgt represents how much the gate voltage exceeds threshold

**Step 2: Simplify the Current Equation**
- The full current equation includes a λ (lambda) term for channel length modulation
- For small Vds values, we can neglect this term
- This makes our analysis simpler without losing much accuracy

**Step 3: Understand Vdsat**
- **Vdsat** is another important technology parameter
- It is the drain voltage at which velocity saturation begins
- When Vds reaches Vdsat, the device enters the velocity saturation region
- Beyond this point, increasing Vds does not increase current significantly</br>
<img width="831" height="212" alt="image" src="https://github.com/user-attachments/assets/2e70d7d1-4891-4488-90e8-93f9b5f1322c" />

<img width="1026" height="536" alt="image" src="https://github.com/user-attachments/assets/724c8f7e-e772-4006-9f39-05d7a8e06b56" />

<img width="1080" height="540" alt="image" src="https://github.com/user-attachments/assets/13ace523-0233-4dd0-802d-d1ab5f026de6" />

<img width="1006" height="538" alt="image" src="https://github.com/user-attachments/assets/2d5432ec-2438-41c5-9b52-2f658a17c006" />

<img width="1331" height="583" alt="image" src="https://github.com/user-attachments/assets/5a5755f0-0723-4aea-8f07-e277cf3fdf18" />

In the above equation, it seems when W is constant and L is lowered then Id should increase, But it is not so practically.</br>

* **Observation 2** - The saturation current for lower nodes is low instead of being high. This is because Velocity saturation tends to saturate the device early so the peak current we see for lower nodes is much lesser than for higher nodes.</vr>
<img width="1370" height="576" alt="image" src="https://github.com/user-attachments/assets/82010154-16a3-4079-a57c-e5a7435b9507" />

### L5 Labs Sky130 Id-Vgs
We will now do simulation for lower nodes. Inside day2 design file.</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/2e30ad35-dbfe-42e4-a2c6-1c3e3ffd3d8b" />

<img width="1915" height="1078" alt="image" src="https://github.com/user-attachments/assets/46853bc0-6ac5-4d4e-8c34-133b54530564" />

We can see above, simulation is being done for L=0.15u and W=0.39u.</br>
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/0112c1fb-efa5-4eb2-a5c2-9c34923067ab" />
<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/05b5bf4a-79e4-4b9e-b92d-938707164205" />

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/3455d86b-dd2b-4b41-aad6-4bee2f683440" />

**Id vs Vds Plot Observations:**

- Low Vgs → Quadratic curve</br>
- High Vgs → Linear curve (velocity saturation)</br>

**To get peak current at Vgs = 1.8V:** Left-click on the Vgs = 1.8V curve.</br>

<img width="290" height="22" alt="image" src="https://github.com/user-attachments/assets/83d91519-32f9-4d17-b88a-379635529e9a" />
So we can see it is approximately 198uA.</br>

**Now let us observe Id vs Vgs**
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/38b27e55-94b1-4190-9191-e022f3e3d548" />

Here again we are taking values for L=0.15u and W=0.39u, Keeping Vds constant at 1.8V and sweeping Vgs from 0 to 1.8V with step of 0.1V.</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/2c4fd12f-4995-43bc-b1bd-faaa1d6291a7" />
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/17f7032a-f654-4c22-81e9-acbc1cbe368f" />

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/b490e2f2-76aa-49f1-b37c-e986cb3e4126" />
In the above graph we can see that, due to short channel effect we are seeing a linear behaviour for higher Vgs and Vds being constant.</br>

### L6 Labs Sky130 Vt
Now we will calculate Threshold Voltage Vt for Id vs Vgs curve.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/1e4b97da-884d-4447-b8ae-4d83ff1aef33" />

In the curve we can see that Vt is the value when current increases drastically for small change in Vgs. To calculate we will draw tangent on the curve and see where it touches.</br>

<img width="292" height="30" alt="image" src="https://github.com/user-attachments/assets/dfd6b8ca-308f-425e-97d0-58cb1799fca4" />

It comes at around 0.76V.

## CMOS voltage transfer characteristics (VTC)

### L1 MOSFET as a switch
We will now look at the device parameters from the switch point of view.</br>

<img width="907" height="508" alt="image" src="https://github.com/user-attachments/assets/6bb70912-c36e-4031-bf01-7e05871b28a8" />
The above shows MOSFET as a switch:
* When |Vgs|<Vt, device is OFF and it acts as open switch
* When |Vgs|>Vt, device is ON and it acts as closed switch

<img width="1220" height="685" alt="image" src="https://github.com/user-attachments/assets/48869cbb-daee-4a3b-96a8-bdd0fb45a79f" />

### L2 Introduction to standard MOS voltage current parameters
We are trying to get the equivalent circuit of CMOS when Vin is 'high' and 'low', so that we can get the Voltage Transfer Characteristics (VTC) and therefore calculate the delay of the cell.</br>
![WhatsApp Image 2026-02-27 at 3 01 39 PM](https://github.com/user-attachments/assets/2e1329b7-1fd1-4142-bd5f-e84bceb4b7e9)

* Case 1: Input is High (Vin = Vdd)</br>
When we apply a high voltage (equal to the power supply, Vdd) to the input, the PMOS transistor turns OFF, and the NMOS transistor turns ON.</br>

* Case 2: Input is Low (Vin = 0)</br>
When we apply a low voltage (0V) to the input, the PMOS transistor turns ON, and the NMOS transistor turns OFF.</br>

**From this, we can understand the path the current takes:**</br>

When Vin = Vdd, a direct path is created between the ground (Vss) and the output (Vout). This allows the capacitor (CL) connected to the output to discharge through the NMOS transistor.</br>

When Vin = 0, a direct path is created between the power supply (Vdd) and the output (Vout). This allows the capacitor (CL) to charge through the PMOS transistor.</br>

**Naming the Currents**</br>

We need to name the currents flowing through the transistors:</br>

The current flowing through the NMOS (from Drain to Source) is called Idsn.</br>

The current flowing through the PMOS (from Drain to Source) is called Idsp.</br>

These two currents are always equal in magnitude but flow in opposite directions. This relationship is written as: **Idsp = -Idsn**.</br>

### L3 PMOS/NMOS drain current vs drain voltage

If we were to draw the curves for these currents, we would have:</br>

A graph showing how Idsn changes with Vdsn (the voltage across the NMOS).</br>

A graph showing how Idsp changes with Vdsp (the voltage across the PMOS).</br>

### L4 Step1- Convert PMOS gate-source-voltage to Vin
We have seen various internal voltages, but actually in terms of user's perspective we can't see the internal voltages and only see the external Vin and Vout. From these we calculate the VTC and eventually we get to know the delay.</br>

**Now we will see the steps to obtain Voltage Transfer Characteristics(VTC) for static CMOS inverter:**
*Assumption: Let us assume that it is a long channel device with Vdd=2V*
* We will fix the Vgs values as shown below
 
* We know that Vgsp= Vin-Vdd, So we get the above values.So we get **Vin = Vgsp+Vdd**, we are trying to convert all the voltages as function of Vin and Vout.
* We will try to plot the graph of PMOS in terms of Idsn, the plot will be as shown below.

  
### L5 Step2 & Step3- Convert PMOS and NMOS drain-source-voltage to Vout
Now we be converting the Vdsp and function of output voltage Vin. We know **Vdsp = Vout-Vdd**.</br>
Let us convert Vdsp into Vout. So to get Vout there is a shift of Vdd towards left hand side.</br>


We can see that whenever Vout=2V that means Vdsp=0V and Vdd=2V (given), then The current is zero and capacitor at the output is discharged. This is true only when PMOS is in combination with NMOS and forms a CMOS inverter.</br>
Let us take another example, when Vout=0V, that means -Vdsp=2V and Vdd=2V, so at every gate voltage of Vin we will see a finite current whenever Vout=0V. As Vout=0V, the capacitor is completely discharged and we need to charge that, so that is the charging current required. So, here we get the load curve for PMOS</br>

![WhatsApp Image 2026-02-27 at 3 26 42 PM](https://github.com/user-attachments/assets/f4d7727c-9650-4cc2-b503-5f78dd314d4c)

Now we will try to get the "load curve" for NMOS transistor from this equations.</br>

It is actually simple as Vgsn = Vin and Vdsn = Vout, directly we can get the graphs.</br>


### L6 Step4- Merge PMOS-NMOS load curves and plot VTC
We will now merge the above two curves and obtain the voltage transfer characteristics(VTC) for CMOS inverter.

For this we will superimpose both the Load Curves to get the VTC. We are doing this to find out the common point between Vin and Vout of both NMOS and PMOS.</br>

![WhatsApp Image 2026-02-27 at 3 27 22 PM](https://github.com/user-attachments/assets/9e25efcf-8287-468a-9956-e3d3dc7a53d9)

So the  range of Vin and Vout is 0V-2V.</br>

* When Vin = 0V: The output Vout is 2V. In this state, the NMOS is Cut Off, and the PMOS is in its Linear region.
* When Vin = 0.5V: The output Vout falls between 1.5V and 2V. Here, the NMOS is in the Saturation region, and the PMOS is still in the Linear region.
* When Vin = 1V: The output Vout is between 0.5V and 1.5V. In this mid-range, both the NMOS and PMOS are in the Saturation region.
* When Vin = 1.5V: The output Vout is between 0V and 0.5V. Here, the NMOS enters the Linear region, while the PMOS is in the Saturation region.
* When Vin = 2V: The output Vout is 0V. In this final state, the NMOS is in the Linear region, and the PMOS is Cut Off.

# Day3-CMOS switching threshold and dynamic simulations

## Voltage transfer characteristics-SPICE simulations

### L1 SPICE deck creation for CMOS inverter
**Simulating VTC – Creating SPICE Deck:**

- SPICE deck = Netlist = tells how components are connected</br>
- Circuit has:</br>
  - M1 = PMOS</br>
  - M2 = NMOS</br>
- Include substrate connections in netlist</br>

<img width="546" height="501" alt="image" src="https://github.com/user-attachments/assets/87648d3d-9f23-4e6a-b66a-872306e570f1" />

Next we will write down the **Component Vlaues**, keeping W/L for both NMOS and PMOS same.</br>

<img width="622" height="487" alt="image" src="https://github.com/user-attachments/assets/01bb49d8-39b6-40e1-850f-6a6a95dc5946" />

Next we will assume the **Vin and Vout values**

<img width="585" height="482" alt="image" src="https://github.com/user-attachments/assets/38af526d-c53a-4ff7-91c5-bd804fd572da" />

Next step is to **Identify the Nodes** (Node is the point where two components meet)

<img width="766" height="532" alt="image" src="https://github.com/user-attachments/assets/e7a2d759-0ff9-4c2c-939e-ac4af8840cae" />

**Name the nodes** In model file we will mention like, 2.5V input lies between Vin and 0, similarly Vdd lies between vdd and 0.

<img width="592" height="482" alt="image" src="https://github.com/user-attachments/assets/683acee0-3468-498a-9f94-c804122c5a4b" />

Now let us write the SPICE deck:

<img width="1227" height="585" alt="image" src="https://github.com/user-attachments/assets/1b54b47c-edea-4a16-ac0d-fe40405cd393" />
We know for Mosfet the syntax is DGSS(Drain gate source and substrate).

### L2 SPICE simulation for CMOS inverter
<img width="1197" height="582" alt="image" src="https://github.com/user-attachments/assets/6d58c77a-50fe-4eab-9891-287d7a98ae44" />
<img width="1192" height="553" alt="image" src="https://github.com/user-attachments/assets/a06f6d8e-c074-4aa9-9946-6056ed71f927" />
<img width="1280" height="592" alt="image" src="https://github.com/user-attachments/assets/f4e7acd7-6158-432b-8003-b2c74656f9b0" />

**Simulation Steps:**

1. **Simulation Command:** Sweep Vin 0 to 2.5V (step 0.05V) → measure Vout → get VTC</br>
2. **Model Files:** Include technology files (contains all transistor parameters)</br>
<img width="1223" height="565" alt="image" src="https://github.com/user-attachments/assets/1bd6f151-618b-4612-82fd-6b43f7eec459" />

Now we will do the SPICE simulation for Wn=Wp=0.375u, Ln=Lp=0.25u, Wn/ln=Wp/Lp=1.5. Below is the VTC we get for the above netlist.</br>

<img width="743" height="567" alt="image" src="https://github.com/user-attachments/assets/91c4ab55-57f1-45ab-826b-b9a9631647ee" />

Next we will get the VTC for Wn= 0.375u, Wp= 0.9375u, Ln,p=0.25u; Wn/Ln=1.5, Wp/Lp=2.5  (PMOS width is 2.5 times more than NMOS)

<img width="741" height="572" alt="image" src="https://github.com/user-attachments/assets/5d83f191-3962-4e25-99b3-aa5d3f520d92" />

If we observe the previous graph is left shifted slightly. This happens because NMOS is more stronger than PMOS in previous graph.</br>

### L3 Labs Sky130 SPICE simulation for CMOS
We now get the VTC characteristics

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/3e6c8b58-05e8-4c43-94a8-e1f8323a9e00" />
We are using both pfet and nfet for CMOS inverter. We can see that W/L ratio of pmos is 2.33 times greater than that of nmos. And we will be sweeping Vin from 0 to 1.8V with step isze of 0.01V and plotting the Vout.</br>

<img width="1913" height="1078" alt="image" src="https://github.com/user-attachments/assets/a9aa02e7-a3f0-4485-9b07-129fd8260d03" />
To get the plot type `ngspice` and `plot out vs in`.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/2b2cd0ab-86fa-43cb-aae5-6192e7c52c10" />

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/e71074c8-50af-44c1-9316-790007b9394e" />

Now we need to know the Switching Threshold from this graph, it is the point when Vin=Vout.</br>
To zoom in the curve; press righ mouse button + hold it.</br>

<img width="1918" height="1076" alt="image" src="https://github.com/user-attachments/assets/f23c8b99-6ef4-49e3-860b-2e0c324f4320" />
So switching threshold for W/L=2.3 is around 0.876V</br>

<img width="280" height="30" alt="image" src="https://github.com/user-attachments/assets/816fa465-de21-4d8d-bff4-fb79ab059723" />

We will now see the transient analysis:</br>
For that we will go inside the tansient SPICE file for day3</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/fe3e84fa-8511-4f02-917e-570de93216d9" />
We can see that it is for typical corner as before and the W/L is also same. But now we taking transient pulse from 0v to 1V with shift of 0 with rise time and fall time being 0.1ns and 0.1ns respectively, pulse width of 2ns and total time period of 4ns. Let us run this.</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/93a365ad-7eff-4172-921b-d0301c2978f7" />
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/786bea0f-e506-4475-b099-575545bd0685" />

So for rise delay and fall delay, we need to consider 50% of output curve i.e. at 0.9V; out-in.</br>
<img width="305" height="67" alt="image" src="https://github.com/user-attachments/assets/9e8f888e-74a1-465c-8cb5-71ee3302b0f7" />

Therefore **Rise delay = 2.482ns-2.15ns = 0.333ns**

For fall delay, consider while falling.</br>

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/4c675f5c-cef5-4f78-8692-67398bbf94eb" />
<img width="315" height="71" alt="image" src="https://github.com/user-attachments/assets/73197af2-d7b5-4545-a2b6-aebde88f7f20" />
Therefore **Fall Delay = 4.334ns-4.050ns = 0.285ns**

## Static behaviour evaluation-CMOS inverter robustness-Switching Threshold

### L1 Switching Threshold, Vm
Let us compare the two different CMOS inverters with different W/L ratios of PMOS and NMOS, we can see that the shape of the VTC is same in both the cases only the switching threshold is different. This shows the robustnesss of CMOS inverter.</br>

<img width="1243" height="578" alt="image" src="https://github.com/user-attachments/assets/c246dc3c-6686-4d8f-b8a5-74136a9323de" />
Let us find out the Switching threshold, Vm in both the cases by drawing a 45 degree line.</br>

So, in first case Vm comes out to be somewhere around 0.9V and in second case Vm=1.2V.</br>
<img width="1168" height="417" alt="image" src="https://github.com/user-attachments/assets/7b300b9a-c5ee-4a11-ab44-6bc6027f8b63" />

This is the area where PMOS and NMOS both are in saturation region. Current flows from both the transistor, it is actually a dangerous situation.

<img width="1083" height="462" alt="image" src="https://github.com/user-attachments/assets/5b52f85c-c43e-4b4f-b38f-e51e8fe28170" />

### L2 Analytical expression of Vm as a function of (W/L)n and (W/L)p
We will now calculate the value of Vm w.r.t the NMOS and PMOS width and length. </br>
<img width="553" height="367" alt="image" src="https://github.com/user-attachments/assets/6c11d77c-26a3-46e5-bf6c-349740e6eb00" />
<img width="860" height="53" alt="image" src="https://github.com/user-attachments/assets/b8533cc5-176d-4cb7-97c3-7d6ad5f4ec88" />
<img width="557" height="148" alt="image" src="https://github.com/user-attachments/assets/aacac08b-2543-4f88-8ddb-ce58cad2b763" />

### L3 Analytical expression of (W/L)n and (W/L)p as a function of Vm
Now here we will calculate the value of W/L for PMOS and NMOS when Vm is given.</br>
We have to move in reverse fashion, as we need to calculate W/L ratio of PMOS and NMOS such that Switching threshold is exatly half of the power supply Vdd = 2.5V, therefore required Vm = 1.25V.</br>
We will start from the current equation itself i.e. **Idsn = -Idsp**

<img width="962" height="362" alt="image" src="https://github.com/user-attachments/assets/4abd767b-176b-42c2-9e2e-bdf52323fed2" />
Expanding Kp and Kn (Gain factor) </br>
<img width="517" height="92" alt="image" src="https://github.com/user-attachments/assets/950f6372-d1d7-4c18-8cfd-5b1f35cdfce5" />
<img width="517" height="92" alt="image" src="https://github.com/user-attachments/assets/a532b030-2296-4ff8-981d-2ab29cd88dea" />

**Finding W/L ratios from Vm:**

- RHS has constants (from model files) and Vm</br>
- If we know Vm → we can find W/L ratios</br>
- This tells us when PMOS W/L > NMOS W/L</br>

Now we will see CMOS behavior for different W/L ratios.</br>

<img width="301" height="233" alt="image" src="https://github.com/user-attachments/assets/8534791b-2793-4986-bdad-4a2ef6bde1fe" />

### L4 Static and Dynamic simulation of CMOS inverter
* For (W/L)n = (W/L)p = 1.5</br>
  <img width="750" height="567" alt="image" src="https://github.com/user-attachments/assets/1c8f3e81-2023-429d-9a9e-b80e35d3ad09" />

  We can also calculate the "Rise Delay" and "Fall Delay" by using the transient analysis, just like we did earlier.</br>
  <img width="1256" height="512" alt="image" src="https://github.com/user-attachments/assets/836bb013-63a3-44aa-b0d5-d640359c35f7" />

### L5 Static and Dynamic simulation of CMOS inverter with increased PMOS width
We will be doing the SPICE simulations for increased width of PMOS transistors and compare the results.</br>
* (W/L)p = 2(W/L)n</br>
  <img width="1181" height="507" alt="image" src="https://github.com/user-attachments/assets/7333b09a-2e41-40b2-881e-373214b16c5b" />

We can see that the Vm is now increased as the PMOS has become more stronger and it needs more current to charge the output load capacitor.</br>
* (W/L)p = 3(W/L)n</br>
  <img width="1197" height="507" alt="image" src="https://github.com/user-attachments/assets/f3bea4a2-8853-4330-8886-86e6ab224069" />

<img width="1241" height="512" alt="image" src="https://github.com/user-attachments/assets/abf77cdf-93df-45b2-8373-b9d526a1c8e6" />
<img width="1207" height="512" alt="image" src="https://github.com/user-attachments/assets/978a4960-3442-4ba5-bd1b-e8f336f8812a" />

*Note: Rise delay decreases with increase in PMOS width, this shows the time required to charge the output capacitor decreases significantly this is because we have a bigger area.* </br>

### L6 Applications of CMOS inverter in clock network and STA
The final data set we got from above experiment is shown below:

<img width="692" height="236" alt="image" src="https://github.com/user-attachments/assets/0359ac26-996d-423d-bd27-99e08b6dddaa" />

**Experiment Conclusions:**

1. **Robustness:** Even if transistor sizes vary during fabrication, Vm does not change much → CMOS is robust.</br>
2. **Symmetry:** When (W/L)p = 2 × (W/L)n, rise delay ≈ fall delay. This shows CMOS inverter symmetry.</br>
  *This is a typical characteristic of Clock Inverter/buffer where we want the rise delay and fall delay to be equal.* </br>
  
  <img width="1110" height="653" alt="image" src="https://github.com/user-attachments/assets/30d33241-5e2f-4389-9a80-cd8d2ad5baaf" />
* Other types of cells can be used according to the data path requirement

# Day4-CMOS Noise Margin robustness evaluation

## Static behaviour evaluation-CMOS inverter robustness-Noise Margin

### L1 Introduction to Noise Margin</br>
We now examine the CMOS inverter's robustness through the lens of **Noise Margin**—a key metric for assessing noise immunity.</br>

**Noise Margin** quantifies the maximum tolerable input voltage deviation that a logic gate can withstand while still maintaining correct output logic levels. It essentially measures the circuit's resilience against electrical disturbances.</br>

For example if we consider an ideal Inverter, for inputs 0/1 it gives output as 1/0. The slope of switch is infinite. </br>

<img width="557" height="451" alt="image" src="https://github.com/user-attachments/assets/2465a4e2-199d-4698-aa7d-58f0b42f0c6f" />

But practically the slope won't be infinite, due to presence of resistances and capacitances there will be delay. Therefore we will get a finite slope </br>

<img width="368" height="316" alt="image" src="https://github.com/user-attachments/assets/f8f2f3f3-dc21-45eb-90b7-c9f2fdb8ef94" />

We can observe the following from the VTC curve:</br>

- When the input voltage is between **0 and VIL** (input low voltage), the output stays at **VOH** (output high voltage).</br>
- When the input voltage is between **VIH** (input high voltage) and **Vdd**, the output stays at **VOL** (output low voltage).</br>
<img width="405" height="342" alt="image" src="https://github.com/user-attachments/assets/8e3c22bf-b012-4a75-a08d-910511ed2980" />

### L2 Noise Margin voltage paramters</br>
**Practical inverter VTC (with non-idealities):**</br>

- 0 < Vin < VIL   →   VOH < Vout < Vdd</br>
- VOL < Vin < Vdd →   0 < Vout < VOL</br>

**Relationships:**</br>
- VOL < VOH < Vdd</br>
- 0 < VOL < VIL</br>

Slope ≈ -1 in transition region (output drops as input rises) </br>

<img width="356" height="337" alt="image" src="https://github.com/user-attachments/assets/d848d4c0-de9b-4b6b-8c6a-f3006bae557c" />

### L3 Noise margin equation and summary
Now we will calculate the noise margin equation, for that we will plot the voltages on the same scale.</br>

<img width="733" height="443" alt="image" src="https://github.com/user-attachments/assets/c25a3266-d8f3-4e16-8afa-298756b3a59d" />
In the above scale: </br>
* **Noise amrgin High NH** - value between VIH and VOH. </br>
* **Noise Margin Low NL** - value between VIL and VOL. </br>

So, any value which lies in between noise margins is considered either 1/0 and considered to be tolerable. Apart from this region the value is "Undefined" and the logic level can swing between 'high' and 'low'.

<img width="783" height="423" alt="image" src="https://github.com/user-attachments/assets/80791538-0e36-46a8-9bf1-043e740dd778" />

<img width="822" height="481" alt="image" src="https://github.com/user-attachments/assets/6443e129-644a-4d0d-a4c4-0439ba4165de" />

### L4 Noise margin variation with respect to PMOS width
**Finding Noise Margins:**</br>

1. Find points where slope = -1 on VTC curve</br>
2. Extend lines to x-axis and y-axis</br>
3. Get VIL, VIH, VOL, VOH from these points</br>
4. Calculate noise margins = VOH - VIH and VIL - VOL</br>

We will do this for different PMOS widths to prove CMOS robustness.</br>

<img width="1207" height="542" alt="image" src="https://github.com/user-attachments/assets/5ab8cb26-4ab7-4e77-9a04-be82cfcdac12" />
The larger the Noise margin, stronger is CMOS inverter and immune to Noises.</br>

<img width="1175" height="523" alt="image" src="https://github.com/user-attachments/assets/98daed0b-5528-4d72-8a99-06806511d1b8" />
<img width="1197" height="503" alt="image" src="https://github.com/user-attachments/assets/89b5f850-df64-4e6e-abcb-366cc3755d13" />
<img width="1203" height="517" alt="image" src="https://github.com/user-attachments/assets/13199ec4-704c-4812-aba2-38257330e40b" />

For (W/L)p=4(W/L)p and (W/L)p=5(W/L)p noise margins are same, so even if we increase the widths further noise margin will be static. 

<img width="677" height="226" alt="image" src="https://github.com/user-attachments/assets/fca7bcac-471c-4114-8c64-4b97cba1f5b0" />

Here also we can verify the robustness of CMOS inverter. </br>

Also we come to know the ranges for "Digital design" and "Analog design" in the CMOS inverter.</br>

<img width="741" height="546" alt="image" src="https://github.com/user-attachments/assets/3e9a0cf6-a232-4ff2-ad4c-214b03803af3" />
<img width="772" height="542" alt="image" src="https://github.com/user-attachments/assets/56c5c94d-b59f-456c-ba92-b22fab03b6d9" />

### L5 Sky130 Noise margin labs
We will now plot Noise margins

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/af440785-3266-41ad-97ed-dd819824aaa5" />
<img width="1918" height="1077" alt="image" src="https://github.com/user-attachments/assets/58aba228-174c-453c-90df-e81aeab49d53" />

We are taking the W/L ratios of PMOS to NMOS as 2.77 and sweeping the Vin from 0 to 1.8V with stepsize of 0.01V.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/7e8e9139-43f7-4aa7-9737-9e7e378d443b" />
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/bc470f7d-f493-47c5-89e9-dfbad4e053bb" />
<img width="278" height="60" alt="image" src="https://github.com/user-attachments/assets/501565f8-b944-4af8-854b-a9f1eded062b" />

We will take the point where the slope is -1 ; x axis will give VIL and VIH, whereas y axis will give VOH and VOL.

**Noise margin NH = VOH - VIH = 1.70952-0.98778 = 0.72** </br>
**Noise margin NL = VIL - VOL = 0.7733-0.09523 = 0.67807** </br>

# Day5-CMOS power supply and device variation robustness evaluation

## Static behaviour evaluation-CMOS inverter robustness-Power supply variation

### L1 Smart SPICE simulations for power supply variations
**Power Supply Scaling** is another factor in CMOS robustness.</br>

- Smaller gate length → Lower operating power</br>
- Even with power scaling, CMOS characteristics should stay the same</br>

We will check by simulation, taking two cases.

<img width="1172" height="328" alt="image" src="https://github.com/user-attachments/assets/03dcd0b9-4dd3-4762-83b2-9cbb882e7bc3" />
<img width="723" height="442" alt="image" src="https://github.com/user-attachments/assets/e403056b-c4bb-4b18-a67c-baf5b02842ab" />
<img width="717" height="436" alt="image" src="https://github.com/user-attachments/assets/f357c6d2-fa02-43bc-bf51-184494cf8858" />
<img width="421" height="171" alt="image" src="https://github.com/user-attachments/assets/25f4e021-6818-4e30-85d9-cf300b35bd03" />

We will now plot the VTC charactersitics for Vdd= 2.5V, 2V, 1.5V, 1V, 0.5V;

<img width="742" height="568" alt="image" src="https://github.com/user-attachments/assets/87cf496c-6386-4374-9e92-1a6ef71959c1" />

### L2 Advantages and disadvantages using low supply voltage</br>
**Analyzing simulation results for different Vdd values:** </br>

First, we check the **gain** for each supply voltage.</br>

Gain = ΔVout / ΔVin  (how much output changes for a given input change)</br>

This tells us how sharp the switching transition is.
<img width="968" height="516" alt="image" src="https://github.com/user-attachments/assets/dd11da87-d570-4fe1-9439-bd449e39af6a" />

<img width="976" height="547" alt="image" src="https://github.com/user-attachments/assets/102b9c1b-82ce-4d72-bc7e-fb502591c636" />

There is energy lowering for low supply voltage.

<img width="1000" height="526" alt="image" src="https://github.com/user-attachments/assets/f9a05a5f-40c0-4bad-be1f-3cd16f1445f4" />
<img width="927" height="527" alt="image" src="https://github.com/user-attachments/assets/b96be82f-5993-4fd1-9cc2-c0756dc212df" />

* Advantages of low supply voltage
  
<img width="722" height="212" alt="image" src="https://github.com/user-attachments/assets/ab3ef568-d3f7-44cb-a6c5-6524ba5b72ec" />

* **Disadvantages of using low supply voltage:**

- **Slower switching**: The load capacitor takes more time to charge and discharge
- **Increased delays**: Both rise delay and fall delay become larger
- **Performance impact**: The circuit operates at a lower maximum frequency
### L3 Sky130 Supply variation Labs
We will calculate the supply variation.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/94a3c1ba-3139-4838-b302-2320ce3f643e" />
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/56419121-44bb-4f73-9084-06b1503b6544" />

The initial supply voltage is 1.8V and we are reducing it with the step of 0.2V, so there will be 6 iterations.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/af291d32-1484-4d6b-8291-dabc5b70df65" />
We will calculte the Gain: </br>

* **Vdd=1.8V** </br>

  <img width="292" height="61" alt="image" src="https://github.com/user-attachments/assets/0f2c56cc-5fb4-4c1e-9e49-0e7ee75b964b" />

  |Gain| = 7.6229 </br>

* **Vdd=0.8V**

  <img width="267" height="52" alt="image" src="https://github.com/user-attachments/assets/112695f4-b69a-4c76-bd41-a066a08ac6b7" />

  |Gain| = 9.3844 </br>

## Static behaviour evaluation-CMOS inverter robustness-Device variation
We will see the sources of variation of VTC characteristics in a CMOS inverter.</br>
### L1 Sources of variation - Etching process

First is **Etching Process** </br>
If we see a single inverter layout, we will see the length of gate, the width(common area between polysilicon and diffusion). Due to etching process there can be a variation in length and width of CMOS.
![WhatsApp Image 2026-02-27 at 9 26 54 PM](https://github.com/user-attachments/assets/42d2820f-1050-420d-814b-f63919b53617)
<img width="1144" height="518" alt="image" src="https://github.com/user-attachments/assets/d4f6117d-80b2-4f5b-9b80-0874e7f5332e" />

Now considering the inverter chain, the variation can differ with different inverter.

<img width="1288" height="652" alt="Screenshot 2025-10-03 203314" src="https://github.com/user-attachments/assets/a326d12c-e0b7-4daa-bf13-311ccaa8e476" />
<img width="1121" height="618" alt="Screenshot 2025-10-03 203404" src="https://github.com/user-attachments/assets/8683fe6c-a634-4720-98d4-8ef619ab52b1" />

The variation is more at the edges or sides than at the center.

<img width="1324" height="621" alt="Screenshot 2025-10-03 203542" src="https://github.com/user-attachments/assets/998d8d7c-941f-4643-a768-13896c578018" />

Therefore the variation in L and W can change the drain current of CMOS inverter.

<img width="926" height="483" alt="Screenshot 2025-10-03 203633" src="https://github.com/user-attachments/assets/b1c7130a-de89-4cf1-ab2e-064702878082" />

### L2 Sources of variation - Oxide thickness
Let us consider the cross-sectional view of CMOS inverter. We will see the oxide under polysilicon gate, while fabricating the thickness can vary.</br>

<img width="1318" height="561" alt="Screenshot 2025-10-03 203747" src="https://github.com/user-attachments/assets/25b705ca-1d73-4127-a9bc-a69e2af0c8c2" />
<img width="826" height="377" alt="Screenshot 2025-10-03 203848" src="https://github.com/user-attachments/assets/df455509-4718-4074-9eda-bb314e6462c0" />

There is a difference between ideal thickness and actual thickness.

<img width="1205" height="597" alt="Screenshot 2025-10-03 203924" src="https://github.com/user-attachments/assets/a802cce3-df91-4e80-9b34-d2f931de9f8d" />

We know **Cox=Eox/tox**, therefore change in tox can actually change the drain current.

<img width="1162" height="461" alt="Screenshot 2025-10-03 204044" src="https://github.com/user-attachments/assets/d06ee6da-3467-41cb-8a0e-280b15faae56" />

### L3 Smart SPICE simulation for device variations
To prove the CMOS inverter's robustness, we will simulate two extreme cases using SPICE:

- **Strong PMOS + Weak NMOS**: PMOS width is larger → lower resistance → stronger PMOS
- **Strong NMOS + Weak PMOS**: NMOS width is larger → lower resistance → stronger NMOS

The inverter's performance under these conditions will demonstrate its reliability.</br>

<img width="1148" height="339" alt="Screenshot 2025-10-03 224857" src="https://github.com/user-attachments/assets/398d01a6-ffc4-4a10-86a8-3907d3214b69" />
<img width="594" height="436" alt="Screenshot 2025-10-03 224935" src="https://github.com/user-attachments/assets/41b1f2f6-c4ba-4c71-a8e6-d1fc8e3b4844" />
<img width="695" height="398" alt="Screenshot 2025-10-03 224949" src="https://github.com/user-attachments/assets/9314e15f-c027-47ba-b34e-f35d886e5aff" />
<img width="895" height="694" alt="image" src="https://github.com/user-attachments/assets/73b6f593-69c9-4e9f-82ff-a56e4c25e6d0" />
<img width="753" height="567" alt="Screenshot 2025-10-03 225153" src="https://github.com/user-attachments/assets/33e8fc0e-5220-4dc4-8da9-4c8dd5406e02" />

### L4 Conclusion from the characteristics we got
<img width="994" height="537" alt="Screenshot 2025-10-03 231012" src="https://github.com/user-attachments/assets/aec473f9-00f5-4028-b122-fa2922affcb3" />

* The switching threshold **Vm** shifts to the right when the PMOS is stronger, and to the left when the NMOS is stronger. </br>

<img width="1095" height="661" alt="image" src="https://github.com/user-attachments/assets/7acdec95-de39-4389-937d-1a80e83ac83f" />
* The noise margins show very little change in both extreme cases, confirming that the inverter remains robust regardless of process variations.</br>
### L5 Sky130 device variations labs
We will now do the SPICE simulations for the device variations</br>
We can see that the width of PMOS is quite large than that of NMOS. SO it is clearly strong PMOS and weak NMOS case. The Vm will be right shifted.</br>
<img width="1126" height="594" alt="image" src="https://github.com/user-attachments/assets/3bd621fa-c18f-4fe8-aec9-327735420b9a" />

