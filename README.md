# demo-dead-gate-elimination
A demonstration that the idea of dead gate elimination works.
Since this is just a demo, we implemented circuits and gates as simplified list-like data structures. 
* Format of circuits: A circuit is a list of gates.
* Format of gates:
[0, q] : single-qubit gate, acting on qubit q;
[n, q1,..., qn] : multi-qubit gate, acting on qubit q1, q2, ..., qn;
[2, q1, q2] : CNOT gate, q1 is controlling qubit;
[-1, i, j] : SWAP gate, acting on qubit i and j.

Note: recall that we made the assumption in the manuscript that the circuit has been optimized by existing state-of-art circuit transpiler. Therefore, we treat all single-qubit gates as the same, and do not consider any possibility of circuit simplification, such as gate cancellation and opportunities gained by taking into account the commutative analysis (because the hypothesis is that we have exhausted such optimizations beforehand). 

The function `gen_random_list_circuit_alike` generates a random circuit based on the above format. `num_qubits` controls the qubit number, `num_gates` sets the number of gates, `p_single` sets the probability of any gate being single-qubit gate, `p_swap` sets the probability for a 2-qubit gate being SWAP.

The function `remove_dead_gates_from_pseudo_list` corresponds to the pseudocode presented in the paper as _Algorithm 1: Dead gates removal_. `invalid_qubits` sets the subset of qubits to be dead at the very end of the circuit.
We have not implemented the while-loop faithfully as presented in the manuscript. Instead, for simplicity, we iterate all gates from the end to the front of the circuit, which does not hurt the efficiency of the algorithm, because Theorem 4 (Algorithm 1 is polynomial) still holds, since for each while-iteration, still $\mathcal{O}(C.\text{gates()})$ many gates are checked. If you are implementing the function based on the pseudocode in the manuscript, there is then on thing to be noted: after performing the statement $C_{opt} \leftarrow C_{opt} - g$, the data structure of the circuit $C_{opt}$ needs to ensure that the frontier, $C_{opt}.frontier()$, gets simultaneously updated.

## Use jupyter notebook
Simply use jupyter notebook to run the experiments.

## Imports needed
To run the code blocks, import the following:
```python
import random
import matplotlib
import matplotlib.pyplot as plt
import numpy as np
import time
```
## Before performing experiments
Run the code block in file `demo-implementation.py`, which is a demo implementation of the algorithm.

## Perform the experiments
* Run the code block in file `experiments-hybrid-program-random-circuits.py` to perform the experiments on hybrid programs embedded with randomly generated circuits and observe the gate reduction gained across varying circuit width.
* Run the code block in file `demo-experiments-runtime.py` to perform the experiments to showcase the efficiency of the proposed algorithm.
