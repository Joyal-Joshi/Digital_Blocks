

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

https://www.falstad.com/s.php?s=nEP2gi

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

## 8. Adder/Subtractors

Adders can be designed in many ways depending on the optimization requirements.

### 8.1 Ripple Carry Adder (4 bits)

Ripple carry adder can be used to optimize area and power.

Feed the C_out of previous bits to the C_in to form the ripple carry adder.

t_pd = (N-1)*t_carry  + t_sum

Latency : O(N)

Throughput: O(1/N)

Hardware: O(N)

https://github.com/user-attachments/assets/3a0e4c06-0481-49a5-9c90-2071dc887db6

https://www.falstad.com/s.php?s=G1FyEt

### 8.2. Carry Bypass adder 

To understand carry bypass, we need to convert the inputs to Generate, Propogate and Delete Signals.

C_out = AB + (A⊕B)C

From the above equation it can be observed that an adder generates a C_out, irrespective of C_in when both A and B are 1. The C_in makes the C_out equal to 1 when (A⊕B) is 1. Also, the C_out is 0 if both A and B are 0 irrespective of C_in.

Hence,

G = AB

P = (A⊕B)

D = ĀB̅

| C_in | A | B | S | C_out | G | P | D |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |  
| 0 | 0 | 1 | 1 | 0 | 0 | 0 | 1 |  
| 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 |   
| 0 | 1 | 1 | 0 | 1 | 0 | 1 | 0 |   
| 1 | 0 | 0 | 1 | 0 | 0 | 1 | 0 |   
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 0 |   
| 1 | 1 | 0 | 0 | 1 | 1 | 0 | 0 |   
| 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 |   

After converting the inputs to these signals, the propogate signal can be used to bypass adders by calculating the carry beforehand, decreasing the propogation delay. The dotted line in the diagram below shows the critical path. It bypasses all the adders except for the first one due to the property of propogate and generate signals. 

The point where the generate signal is 1 can be used to break the adder up, as the following adder circuit is independent of the C_in and addition done before. Hence, only G0 being on will give the longest unbroken path. 
Also, the above truth table shows that generate, propogate, and delete signals are mutually exclusive, that is only 1 signal is on at a time, making all the other propogate signals on.

<img width="733" height="195" alt="image" src="https://github.com/user-attachments/assets/0e64583a-c5e1-4304-a7f1-44f11f1bed19" />

t_pd = t_gp + K*t_carry + (N/K-1)*t_mux + (K-1)*t_carry + t_sum

where, K is the size of the each divided adder block.

To , find the most optimal K, the above equation can be partially differentiated to get,

K = sqrt((N * t_mux)/(2 * t_carry))

### 8.3 Carry Select Adder (4 bits)

Instead of waiting for the carry to ripple through, the adder is divided into two parts from the middle. The higher bits are solved for both possibilities of C_in simultaneously along with the lower half of the bits and later a Mux is used to select between them. This reduces the delay in the expense of power and area. The adder can be divided multiple times to get the best match of requirements for delay and area.

The delay for n-bit binary is of the order sqrt(n)

Latency : O(sqrt(N))

Throughput: O(1/sqrt(N))

Hardware: O(2N)

<img width="1736" height="685" alt="image" src="https://github.com/user-attachments/assets/8c80c671-ec86-4499-b0fa-576dbb203ffc" />

Instead of equally dividing the bits, bits can be divided into smaller chunks and increase progressively to get smaller delays.

<img width="1753" height="615" alt="image" src="https://github.com/user-attachments/assets/87371f34-ad8a-4252-868f-96d730bbb8a5" />

https://github.com/user-attachments/assets/641e3a20-6263-405f-b444-1b8493fd4c4d

https://www.falstad.com/s.php?s=w6hWUn

### 8.4 Carry Lookahead Adder/Subtractor (4 bit)

Instead of waiting for the carry to ripple through, the carries can be calculated simultaneously with adders to decrease the time of propogation.

