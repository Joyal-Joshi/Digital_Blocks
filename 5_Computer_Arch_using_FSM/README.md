Example Problem: Find the Factorial of N?

The problem above will be used to demonstrate the evolution of computer architecture from a simple FSM.

# 1. FSM to solve a specific problem

## 1.a. writing C Code or pseudo-code for finding factorial of N

int a = 1;

int b = N;

do{ 

  a = a * b;
 
  b = b - 1;

}while( b!=0 );

## 1.b. Converting the code to Finite State Machine

A finite state machine is a machine that stays in a fixed state from a fixed number of states at any given time. The machine can take external inputs, and transition from one state to the other. The transition is shown through arrows pointing to the new state.

<img width="362" height="176" alt="image" src="https://github.com/user-attachments/assets/7661e16a-589f-4418-8150-670bb39e9881" />

The finite state machine to calculate the factorial of N can be modeled as shown below:

<img width="206" height="90" alt="image" src="https://github.com/user-attachments/assets/79dd9156-fa1a-4f7f-94d9-d04f9a84333a" />

## 1.c. Implementing the FSM

Each state at a moment in the Finite State Machine can be stored using sequential circuits and the next state can be calculated using the current state and the external inputs using combinational circuits. Hence, any FSM, can be modeled as a combination of sequential and combinational circuits as shown in the figure below:

<img width="389" height="174" alt="image" src="https://github.com/user-attachments/assets/4fb01fc4-c956-4e15-bdf1-12992de5c930" />

If we assume the variables a and b to be stored in 32 bit Registers, then there are 2^66 possible states, {var_a(32) + var_b(32) + a_sel + b_sel = 66}. The number of states can be reduced by dividing the single FSM to two distinct dependent FSM's: control FSM and Datapath FSM. The next state only depends on the current state and the status of the Datapath FSM which reduces the size of the state. The next state and the control for the Datapath FSM is calculated by the control FSM. 

https://github.com/user-attachments/assets/5648d2c4-5d18-4aa6-996f-021d53368ff1

# 2. Von-Neumann Computer

The FSM made above can only solve factorials. To make a more generic computing device:

1. Add more registers, for operands and results.

2. Add more operations to the repertoire.

3. Add a larger memory, in which the data and instructions can be stored and retrieved.

4. Remove the status bits from the inputs to the control FSM and add it to the combinational circuit inside the control FSM. Also, make the default next state as the current state + state_size. This makes the control FSM a function of the current state only, and the states become equivalent to the address of the instruction.

5. Encode the output of the control FSM to smaller bits, mostly equal to the size of datapath, and add a decoder to decipher it. This encoded output is also known as the ISA(Instruction Set Architecture) of the micro-controller.

6. Allow constants to be added in the instruction for initialization.





