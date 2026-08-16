Building Combinational circuits using the derived Logic gates:

1. Decoder (2 x 4)
   
Converts Binary encoding to individual outputs.

https://github.com/user-attachments/assets/30f23bbb-69b6-4c66-9892-44805f020e8f

https://www.falstad.com/s.php?s=oNSezK

2. Multiplexer (4 x 1)
   
Selects output from 2^n inputs using n bit encode.

https://github.com/user-attachments/assets/074e3f0e-34ba-418d-8fc0-2fc2b93e6c76

https://www.falstad.com/s.php?s=LlTB17

3. Equality Checker (4 bits)

Checks if two n bit digits are equal or not.

https://github.com/user-attachments/assets/e13717ad-6252-43f6-a57b-903276d04621

https://www.falstad.com/s.php?s=jHh2WN

4. Magnitude comparator (4 bits)

To check if A>B, we start form the MSB and move towards LSB if Ai = Bi until Ai > Bi.

To check if A=B XNOR can be used,

and to check A<B the above outputs can be passed through XNOR.

This 4 bit comparator can be cascaded by using the outputs of the LSB comparators.

https://github.com/user-attachments/assets/953109f0-034f-4da4-ae97-bb3b6c89a9ea

https://www.falstad.com/s.php?s=BW0cQN

5. Full Adder (4 bits)

Understanding 2's complement
Binary digits are not stored in 2's complement due to the ease in storing 2's complement but because it is easy to operate on 2's complement. To understand why is it easy, other methods will be shown below to compare and contrast.

a) MSB as the sign bit

The Most significant bit can be used as the sign bit. The digit is negative when the MSB is 1 and positive when it is 0. To design a adder/subtractor for digits stored like this will be very complicated. 

There are 8 possible combinations wrt the signs of the digits and the sign of operation. Hence, 8 different adder/subtractor have to designed which needs to selected according the inputs using a multiplexer. This will increase the area, power and time needed.

The second reason for not using this method is that the process of subtraction itself is complicated. Hence, a different approach is needed.

b) 1's complement

Let's take an example: 45-27

Instead of subtracting 45 with 27, add 47 with 27's 9's complement which is 72 (45+72 = 117). Then, subtract 100, by simply removing 1 from the front and then add 1 to the answer to obtain (18).

