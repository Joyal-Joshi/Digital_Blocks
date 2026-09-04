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

The finite state machine can be modeled as shown below to calculate the factorial of N.

<img width="206" height="90" alt="image" src="https://github.com/user-attachments/assets/79dd9156-fa1a-4f7f-94d9-d04f9a84333a" />

## 1.c. Implementing the FSM

Any computational problem can be modeled as a Finite State machine. Any finite state machine is a combination of sequential and combinational circuits. The sequential circuits store the current state and the combinational circuits uses the external inputs and the current state to find the next valid state, and store it back into the sequential circuit.

<img width="389" height="174" alt="image" src="https://github.com/user-attachments/assets/4fb01fc4-c956-4e15-bdf1-12992de5c930" />

The original FSM should consist of variables a and b as the state, and the combinational circuit will convert it to the next state. However, this will lead to 2^64 different states, as each variable is 32 bits in size. A pattern can be observed among these states depending on the operations done. The states can be classified wrt these patterns. The next state only depends on these subclass and the status bits, calculated from the variables. The sub-class can replace the old states.

Hence, the FSM can be divided into two parts: a Control FSM and a Datapath FSM. The control FSM converts the current state and status bits to the next state and the control bits for the Datapath FSM. The Datapath FSm will convert the variables for t he next state.

From the FSM diagram, three distinct states can be identified for the above problem. The start, loop and stop. The sequential circuit for the problem will consist of three registers which can store the values of a, b and the state. 

The combinational circuits take the state value and internal states a and b to calculate the next state. The combinational circuit can also be replaced with a lookup table made of ROM. 32 bit registers should be enough to solve this problem.



https://github.com/user-attachments/assets/5648d2c4-5d18-4aa6-996f-021d53368ff1

# 2. Making a General computer using FSM

The FSM made above can only solve factorials. To make a more generic computing device:

1. Add more registers, for operands and results.

2. Add more operations to the repertoire.





