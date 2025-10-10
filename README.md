# qiskit-project
This code implements the Deutsch–Jozsa algorithm using IBM Qiskit in OpenQASM 2.0. OpenQASM 2.0 is a programming language used to describe quantum circuits and operations on quantum computers.
The goal of the algorithm is to determine whether a given function `f(x)` is constant or balanced. 

To do this:
1. I used 3 input qubits (q[0], q[1], q[2]) and 1 ancilla qubit (q[3]).
2. An ancillary qubit is an extra helping qubit. It holds intermediate results during calculation and stores temporary or hidden information. The ancilla starts in state |1⟩ and is superimposed using a Hadamard gate so that the oracle can create a phase difference.
3. Hadamard gates on input qubits create a superposition, testing all possible inputs at once.
4. Next, I apply the oracle for my function f(x₀, x₁, x₂) = x₀ ⊕ x₁ ⊕ x₂. The oracle flips the ancilla qubit conditionally, effectively adding a phase (-1)^{f(x)} to each input state.
5. The oracle section represents the black-box function f(x), which can be either constant or balanced.
6. The final Hadamard and measurement steps reveal the nature of f(x):
- If all measurements are 000, the function is constant.
- If any other result appears, the function is balanced.
     
🧭 **How to Reproduce and Execute (in Web Browser)**

### Using IBM Quantum Composer (recommended)
1. Go to [IBM Quantum Composer](https://quantum.ibm.com/composer)
2. Sign in with your IBM Quantum account (create one if needed)
3. Click **“New Circuit”**
4. On the top-right, click **“Code”** and select **OpenQASM** view
5. Paste the following code into the editor:
6.
OPENQASM 2.0;

include "qelib1.inc";

qreg q[4];

creg c[3];

h q[2];

h q[0];

h q[3];

h q[1];

cx q[0], q[3];


cx q[1], q[3];

cx q[2], q[3];

h q[0];

h q[1];

h q[2];

measure q[0] -> c[0];

measure q[1] -> c[1];

measure q[2] -> c[2];

8. Click “Run” on the top bar and select Simulator as backend.
9. Wait for execution results.
- If the output (counts) show only 000, the oracle is constant.
- If the output shows any pattern other than 000, the oracle is balanced.
9. The picture of the quantum circuit is added in the section I PDF file. 

