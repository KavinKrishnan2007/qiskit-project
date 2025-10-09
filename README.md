# qiskit-project
🧭 How to Reproduce and Execute (in Web Browser)

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
