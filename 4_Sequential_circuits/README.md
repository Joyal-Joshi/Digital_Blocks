Building Sequential circuits using the derived Logic Gates:

# 1. Latch

## 1.1. S-R Latch

Consider, an OR Gate where the output is fed back to one of its inputs. The value given to the other input will be trapped/latched or stored forever. This method can be used to store bits.

https://github.com/user-attachments/assets/09b7898e-9d82-4f0e-a9dc-186c34b8f7cd

The circuit above can be modified to reset the stored bit, without switching off the entire circuit as shown below.

https://github.com/user-attachments/assets/d18be2eb-aa83-43ee-a5de-3d2073833b2b

Converting all the gates to NAND gate will be give the classic S-R latch.

https://github.com/user-attachments/assets/c79c1ba6-3e9d-410d-9057-2a9f94e0057b

https://www.falstad.com/s.php?s=7v1qmD

## 1.2. Gated D Latch

The SR latch can be modified, to store a bit of data when the Enable bit is on.

https://github.com/user-attachments/assets/aa708f5f-fbe8-4a15-a275-a15d309323a4

https://www.falstad.com/s.php?s=JVLr6v

# 2. Flip-Flops

The latches can be modified to be synchronous with the clock signal. The Flip-Flop only changes when the clock signal is high.

## 2.1. SR Flip-Flop

https://github.com/user-attachments/assets/86e1f68a-fd2f-41cc-a166-d44627811afe

https://www.falstad.com/s.php?s=SQUtda

The Clock high signal represents the sampling time of the Flip-Flops. The input signal can be unstable within this period making the output unstable. This can be solved in two different ways:

### 1. Master-Slave Flip-Flops

Instead of one, Flip-Flop, two Flip-Flops are used in series. The first Flip-Flop samples the unstable input. At the low edge the stored bit in the first flip-flop  which is stable is passed to the second flip-flop.

### 2. Edge Triggered Flip-Flops

The sampling time can be reduced by passing the clock signal through a pulse generator. However, the pulse width should be long enough to capture the value and short enough to prevent timing issues.

https://github.com/user-attachments/assets/afbc88eb-24e3-42b1-806d-1623738ab27b

The pulse width above is t_pd_not + t_pd_and. The pulse width should be above slightly above t_pd for the value to be registered by the flip-flop. Depending on the timing analysis the minimum pulse width can be calculated.

## 2.1.1. Master-Slave SR Flip-Flop

https://github.com/user-attachments/assets/73a8135e-2796-4f8b-9b4a-e7620084a220

https://www.falstad.com/s.php?s=J6LVAO

## 2.1.2. Edge Triggered SR Flip-Flop

https://github.com/user-attachments/assets/9059467e-d2d5-433d-aa85-2178b405d591

https://www.falstad.com/s.php?s=I6KpDq

Master-Slave approach is considered to be better for unstable inputs and easier to design. Hence, it will be used for the Flip-Flops below.

## 2.2 D Flip-Flop

https://github.com/user-attachments/assets/8336c5e8-72f2-475a-9cea-fcdbed02e632

https://www.falstad.com/s.php?s=CO7JrL

## 2.2.1 D Flip-FLop with PR & CLR

The D flip-Flops will be used primarily to make Registers. Then the Preset and Clear signals can be used to reliably control the starting state of the registers. Note that, PR and CLR change the outputs asynchronously. PR and CLR can be added to any type of Flip-Flop.

https://github.com/user-attachments/assets/495bd5a7-934e-4133-8b59-cd847ad70353

https://www.falstad.com/s.php?s=GgHNZP

## 2.3. JK Flip-Flop

The State of the output is unknown when both Set and Reset are high simultaneously. With some modifications in SR Flip-Flop, this unused state can be used, to toggle between High and Low.

The pulse width should be smaller than the time to loop around in JK Flip-Flops to prevent racing. It is better to use Master-Slave Flip-Flops to avoid racing conditions.

https://github.com/user-attachments/assets/8159ef24-1674-450f-9b04-6c3dee768bcf

https://www.falstad.com/s.php?s=CL3UQQ

## 2.4. T Flip-Flop

Instead of two separate inputs to set and reset, one common Toggle bit can be used to either switch on or off the toggle.

Similar to JK Flip-Flops, Master-Slave Flip-Flops are used to prevent racing.

https://github.com/user-attachments/assets/6e10239a-0096-49c0-bc8f-798a3cd712f3

https://www.falstad.com/s.php?s=o0bz1G

# 3. Registers

## 3.1 Register (8 bit)

Flip-Flops can be used in parallel to form the Registers. Registers are used to store multiple bits.

https://github.com/user-attachments/assets/69c3b378-0bb5-49f6-8e97-4e149542fb26

https://www.falstad.com/s.php?s=WeEuRZ

## 3.2 Shift Registers (8 bit)

Shift Registers are used to convert a serial input (1 bit) to parallel output (8 bit). The D flips-flops used to make the registers are cascaded to form the shift registers.

https://github.com/user-attachments/assets/0a923ebb-018a-4b9f-910e-8a9429b5c156

https://www.falstad.com/s.php?s=8uEDqH

## 3.3 Counters (4 bit)

Counters are also special registers that can be used to count or load bits. Counters can be made in two ways:

### 3.3.1. Ripple/Async Counters

JK Flip-Flops can cascaded to make the Ripple Counter, due to which every counter down the line toggles at half the frequency, leading to counting in binary. Ripple counters are not good for loading as the flip-flops are asynchronous.
These Flip-Flops can be used to Count up or Count down as required by using the Q and Q' outputs.

### 3.3.2. Sync Counters

In this counter all the flip-flops have the same clock signal. These counters can be used to count and load data, making them more versatile. The outputs from the previous two JK Flip-Flops are passed through an AND gate and fed to the input of the next Flip-Flop to make the counter. Additional circuitry is needed to switch between loading and counting bits. Similar to Ripple Counters Q and Q' outputs can be used to generate counting up or down outputs.