The delay for n bits is of the order log(n).

The concepts from 2's complement is used to add the subtractor module to the base CLA adder.

Latency : O(log(N))

Throughput: O(1/log(N))

Hardware: O(2N)

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


### 8.5. Parallel Prefix Adders (8bits)

CLA needs to go back and forth to calculate the G and P first then to calculate the carry. The tree structure of Parallel Prefix Adders completely remove it, and only needs to traverse the tree once.

https://github.com/user-attachments/assets/be03ee01-3e37-4ffb-b8b6-8d8fad9810b1

## 9.Multiplier (4 bit)

### 9.1 Array Multiplier (Unsigned 4 bits)

<img width="890" height="380" alt="image" src="https://github.com/user-attachments/assets/41fcc4c7-054d-4203-91f7-e454bca85c31" />

The way multiplication is done normally is directly done using hardware in one clock cycle.

There are 2 parts to array multipliers: 

- generating the partial products

- adding the partial products

https://github.com/user-attachments/assets/795e2dba-9add-4e1a-a87d-0abaa771481e

Latency : O(2N)

Throughput: O(1/2N)

Hardware: O(N^2)

### 9.2 Carry-save Multiplier (Unsigned 4 bits)

In Array multiplier, each row is a ripple carry adder, waiting for the carry to ripple through, increasing the delay.

The carry-save multiplier does not wait for the carry to ripple. It does not matter when the carry is added to the partial products in a particular column. Hence, the carry is passed to the next layer of adders, instead of waiting for the carry. The carry-save multiplier adds an an extra layer of adders at the end, which can be optimized using Lookahead adders for smaller delays.

This way carry-save multiplier makes the multiplier part independent of the rows.

The critical path passes through 7 adders, compared to 8 adders in Array Multiplier. This difference grows with the size of operands.

There are 3 parts to the Carry-save multipliers:

- generate the partial products

- Reducing the rows of partial products

- Optimized Final Adder

https://github.com/user-attachments/assets/923d357c-1c93-4cd7-ad79-2a8fbb00944f

### 9.3 Wallace Tree Multiplier (Unsigned 4 bits)

The partial products in a column can be added anytime and does not need to follow the fixed pattern. The Wallace tree tries to utilize this and rearranges the additions of the partial products in a column to reduce the rows faster, using fewer layers of adders. 

The critical path of Wallace tree for 4 bits passes through 6 adders, compared to 8 adders in Array Multiplier. This difference grows with the size of operands.

The image below shows the Wallace Tree reduction for 8 X 8:

<img width="544" height="674" alt="image" src="https://github.com/user-attachments/assets/53a0557c-684d-4886-b6fb-6109f87b4305" />

https://github.com/user-attachments/assets/b9169df3-0bd7-4e01-82c9-a9139eace4f8

### 9.4 Dadda Multipliers (Unsigned 4 bits)

The Wallace Tree uses 5 Full Adders and 3 Half Adders in the reduction stage of 4x4 multipliers. The Full adders take 3 inputs and compress it to 2 outputs, whereas the Half adders don't do any compression. It just moves one bit to higher order. The multiplier is forced to use half adders, to reduce the extra bits. If the Wallace tree is expanded backwards, the optimal size for each layer can be obtained - 2,3,4,6,9,13,19,28,42,63. The Dadda multiplier only reduce the columns to the required size.

The Dadda multiplier only uses 3 Full Adders and 3 Half adders for the reduction stage of 4x4 multiplier. But, the reduction hardware comes at the expense of larger bit size at the final adder. But, the optimization using Lookahead adders make up for it.

The critical path of dadda multiplier for 4 bits passes through 6 adders, compared to 8 adders in Array Multiplier. This difference grows with the size of operands.

The image below show the Dadda reduction for 8x8:

<img width="188" height="308" alt="image" src="https://github.com/user-attachments/assets/de7493c6-549d-467c-83b2-d4cd1534e337" />

