# 7-Day Python Refresh for Quantum Software Development

This 7-day refresh is for developers who already know basic Python and want to prepare for quantum software development with **Qiskit**, **PennyLane**, **NumPy**, and Jupyter notebooks.

The goal is not to relearn Python from zero. The goal is to refresh only the Python concepts that matter most for quantum computing:

- NumPy arrays
- Vectors and matrices
- Matrix multiplication
- Complex numbers
- Probability and sampling
- Functions and reusable code
- Matplotlib visualizations
- Mini quantum-style simulations

---

## How to use this file

For each day:

1. Read the priority concepts.
2. Code the examples yourself.
3. Solve the 25 practice questions.
4. Commit your notebook or script to GitHub.
5. Write 3–5 lines in your notes about what you learned.

Recommended folder:

```text
week-01-foundations/
├── 00_python_refresh_numpy.ipynb
├── 01_vectors_and_matrices.ipynb
├── 02_matrix_multiplication.ipynb
├── 03_complex_numbers.ipynb
├── 04_probability_sampling.ipynb
├── 05_functions_for_quantum.ipynb
├── 06_visualization.ipynb
└── 07_mini_quantum_simulator.ipynb
```

---

# Day 1: NumPy Basics for Quantum Computing

## Goal

Refresh NumPy basics because quantum states, gates, and measurement results are easier to work with using arrays.

## Concepts to prioritize

- `np.array()`
- 1D arrays
- 2D arrays
- Array shape
- Array indexing
- Array slicing
- `np.zeros()`
- `np.ones()`
- `np.eye()`
- `np.sqrt()`
- Difference between Python lists and NumPy arrays

## Why this matters for quantum

In quantum computing:

```text
Quantum state = NumPy vector
Quantum gate = NumPy matrix
Probability list = NumPy array
```

Example:

```python
import numpy as np

zero_state = np.array([1, 0])
one_state = np.array([0, 1])

print(zero_state)
print(one_state)
print(zero_state.shape)
```

## Practice questions: Day 1

1. Create a NumPy array representing the quantum state `|0⟩ = [1, 0]`.
2. Create a NumPy array representing the quantum state `|1⟩ = [0, 1]`.
3. Print the shape of both `|0⟩` and `|1⟩` arrays.
4. Create a 2x2 identity matrix using `np.eye()`.
5. Create a 2x2 zero matrix using `np.zeros()`.
6. Create a 2x2 matrix filled with ones using `np.ones()`.
7. Create a NumPy array `[0.5, 0.5]` and print its sum.
8. Create a NumPy array `[1, 2, 3, 4]` and print the first element.
9. Create a NumPy array `[1, 2, 3, 4]` and print the last element.
10. Create a 2D matrix `[[1, 2], [3, 4]]` and print its shape.
11. From the matrix `[[1, 2], [3, 4]]`, print the element `3` using indexing.
12. Create a vector `[1, 0]` as a Python list and as a NumPy array. Print both.
13. Add two NumPy arrays: `[1, 0] + [0, 1]`.
14. Multiply the NumPy array `[1, 2, 3]` by `2`.
15. Use `np.sqrt(2)` and print the result.
16. Create an array `[1 / np.sqrt(2), 1 / np.sqrt(2)]`.
17. Print the sum of `[1 / sqrt(2)]² + [1 / sqrt(2)]²`.
18. Create an array of probabilities `[0.25, 0.75]` and check if the sum is `1`.
19. Create a 3-element array and print its length.
20. Create a 2x3 matrix and print the number of rows and columns.
21. Convert a Python list `[5, 10, 15]` into a NumPy array.
22. Create an array `[1, 2, 3, 4, 5]` and slice the first three values.
23. Create an array `[1, 2, 3, 4, 5]` and slice the last two values.
24. Create a matrix using `np.array()` and print each row.
25. Write a short note explaining why NumPy arrays are useful for quantum computing.

## Git commit

```bash
git add .
git commit -m "Refresh NumPy basics for quantum computing"
```

---

# Day 2: Vectors and Matrices

## Goal

