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