https://github.com/user-attachments/assets/cc9898bc-7afc-4510-bc41-96f4c493e60b

### 9.5 Modified Booth Dadda multiplier with CLA as fast adder (4 bits)

The Booth's recoding tries to compress the streams of 1 using a ternary number system (1,0,-1). Eg: 011100 can be represented as 100-100, as 1000 - 1 = 111.

Add a dummy 0 at the end and group the bits in groups of 2 and use the table below, to do the booth's recoding:

| D1 | D0 | recode |
| --- | --- | --- | 
| 0 | 0 | 0 | 
| 0 | 1 | 1 |  
| 1 | 0 | -1 | 
| 1 | 1 | 0 | 

The recoded bits are then rewritten in radix 4. This represents the Modified Booth's recoding. Again pair the bits in groups of 2 and change them to radix 4, using the table below:

| D1' | D0' | Modified recode |
| --- | --- | --- | 
| 0 | 0 | 0 | 
| 0 | 1 | 1 |  
| 1 | 0 | 2 | 
| 0 | -1 | -1 |  
| -1 | 0 | -2 | 
| -1 | 1 | -1 |  
| 1 | -1 | 1 | 

The modified booth recoding can be directly done by combining the above tables as shown below:

| D2 | D1 | D0 | modified recode |
| --- | --- | --- | --- |
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 2 |
| 1 | 0 | 0 | -2 |
| 1 | 0 | 1 | -1 |
| 1 | 1 | 0 | -1 |
| 1 | 1 | 1 | 0 |

Modified Booth's Algorithm is applied on the multiplier and then the multiplicand is multiplied with the multiplier. This decreases the total number of partial products by half, hence reducing Dadda reduction stages and CLA stages.

The multiplicand passes through 3 multiplexers, choosing between A or 0 , A or -A , A or 2A. To note, instead of implementing the complete 2's complement circuit, ~A can found and the addition by 1 can be handled by the Dadda multiplier.

The final addition is replaced by Carry Lookahead Adders, to further optimize the multiplier.

The benefits of Modified Booth Dadda Multiplier with PPA is clearer with bigger operands.

To note, the partial products should be sign extended to full extend to account for the signed values. This will add for adders in the dadda multiplier, but the delay will remain the same.

https://github.com/user-attachments/assets/8679261c-a0bf-4444-ad21-08b74003da58

<img width="781" height="692" alt="image" src="https://github.com/user-attachments/assets/b36e297c-f928-4924-bbb1-7e5443b33255" />

## 10. Array Dividers (Unsigned 4 bits)

The way division is done normally is directly done using hardware in one clock cycle.

https://github.com/user-attachments/assets/77e0cd4f-de27-46e2-a2fc-7d68ad056489


## 11. Barrel Shifters (32 bits)

Shifting operation can be done using Shift registers in a sequential way. Instead, 2x1 mux can be used in layers to shift and select to make a shifter using pure combinational circuits. 

Each bit in the shift amount becomes the selector for each layer of mux's The mux's in each layer will be select between the original input and the value shifted right by 2^shift_amount_bit.

The left shifting is done by reversing the original value and then doing right shift operations and then reverting it back after the operations. These can also be achieved using mux's. 

For logical shift 0 is used to fill the new spaces and for arithmetic A[31] is used.

https://github.com/user-attachments/assets/208eab91-41ba-4b6a-9f3e-2e2e566d254b

## 12. 32 bit Arithmetic Logic Unit (ALU)

All the combinational circuits can be combined into one block. 

The circuit below does:

Arithmetic: Addition, Subtraction , Multiplication ,Division

Logical: ADD, OR, XOR, XNOR

Shift operations: Shift Left Logical, Shift Right Logical, Shift Right Arithmetic

Comparative : Compare if Equal, Compare if Less than or Equal, Compare if Less Than

https://github.com/user-attachments/assets/9bdbf7b4-d4ff-40fd-bb53-e0b30be08dea