Understand how quantum states and gates can be represented as vectors and matrices.

## Concepts to prioritize

- Vectors
- Matrices
- Column-vector thinking
- State vectors
- Gate matrices
- Matrix dimensions
- Basis states
- Identity matrix
- Pauli-X matrix

## Why this matters for quantum

The basic one-qubit states are:

```text
|0⟩ = [1, 0]
|1⟩ = [0, 1]
```

The X gate is:

```text
X = [[0, 1],
     [1, 0]]
```

It flips `|0⟩` to `|1⟩` and `|1⟩` to `|0⟩`.

Example:

```python
import numpy as np

zero = np.array([1, 0])
one = np.array([0, 1])

X = np.array([
    [0, 1],
    [1, 0]
])

print(X @ zero)
print(X @ one)
```

## Practice questions: Day 2

1. Create the vector for `|0⟩`.
2. Create the vector for `|1⟩`.
3. Create the 2x2 identity matrix.
4. Create the Pauli-X matrix.
5. Create the Pauli-Z matrix `[[1, 0], [0, -1]]`.
6. Create the Hadamard matrix using `1 / np.sqrt(2)`.
7. Print the shape of the Pauli-X matrix.
8. Print the shape of the Hadamard matrix.
9. Check if `|0⟩` has shape `(2,)`.
10. Apply the identity matrix to `|0⟩`.
11. Apply the identity matrix to `|1⟩`.
12. Apply the X matrix to `|0⟩`.
13. Apply the X matrix to `|1⟩`.
14. Apply the Z matrix to `|0⟩`.
15. Apply the Z matrix to `|1⟩`.
16. Apply the Hadamard matrix to `|0⟩`.
17. Apply the Hadamard matrix to `|1⟩`.
18. Print the probabilities of the result after applying H to `|0⟩`.
19. Print the probabilities of the result after applying H to `|1⟩`.
20. Create a custom 2x2 matrix and multiply it with `[1, 0]`.
21. Create a function called `print_state(name, state)` that prints a state name and vector.
22. Store X, Z, H, and I gates in a dictionary.
23. Retrieve the X gate from the dictionary and apply it to `|0⟩`.
24. Write a short explanation of why gates are matrices.
25. Write a short explanation of why states are vectors.

## Git commit

```bash
git add .
git commit -m "Practice vectors and matrices for quantum states"
```

---

# Day 3: Matrix Multiplication and Gate Application

## Goal

Understand that applying a quantum gate means multiplying a matrix by a state vector.

## Concepts to prioritize

- `@` operator
- `np.dot()`
- Matrix-vector multiplication
- Matrix-matrix multiplication
- Gate chaining
- Order of operations
- Applying multiple gates

## Why this matters for quantum

In quantum software, when you apply a gate, you are transforming the state.

```text
new_state = gate @ old_state
```

Example:

```python
import numpy as np

zero = np.array([1, 0])

X = np.array([
    [0, 1],
    [1, 0]
])

new_state = X @ zero
print(new_state)
```

## Practice questions: Day 3

1. Multiply the X gate with `|0⟩` using the `@` operator.
2. Multiply the X gate with `|1⟩` using the `@` operator.
3. Multiply the identity gate with `|0⟩`.
4. Multiply the identity gate with `|1⟩`.
5. Multiply the Z gate with `|0⟩`.
6. Multiply the Z gate with `|1⟩`.
7. Multiply the H gate with `|0⟩`.
8. Multiply the H gate with `|1⟩`.
9. Apply X twice to `|0⟩`. What is the final state?
10. Apply H twice to `|0⟩`. What is the final state?
11. Apply X then H to `|0⟩`.
12. Apply H then X to `|0⟩`.
13. Compare the result of X then H vs H then X.
14. Create a function `apply_gate(gate, state)`.
15. Use `apply_gate()` to apply X to `|0⟩`.
16. Use `apply_gate()` to apply H to `|0⟩`.
17. Create a function `apply_gates(gates, state)` that applies a list of gates in order.
18. Use `apply_gates()` with `[H, X]`.
19. Use `apply_gates()` with `[X, H]`.
20. Use `np.dot()` instead of `@` and compare results.
21. Multiply X matrix by X matrix and print the result.
22. Multiply H matrix by H matrix and print the result.
23. Check if `X @ X` equals the identity matrix using `np.allclose()`.
24. Check if `H @ H` equals the identity matrix using `np.allclose()`.
25. Write a short note explaining why gate order matters.

