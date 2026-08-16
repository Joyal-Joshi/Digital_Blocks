

Transistors are the building block upon which the entire digital electronics is build on. There are two types of transistors: BJT and MOSFET. BJT stands for Bipolar Junction transistors and MOSFET stands for Metal-Oxide Semiconductor Field Effect Transistor. MOSFET are preferred over BJT to make digital electronics, as they don't need any gate current to operate. 

## MAKING OF MOSFET

   

## MOSFET CLASSIFICATION

Based on how they work the MOSFET can be classified into two types: enhancement type and depletion type. In enhancement type the channel is formed when the gate voltage is applied and in depletion type the channel is removed when the gate voltage is applied.
The enhancement type MOSFET is preferred due to safety as they act as open switch when turned off.

Based on the charge carriers they can be further classified as NPN or PNP. In NPN the electrons are the charge carriers and PNP the positive charge or the absence of electrons are the charge carriers.


## WORKING OF MOSFET

<img width="327" height="107" alt="image" src="https://github.com/user-attachments/assets/966a9f46-8304-4ba6-bb99-04828cc12a92" />

NPN : When positive gate voltage wrt the source(Vgs) is above the threshold voltage(VTh), the channel is formed and the current flows from drain to source.

PNP: When the magnitude of the negative gate voltage wrt the source(Vgs) is above the threshold voltage(Vth), the channel is formed and the current flows from drain to source. Instead of providing a negative voltage to the gate wrt the source, a positive voltage of the same magnitude can be applied to source wrt the gate , to create the same behavior. So, the source is connected to the voltage supply and when the gate voltage is high, the Vgs is zero, closing the gate and and when the gate volt is low, the Vgs becomes negative opening the gate.

The NPN is inherently a bad pull-up transistor and PNP is a bad pull-down transistor. Assume the NPN was On and connected as pull-up transistor. The MOSFET will shut-off prematurely before the source reaches the drain pull-up voltage due the Vgs dropping below Vth as the source voltage reaches the drain voltage. Similar problem occurs when PNP is connected as pull-down. Hence, both PNP and NPN are used together to complement each other and build digital circuits. Hence the name CMOS (Complementary MOSfet).


Vgs vs Ids

<img width="193" height="169" alt="image" src="https://github.com/user-attachments/assets/19c82331-3240-4473-ad6d-c51583467528" />

There is no current when the Vgs is below threshold voltage. Above threshold voltage the curve can be modeled as a parabolic curve using the equation below: Ids = K(Vgs-Vth)^2

Ids vs Vds

<img width="332" height="295" alt="image" src="https://github.com/user-attachments/assets/5ded2465-2290-45c6-9280-6b66fd595551" />

The graph can be divided into two regions. the Ohmic region where the current increases wrt voltage and the Saturation region where the current is steady wrt voltage.
Also, there is no current if the Vgs is below the threshold voltage.

