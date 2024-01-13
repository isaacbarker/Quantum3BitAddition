### Classical addition using 3 Qubits. 

#### The problem:

Build a quantum circuit which will calculate the sum of 3 classical bits eg. 1 + 0 + 1 or 
1 + 1 + 1.

#### Circuit design.

To create an algorithm that makes use of quantum logic gates, all the possible input states
need to be considered. The maximum sum possible is $1 + 1 + 1$ which is $2^0 + 2^0 + 2^0 = 3$.
This can most easily be broken into $2^1 + 2^0 = 11$ in binary. Another abritary example is $1 + 1 + 0$ which is equivalent in decimal to $2^0 + 2^0 + 0 = 2$. Again, equivalent to $2^1 + 0 = 10$ in binary.

The conditions that need to be satisfied are:

- If there is a $\ket{100}$ or state with only one qubit in $\ket1$ state output `01`.
- If there is a $\ket{110}$ or state with two qubits in $\ket1$ state output `10`.
- If there is a $\ket{111}$ state output `11`.

Firstly, concentrating on the first output qubit, it should only be flipped to $\ket1$ when only one $\ket1$ state is present in the inputs or all 3 inputs are $\ket1$. This can be achieved using a series of CNOTs connected to an output qubit, which cancel eachother out when 2 $\ket1$ states are present. 

Then, to calculate the second output qubit a series of connected Toffoli or CCNOT gates can be used to achieve a $\ket1$ state only when at least two $\ket1$ states are present in the inputs as with only 1 $\ket1$ state none of these such gates' condition will be satisfied. 

Finally, the circuit is measured, mapping qubits 3 and 4 onto classical bits 0 and 1, which represent the outcome of the addition, successfully calculating the sum of 3 bits using quantum logic gates. 