## Git commit

```bash
git add .
git commit -m "Practice matrix multiplication and gate application"
```

---

# Day 4: Complex Numbers and Probability Amplitudes

## Goal

Understand complex numbers because quantum amplitudes can be real or complex.

## Concepts to prioritize

- Python complex numbers
- `1j`
- Real part
- Imaginary part
- Complex conjugate
- Magnitude
- `np.abs()`
- Probability from amplitude
- Squared magnitude

## Why this matters for quantum

A quantum state can have complex amplitudes:

```text
[1/sqrt(2), i/sqrt(2)]
```

Probabilities come from squared magnitude:

```text
probability = |amplitude|²
```

Example:

```python
import numpy as np

state = np.array([
    1 / np.sqrt(2),
    1j / np.sqrt(2)
])

probabilities = np.abs(state) ** 2
print(probabilities)
```

## Practice questions: Day 4

1. Create a complex number `1 + 2j`.
2. Print the real part of `1 + 2j`.
3. Print the imaginary part of `1 + 2j`.
4. Print the magnitude of `1 + 2j` using `abs()`.
5. Print the conjugate of `1 + 2j`.
6. Create a NumPy array with complex values `[1+0j, 0+1j]`.
7. Create the state `[1/sqrt(2), 1j/sqrt(2)]`.
8. Calculate probabilities using `np.abs(state) ** 2`.
9. Check if the probabilities sum to 1.
10. Create a state `[0.6, 0.8]` and calculate probabilities.
11. Check if `[0.6, 0.8]` is normalized.
12. Create a state `[0.5, 0.5]` and check if it is normalized.
13. Normalize the state `[3, 4]`.
14. Create a function `get_probabilities(state)`.
15. Use `get_probabilities()` on `[1, 0]`.
16. Use `get_probabilities()` on `[0, 1]`.
17. Use `get_probabilities()` on `[1/sqrt(2), 1/sqrt(2)]`.
18. Use `get_probabilities()` on `[1/sqrt(2), 1j/sqrt(2)]`.
19. Create a function `is_normalized(state)`.
20. Test `is_normalized()` on `[1, 0]`.
21. Test `is_normalized()` on `[1/sqrt(2), 1/sqrt(2)]`.
22. Test `is_normalized()` on `[1, 1]`.
23. Create a function `normalize(state)`.
24. Normalize `[1, 1]` and print probabilities.
25. Write a note explaining amplitude vs probability.

## Git commit

```bash
git add .
git commit -m "Practice complex numbers and quantum amplitudes"
```

---

# Day 5: Probability, Sampling, and Measurement

## Goal

Simulate quantum measurement using probability distributions and repeated sampling.

## Concepts to prioritize

- Probability distribution
- `np.random.choice()`
- Shots
- Counts
- Sampling randomness
- Measurement result
- Repeated experiments

## Why this matters for quantum

Quantum measurement is probabilistic. If a qubit has probabilities `[0.5, 0.5]`, one measurement gives either `0` or `1`, but many shots give counts close to 50/50.

Example:

```python
import numpy as np

probabilities = [0.5, 0.5]
results = np.random.choice([0, 1], size=1000, p=probabilities)
unique, counts = np.unique(results, return_counts=True)
print(dict(zip(unique, counts)))
```

## Practice questions: Day 5

