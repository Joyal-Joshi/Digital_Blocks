

Building Combinational circuits using the derived Logic gates:

## 1. Decoder (2 x 4)
   
Converts Binary encoding to individual outputs.

https://github.com/user-attachments/assets/30f23bbb-69b6-4c66-9892-44805f020e8f

https://www.falstad.com/s.php?s=oNSezK

## 2. Encoder(4 x 2)

Converts n inputs to binary.

https://github.com/user-attachments/assets/4616f5c7-28fe-4b41-8198-86586965a3b9

https://www.falstad.com/s.php?s=bSbUu0

## 3. Multiplexer (4 x 1)
   
Selects output from 2^n inputs using n bit encode.

https://github.com/user-attachments/assets/074e3f0e-34ba-418d-8fc0-2fc2b93e6c76

https://www.falstad.com/s.php?s=LlTB17

## 4. Demultiplexer (1 x 4)

The input is only passed onto the output line, given by the binary encode.

https://github.com/user-attachments/assets/3e6953fc-5116-4b76-86cb-83ceb7cf5b08

Waiting for short URL for web service...

## 5. Equality Checker (4 bits)

Checks if two n bit digits are equal or not.

https://github.com/user-attachments/assets/e13717ad-6252-43f6-a57b-903276d04621

https://www.falstad.com/s.php?s=jHh2WN

## 6. Magnitude comparator (4 bits)

To check if A>B, we start form the MSB and move towards LSB if Ai = Bi until Ai > Bi.

To check if A=B XNOR can be used,

and to check A<B the above outputs can be passed through XNOR.

This 4 bit comparator can be cascaded by using the outputs of the LSB comparators.

https://github.com/user-attachments/assets/953109f0-034f-4da4-ae97-bb3b6c89a9ea

https://www.falstad.com/s.php?s=BW0cQN


# Understanding 2's complement

Binary digits are not stored in 2's complement due to the ease in storing 2's complement but because it is easy to operate on 2's complement. To understand why is it easy, other methods will be shown below to compare and contrast.

### a) MSB as the sign bit

The Most significant bit can be used as the sign bit. The digit is negative when the MSB is 1 and positive when it is 0. To design a adder/subtractor for digits stored like this, will be very complicated. 

Disadvantages of using MSB as the sign bit:

There are 8 possible combinations wrt the signs of the digits and the sign of operation. Hence, 8 different adder/subtractor have to designed which needs to be selected according the inputs using a multiplexer. This will increase the area, power and time needed.

The second reason for not using this method is that the process of subtraction itself is complicated. Hence, a different approach is needed.

### b) 1's complement

r's complement for a n digit number is r^n - n, and (r-1)'s complement for a n digit number is r^n-n-1.

Let's take an example: 45-27

Instead of subtracting 45 with 27, add 47 with 27's 9's complement which is 72(27+72=99). That gives the answer as 117. By adding 9's complement the answer has shifted up by 99, which can be brought back by subtracting with 100 or removing the 1 in the front and then adding by 1, to get the final answer (18). 

This can be done in binary which is called 1's complement. 

45 = 0b00101101

27 = 0b00011011

1's complement of 27 = 0b11100100 (simply inverting the bits) 

45 + 1's complement of 27 = 0b100010001

Then taking the carry and adding it back to get the final answer: 0b00010010 which is 18.

The 1's complement can be considered as the negative value of the number and stored in the memory. This automatically reserves the MSB as sign bit. Hence, whenever there is a carry, it means that subtraction has taken place, and 1 needs to be added.

Disadvantages of 1's complement:

There are 2 ways to represent 0 in 1's complement, which makes it difficult to use it for comparisons.

The carry around addition added additional steps to the process.


### c) 2's complement

Let's take the same example: 45-27

Instead of subtracting 45 with 27, add with 27's 10's complement which is 73(27+73=100). Then simply subtract by 100 to get the final answer (18).

Now, doing this in binary:

45 = 0b00101101

27 = 0b00011011

