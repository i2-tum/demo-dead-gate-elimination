# demo-dead-gate-elimination
A demonstration that the idea of dead gate elimination works.

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