1. Use `np.random.choice()` to randomly choose between `0` and `1`.
2. Use `np.random.choice()` with probabilities `[0.5, 0.5]`.
3. Use `np.random.choice()` with probabilities `[0.8, 0.2]`.
4. Run 10 shots with probabilities `[0.5, 0.5]`.
5. Run 100 shots with probabilities `[0.5, 0.5]`.
6. Run 1000 shots with probabilities `[0.5, 0.5]`.
7. Compare the counts from 10, 100, and 1000 shots.
8. Create a function `measure(probabilities, shots)`.
9. Use `measure()` with `[1, 0]`.
10. Use `measure()` with `[0, 1]`.
11. Use `measure()` with `[0.5, 0.5]`.
12. Use `measure()` with `[0.25, 0.75]`.
13. Convert a state vector into probabilities using `np.abs(state) ** 2`.
14. Measure the state `[1, 0]`.
15. Measure the state `[0, 1]`.
16. Measure the state `[1/sqrt(2), 1/sqrt(2)]`.
17. Measure the state `[sqrt(0.25), sqrt(0.75)]`.
18. Create a counts dictionary manually.
19. Create a function that returns the most frequent measurement result.
20. Create a function that returns counts as percentages.
21. Simulate 5000 shots and print percentages.
22. Set a random seed using `np.random.seed(42)` and observe repeatability.
23. Remove the seed and observe randomness.
24. Write a note explaining why one measurement is not enough to understand a quantum state.
25. Write a note explaining what shots mean in Qiskit.

## Git commit

```bash
git add .
git commit -m "Simulate quantum measurement with probability sampling"
```

---

# Day 6: Functions, Clean Code, and Visualization

## Goal

Write reusable Python helpers and visualize measurement results.

## Concepts to prioritize

- Functions
- Return values
- Clean naming
- Reusable helpers
- Matplotlib bar charts
- Plotting counts
- Plotting probabilities
- Script structure

## Why this matters for quantum

As your circuits get bigger, clean helper functions make experiments easier to understand.

Useful helpers:

```python
def apply_gate(gate, state):
    return gate @ state


def get_probabilities(state):
    return np.abs(state) ** 2


def measure_state(state, shots=1000):
    probabilities = get_probabilities(state)
    outcomes = list(range(len(state)))
    results = np.random.choice(outcomes, size=shots, p=probabilities)
    unique, counts = np.unique(results, return_counts=True)
    return dict(zip(unique, counts))
```

## Practice questions: Day 6

1. Write a function `apply_gate(gate, state)`.
2. Write a function `get_probabilities(state)`.
3. Write a function `is_normalized(state)`.
4. Write a function `normalize(state)`.
5. Write a function `measure_state(state, shots)`.
6. Write a function `print_state(state)`.
7. Write a function `plot_counts(counts)`.
8. Write a function `plot_probabilities(probabilities)`.
9. Apply X to `|0⟩` using `apply_gate()`.
10. Apply H to `|0⟩` using `apply_gate()`.
11. Get probabilities after applying H to `|0⟩`.
12. Measure the H-transformed state for 1000 shots.
13. Plot the measurement counts.
14. Plot the theoretical probabilities.
15. Create a dictionary of gates: `I`, `X`, `Z`, `H`.
16. Write a function `get_gate(name)` that returns a gate from the dictionary.
17. Use `get_gate("H")` and apply it to `|0⟩`.
18. Write a function `run_experiment(gate, state, shots)`.
19. Use `run_experiment()` with X gate.
20. Use `run_experiment()` with H gate.
21. Add comments to your functions.
22. Add type hints to at least two functions.
23. Create a Python script instead of a notebook for one experiment.
24. Run the script from the terminal.
25. Write a note explaining why reusable functions are important for Qiskit/PennyLane projects.

## Git commit

```bash
git add .
git commit -m "Add reusable quantum-style Python helpers and plots"
```

---

# Day 7: Mini Python-Only Quantum Simulator

## Goal

Build a tiny Python-only quantum simulator for one-qubit gates before moving deeper into Qiskit.

## Concepts to prioritize

- State initialization
- Gate definition
- Gate application
- Probability calculation
- Measurement simulation
- Counts visualization
- Basic project structure

## What to build

Create:

```text
projects/python-mini-quantum-simulator/
├── mini_quantum_simulator.py
└── README.md
```

Example starter code:

