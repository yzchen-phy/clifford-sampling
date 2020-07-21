# clifford-sampling

These are simulation code and data for [Scalable evaluation of quantum-circuit error loss using Clifford sampling (arXiv:2007.10019)](https://arxiv.org/abs/2007.10019) produced by Ying Li and Yanzhu Chen. The experimental data for the two-qubit gates are from Zhen Wang.

The simulations are implemented using the [Mathematica](https://www.wolfram.com/mathematica/) library [QuESTlink](https://questlink.qtechtheory.org/), available at [here](https://github.com/QTechTheory/QuESTLink). Their paper is
```
Tyson Jones, Simon C Benjamin,
"QuESTlink - Mathematica embiggened by a hardware-optimised quantum emulator".
Quantum Sci. Technol. 5, 034012 (2020). arXiv:1912.07904 (2019)
```


The **notebooks** are organized as follows:
- "CS" stands for comparing Clifford sampling to unitary sampling
- "HS" stands for comparing Hybrid sampling to unitary sampling
  in HS the error model is gate-dependent single-qubit depolarizing
- "ddd" stands for depolarising, dephasing, and damping noise
- "Coher" stands for coherent noise consisting of single-qubit rotations
- "sqe" stands for gate-dependent single-qubit depolarizing noise
- "composite" stands for the composite errors consisting of coherent rotations and amplitude damping
- "exp" stands for using the experimentally measured Choi matrices for the two-qubit gates and leaving other components error-free
- "plot" is used for generating the figures
- The file "AllChois.mat" contains all the experimentally measured Choi matrices for the two-qubit gates

The **data files** are organized as follows:
- "CS" stands for comparing Clifford sampling to unitary sampling
- "HS" stands for comparing Hybrid sampling to unitary sampling
  - "C" - Clifford sampling data
  - "H" - hybrid sampling data (1 gate being unitary and others Clifford)
  - "U" - unitary sampling data
- "m" stands for the noise model
  - 0 - depolarising
  - 1 - dephasing
  - 2 - amplitude damping
  - 3 - coherent noise
  - 4 - gate-dependent single-qubit depolarizing
  - c - composite noise
- "expChoi" stands for using the experimentally measured Choi matrices for the two-qubit gates
- "Q" stands for the number of qubits in the circuit
- "G" stands for the number of two-qubit gates in the circuit
- "q" stands for the label for the qubit on which obtaining 0 state is the observable
- "e" stands for the error strength
- "er" stands for the strength of the coherent rotations in the composite noise model
- "ed" stands for the strength of the amplitude damping in the composite noise model
- "r" stands for a randomly generated circuit
- "exp" stands for the main experimental circuit 
- Without "r" or "exp" the circuit is a standard one


To use QuESTlink for simulation with the experimentally measured Choi matrices, one needs to modify the function `macro_isCompletelyPositiveMap` in the file `QuESTlink-master/QuEST/src/QuEST_validation.c` before compiling. In the line `dist_> REAL_EPS`, `REAL_EPS`(=10<sup>-13</sup>) needs to be replaced with some bigger value; for our purpose it is set to 0.5.
