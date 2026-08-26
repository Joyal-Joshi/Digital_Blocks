Building Sequential circuits using the derived Logic Gates:

# 1. Latch

## 1.1 S-R Latch

Consider, an OR Gate where the output is fed back to one of its inputs. The value given to the other input will be trapped/latched or stored forever. This method can be used to store bits.

https://github.com/user-attachments/assets/09b7898e-9d82-4f0e-a9dc-186c34b8f7cd

The circuit above can be modified to reset the stored bit, without switching off the entire circuit as shown below.

https://github.com/user-attachments/assets/d18be2eb-aa83-43ee-a5de-3d2073833b2b

Converting all the gates to NAND gate will be give the classic S-R latch.

https://github.com/user-attachments/assets/c79c1ba6-3e9d-410d-9057-2a9f94e0057b

https://www.falstad.com/s.php?s=7v1qmD

## D Latch

The SR latch can be modified, to store a bit of data when the Enable bit is on.

https://github.com/user-attachments/assets/aa708f5f-fbe8-4a15-a275-a15d309323a4

https://www.falstad.com/s.php?s=JVLr6v