```python
import numpy as np
import matplotlib.pyplot as plt


ZERO = np.array([1, 0])
ONE = np.array([0, 1])

I = np.array([
    [1, 0],
    [0, 1]
])

X = np.array([
    [0, 1],
    [1, 0]
])

Z = np.array([
    [1, 0],
    [0, -1]
])

H = (1 / np.sqrt(2)) * np.array([
    [1, 1],
    [1, -1]
])


def apply_gate(gate, state):
    return gate @ state


def get_probabilities(state):
    return np.abs(state) ** 2


def measure_state(state, shots=1000):
    probabilities = get_probabilities(state)
    outcomes = list(range(len(state)))
    results = np.random.choice(outcomes, size=shots, p=probabilities)
    unique, counts = np.unique(results, return_counts=True)
    return dict(zip(unique, counts))


def plot_counts(counts):
    plt.bar([str(k) for k in counts.keys()], counts.values())
    plt.xlabel("Measurement Result")
    plt.ylabel("Counts")
    plt.title("Measurement Counts")
    plt.show()


if __name__ == "__main__":
    state = ZERO
    state = apply_gate(H, state)

    print("Final state:", state)
    print("Probabilities:", get_probabilities(state))

    counts = measure_state(state, shots=1000)
    print("Counts:", counts)

    plot_counts(counts)
```

## Practice questions: Day 7

1. Create a project folder called `python-mini-quantum-simulator`.
2. Create `mini_quantum_simulator.py`.
3. Define `ZERO` and `ONE` states.
4. Define the Identity gate.
5. Define the X gate.
6. Define the Z gate.
7. Define the H gate.
8. Write `apply_gate()`.
9. Write `get_probabilities()`.
10. Write `measure_state()`.
11. Write `plot_counts()`.
12. Apply X to `ZERO` and print the result.
13. Apply X to `ONE` and print the result.
14. Apply H to `ZERO` and print the result.
15. Apply H to `ONE` and print the result.
16. Apply H twice to `ZERO`.
17. Apply X twice to `ZERO`.
18. Check if `H @ H` is identity using `np.allclose()`.
19. Check if `X @ X` is identity using `np.allclose()`.
20. Measure `ZERO` for 1000 shots.
21. Measure `ONE` for 1000 shots.
22. Measure `H @ ZERO` for 1000 shots.
23. Plot counts for `H @ ZERO`.
24. Write a README explaining the project.
25. Write a short comparison: Python-only simulator vs Qiskit.

## Git commit

```bash
git add .
git commit -m "Build Python-only mini quantum simulator"
```

---

# Priority checklist

By the end of this refresh, you should be comfortable with:

```text
NumPy arrays
Vectors
Matrices
Matrix multiplication
Complex numbers
Probability amplitudes
Measurement sampling
Shots and counts
Reusable functions
Matplotlib bar charts
One-qubit gate simulation
```

You do **not** need to prioritize these right now:

```text
Advanced DSA
Decorators
Generators
OOP deep dive
Pandas-heavy work
Advanced ML libraries
Web frameworks
```

---

# What to do after this 7-day refresh

Move into Qiskit:

```text
1. Create a QuantumCircuit
2. Apply H, X, Z gates
3. Measure qubits
4. Run simulations
5. Build a Quantum Random Number Generator
6. Build a Bell State circuit
```

Then move into PennyLane:

```text
1. Create a device
2. Create a QNode
3. Use RX, RY, RZ gates
4. Return expectation values
5. Compute gradients
6. Build a small quantum classifier
```

---

# Suggested LinkedIn update after this refresh

```text
I completed a focused Python refresh for quantum software development.

Instead of relearning Python from scratch, I focused on the concepts most useful for quantum computing:
- NumPy arrays
- Vectors and matrices
- Matrix multiplication
- Complex numbers
- Probability amplitudes
- Measurement sampling
- Matplotlib visualizations

I also built a small Python-only one-qubit simulator before moving deeper into Qiskit.

GitHub: your-repo-link

#Python #QuantumComputing #Qiskit #LearningInPublic
```