1's complement of 27 = 0b11100100 (simply inverting the bits) 

2's complement of 27 = 0b11100101 (adding to 1's complement) 

45 + 2's complement of 27 = 0b100010010 (final answer = 18)

The 2's complement can be considered as the negative value of the number and stored in the memory. This automatically reserves the MSB as -ve value of the biggest possible +ve value. The 2's complement incorporates the addition of carry in it and also removes the dual zeros.

## 7. Full Adder (1 bit)

| C_in | A | B | S | C_out | 
| --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 0 | 0 | 
| 0 | 0 | 1 | 1 | 0 | 
| 0 | 1 | 0 | 1 | 0 | 
| 0 | 1 | 1 | 0 | 1 | 
| 1 | 0 | 0 | 1 | 0 | 
| 1 | 0 | 1 | 0 | 1 | 
| 1 | 1 | 0 | 0 | 1 | 
| 1 | 1 | 1 | 1 | 1 | 

Using Sum of Products: 

S = ĀBC̄ + AB̅C̄ + ĀB̅C + ABC = (A⊕B)C̄ + (ĀB̅ + AB)C = A ⊕ B ⊕ C

C_out = ABC̄ + AB̅C + ĀBC + ABC = AB(C+C̄) + (A⊕B)C = AB + (A⊕B)C

https://github.com/user-attachments/assets/ee83337e-b2f1-41ff-a29e-600d09d0f647

https://www.falstad.com/s.php?s=efT2bc

## 8. 4 bit Adders

Adders can be designed in many ways depending on the optimization requirements.

### 8.1 Ripple Carry Adder (4 bits)

Ripple carry adder can be used to optimize area and power.

Feed the C_out of previous bits to the C_in to form the ripple carry adder.

The delay for n bits is of the order n.

https://github.com/user-attachments/assets/3a0e4c06-0481-49a5-9c90-2071dc887db6

https://www.falstad.com/s.php?s=G1FyEt

### 8.2 Carry Select Adder (4 bits)

Instead of waiting for the carry to ripple through, the adder is divided into two parts from the middle. The higher bits are solved for both possibilities of C_in simultaneously along with the lower half of the bits and later a Mux is used to select between them. This reduces the delay in the expense of power and area. The adder can be divided multiple times to get the best match the requirements of delay and area.

The delay for n-bit binary is of the order sqrt(n)

<img width="1736" height="685" alt="image" src="https://github.com/user-attachments/assets/8c80c671-ec86-4499-b0fa-576dbb203ffc" />

Instead of equally dividing the bits, bits can be divided into smaller chunks and increase progressively to get smaller delays.

<img width="1753" height="615" alt="image" src="https://github.com/user-attachments/assets/87371f34-ad8a-4252-868f-96d730bbb8a5" />

https://github.com/user-attachments/assets/641e3a20-6263-405f-b444-1b8493fd4c4d

https://www.falstad.com/s.php?s=w6hWUn

### 8.3 Carry Lookahead Adder/Subtractor

Instead of waiting for the carry to ripple through, the carries can be calculated simultaneously with adders to decrease the time of propogation.

The delay for n bits is of the order log(n).

The concepts from 2's complement is used to add the subtractor module to the base CLA adder.

Modified Full Adders for CLA:

<img width="718" height="399" alt="image" src="https://github.com/user-attachments/assets/fab664c2-cfae-43b5-8328-3133e246194c" />

The C_out calculation can be removed from the full adder and AB and A^B can be outputted instead for calculating the carry.


The Generate Propogate / Carry module
<img width="835" height="427" alt="image" src="https://github.com/user-attachments/assets/af9e35a8-163b-4687-a29c-72dd9bf3dbac" />

G_HL = G_H + P_H * G_L
P_HL = P_H * P_L
C_H = G_L + P_L * C_in
C_L = C_in

https://github.com/user-attachments/assets/b4fd6432-ad7c-4180-9203-8d52e27d5994

https://www.falstad.com/s.php?s=gz2sbL
