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

## 2.1.1. SR Flip-Flop

https://github.com/user-attachments/assets/86e1f68a-fd2f-41cc-a166-d44627811afe

https://www.falstad.com/s.php?s=SQUtda

The Clock high signal represents the sampling time of the Flip-Flops. The input signal can be unstable within this period making the output unstable. This can be solved in two different ways:

### 1. Master-Slave Flip-Flops

Instead of one, Flip-Flop, two Flip-Flops are used in series. The first Flip-Flop samples the unstable input. At the low edge the stored bit in the first flip-flop  which is stable is passed to the second flip-flop.

### 2. Edge Triggered Flip-Flops

The sampling time can be reduced by passing the clock signal through a pulse generator. However, the pulse width should be long enough to capture the value and short enough to prevent timing issues.

https://github.com/user-attachments/assets/27da4022-5b01-4160-bf89-c4d9a30ff188

The pulse width above is 3*t_pd of the not gate. The pulse width should be above slightly above t_pd for the value to be registered by the flip-flop. Depending on the timing analysis the minimum number of Not gates can be decided.

## 2.1.2. Master-Slave SR Flip-Flop

https://github.com/user-attachments/assets/9321cc9a-a78c-48f7-87a9-2ed72123be17

https://www.falstad.com/s.php?s=zO7eXA

## 2.1.3. Edge Triggered SR Flip-Flop

https://github.com/user-attachments/assets/9059467e-d2d5-433d-aa85-2178b405d591

https://www.falstad.com/s.php?s=I6KpDq

Pulse generators will be used for Flip-Flops designed  below.

## 2.2 D Flip-Flop

https://github.com/user-attachments/assets/40400947-9c1d-4ba0-9e52-323359881053

https://www.falstad.com/s.php?s=tbtAUE

## 2.3. JK Flip-Flop

The State of the output is unknown when both Set and Reset are high simultaneously. With some modifications in SR Flip-Flop, this unused state can be used, to toggle between High and Low.


