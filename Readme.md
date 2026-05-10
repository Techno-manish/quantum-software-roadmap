# Quantum Software Development Setup Guide

This guide explains how to set up a local quantum software development environment for learning **Qiskit**, **PennyLane**, and practical quantum computing projects.

It is written for **Windows + Git Bash**, but most commands can be adapted for PowerShell, CMD, macOS, or Linux.

---

## 1. Required tools

Install these tools first:

- Python 3.12
- Git
- VS Code
- VS Code Python extension
- VS Code Jupyter extension

Recommended Python version:

```text
Python 3.12.x
```

Avoid using very new Python versions such as Python 3.14 for now because some scientific and quantum packages may not fully support them yet.

---

## 2. Install Python 3.12

Download Python 3.12 from:

```text
https://www.python.org/downloads/
```

During installation, select:

```text
Add python.exe to PATH
Install launcher for all users
```

After installation, close and reopen Git Bash.

Check installed Python versions:

```bash
py -0
```

Expected example:

```text
-V:3.14[-64] *
-V:3.12[-64]
```

If only Python 3.14 is visible, install Python 3.12 and reopen the terminal.

---

## 3. Create project folder

Go to your preferred location:

```bash
cd /d
mkdir quantum-software-roadmap
cd quantum-software-roadmap
```

Initialize Git:

```bash
git init
```

---

## 4. Create virtual environment

Use Python 3.12 explicitly:

```bash
py -3.12 -m venv quantum-env
```

Do not interrupt this command. Wait until it finishes.

---

## 5. Activate virtual environment in Git Bash

In Git Bash, use this command:

```bash
source quantum-env/Scripts/activate
```

Expected terminal prefix:

```text
(quantum-env)
```

Example:

```text
(quantum-env) pc@Manish MINGW64 /d/quantum-software-roadmap (main)
```

---

## 6. Important Git Bash path note

Do not activate the environment like this in Git Bash:

```bash
d:\quantum-software-roadmap\quantum-env\Scripts\activate
```

That is Windows CMD/PowerShell style and may fail in Git Bash.

Use this instead:

```bash
source quantum-env/Scripts/activate
```

---

## 7. Confirm correct Python version inside venv

After activation, run:

```bash
python --version
```

Expected:

```text
Python 3.12.x
```

---

## 8. Upgrade pip

```bash
python -m pip install --upgrade pip
```

---

## 9. Install required packages

```bash
pip install numpy matplotlib jupyterlab qiskit qiskit-aer qiskit-ibm-runtime pennylane scikit-learn
```

Packages used:

| Package | Purpose |
|---|---|
| numpy | Linear algebra, vectors, matrices |
| matplotlib | Plots and visualization |
| jupyterlab | Notebooks |
| qiskit | Quantum circuits and algorithms |
| qiskit-aer | Local quantum simulator |
| qiskit-ibm-runtime | IBM Quantum runtime access |
| pennylane | Quantum machine learning |
| scikit-learn | ML datasets and evaluation |

---

## 10. Save dependencies

```bash
pip freeze > requirements.txt
```

Other people can later recreate the environment using:

```bash
pip install -r requirements.txt
```

---

## 11. Create project structure

```bash
mkdir -p week-01-foundations week-02-qiskit-basics week-03-quantum-algorithms week-04-qiskit-runtime-hardware
mkdir -p week-05-pennylane-basics week-06-quantum-ml week-07-capstone week-08-polish-and-job-ready
mkdir -p projects/quantum-random-number-generator projects/bell-state-visualizer projects/grover-search-demo
mkdir -p projects/quantum-classifier-pennylane projects/final-capstone notes
```

Create notes files:

```bash
touch notes/quantum-basics.md notes/qiskit-notes.md notes/pennylane-notes.md notes/interview-notes.md
```

---

## 12. Create README.md

Create a `README.md` file:

```bash
touch README.md
```
---

## 13. Open project in VS Code

```bash
code .
```

Then select the Python interpreter:

```text
Ctrl + Shift + P
Python: Select Interpreter
./quantum-env/Scripts/python.exe
```

---

## 14. Test basic Qiskit import

Create a file:

```bash
touch testQiskitBasic.py
```

Add:

```python
from qiskit import QuantumCircuit

qc = QuantumCircuit(1, 1)
qc.h(0)
qc.measure(0, 0)

print(qc)
```

Run:

```bash
python testQiskitBasic.py
```

Expected: a text circuit diagram should print.

---

## 15. Test Qiskit Aer simulator

Create a file:

```bash
touch testQiskitAer.py
```

Add:

```python
from qiskit import QuantumCircuit
from qiskit_aer import AerSimulator

qc = QuantumCircuit(1, 1)
qc.h(0)
qc.measure(0, 0)

simulator = AerSimulator()
job = simulator.run(qc, shots=1000)
result = job.result()

print(result.get_counts())
```

Run:

```bash
python testQiskitAer.py
```

Expected output should be close to:

```text
{'0': 500, '1': 500}
```

The exact numbers will vary.

---

## 16. Test PennyLane

Create a file:

```bash
touch testPennylane.py
```

Add:

```python
import pennylane as qml
from pennylane import numpy as np


dev = qml.device("default.qubit", wires=1)


@qml.qnode(dev)
def circuit(theta):
    qml.RX(theta, wires=0)
    return qml.expval(qml.PauliZ(0))


theta = np.array(0.5, requires_grad=True)

print(circuit(theta))
print(qml.grad(circuit)(theta))
```

Run:

```bash
python testPennylane.py
```

Expected: two numeric values should print.

---

## 17. Start JupyterLab

```bash
jupyter lab
```

Create your first notebook:

```text
week-01-foundations/01_qubit_basics.ipynb
```

---

# Issues faced and solutions

## Issue 1: Virtual environment creation was interrupted

### Error

```text
KeyboardInterrupt
```

This happened while running:

```bash
python -m venv quantum-env
```

### Reason

The venv creation process was interrupted before it finished. This can leave a broken or incomplete `quantum-env` folder.

### Solution

Delete the broken environment:

```bash
rm -rf quantum-env
```

Then recreate it:

```bash
py -3.12 -m venv quantum-env
```

Wait until the command finishes.

---

## Issue 2: Wrong activation command in Git Bash

### Error

```text
bash: d:quantum-software-roadmapquantum-envScriptsactivate: command not found
```

### Wrong command

```bash
d:\quantum-software-roadmap\quantum-env\Scripts\activate
```

### Reason

Git Bash does not use Windows path syntax in the same way CMD or PowerShell does.

### Solution

Use Git Bash syntax:

```bash
source quantum-env/Scripts/activate
```

---

## Issue 3: Only Python 3.14 was installed

### Check command

```bash
py -0
```

### Output

```text
-V:3.14[-64] *   Python 3.14.4
```

### Reason

Only Python 3.14 was installed. Some quantum/scientific packages may not fully support it yet.

### Solution

Install Python 3.12, then create the virtual environment using:

```bash
py -3.12 -m venv quantum-env
```

---

## Issue 4: Qiskit Aer DLL error on Windows

### Error

```text
ImportError: DLL load failed while importing controller_wrappers: The specified module could not be found.
```

This happened while running:

```python
from qiskit_aer import AerSimulator
```

### Reason

`qiskit-aer` uses native compiled components. On Windows, this error often happens because required Microsoft Visual C++ runtime files are missing.

### Solution 1: Install Microsoft Visual C++ Redistributable

Download and install:

```text
https://aka.ms/vs/17/release/vc_redist.x64.exe
```

Install it, then restart your PC.

After restart:

```bash
cd /d/quantum-software-roadmap
source quantum-env/Scripts/activate
python -c "from qiskit_aer import AerSimulator; print('Aer OK')"
```

Expected:

```text
Aer OK
```

### Solution 2: Reinstall qiskit-aer

If the issue remains:

```bash
pip uninstall qiskit-aer -y
pip install --no-cache-dir qiskit-aer
```

Test again:

```bash
python -c "from qiskit_aer import AerSimulator; print('Aer OK')"
```

---

## Issue 5: SyntaxError after pasting multiple Python commands in one line

### Error

```text
SyntaxError: invalid syntax
```

### Problem example

```python
from qiskit import QuantumCircuitfrom qiskit_aer import AerSimulatorqc = QuantumCircuit(1, 1)
```

### Reason

Python statements need line breaks or semicolons. Do not paste multiple statements merged together.

### Correct format

```python
from qiskit import QuantumCircuit
from qiskit_aer import AerSimulator

qc = QuantumCircuit(1, 1)
qc.h(0)
qc.measure(0, 0)

simulator = AerSimulator()
job = simulator.run(qc, shots=1000)
result = job.result()

print(result.get_counts())
```

Best practice: write code in `.py` files or Jupyter notebooks instead of pasting many lines into the Python shell.

---

## Issue 6: Git shows 10,000+ files to add

### Reason

Git is seeing the virtual environment folder:

```text
quantum-env/
```

This folder contains thousands of package files and should not be committed.

### Solution: create `.gitignore`

Create `.gitignore`:

```bash
touch .gitignore
```

Add:

```gitignore
# Python virtual environments
quantum-env/
venv/
.env/

# Python cache
__pycache__/
*.pyc
*.pyo
*.pyd

# Jupyter
.ipynb_checkpoints/

# OS files
.DS_Store
Thumbs.db

# VS Code local settings
.vscode/

# Python build files
build/
dist/
*.egg-info/
```

If files were already staged, unstage them:

```bash
git reset
```

Then add files again:

```bash
git add .
```

Check:

```bash
git status
```

You should not see `quantum-env/` in the staged files.

---

# Other possible issues and fixes

## Problem: `python is not recognized`

### Solution

Use:

```bash
py --version
```

If `py` works but `python` does not, Python is not properly added to PATH.

Fix by reinstalling Python and selecting:

```text
Add python.exe to PATH
```

---

## Problem: `py -3.12` does not work

### Solution

Check installed versions:

```bash
py -0
```

If Python 3.12 is not listed, install Python 3.12.

---

## Problem: virtual environment does not activate in PowerShell

### Error

```text
running scripts is disabled on this system
```

### Solution

Run PowerShell as normal user and execute:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Then activate:

```powershell
.\quantum-env\Scripts\Activate.ps1
```

For Git Bash, use:

```bash
source quantum-env/Scripts/activate
```

---

## Problem: `jupyter` command not found

### Solution

Make sure venv is active:

```bash
source quantum-env/Scripts/activate
```

Install JupyterLab:

```bash
pip install jupyterlab
```

Run using Python module form:

```bash
python -m jupyter lab
```

---

## Problem: VS Code uses wrong Python interpreter

### Solution

In VS Code:

```text
Ctrl + Shift + P
Python: Select Interpreter
```

Select:

```text
./quantum-env/Scripts/python.exe
```

Then reopen the terminal in VS Code.

---

## Problem: packages installed globally instead of inside venv

### Check

```bash
where python
```

The first path should include:

```text
quantum-env\Scripts\python.exe
```

### Solution

Activate the environment first:

```bash
source quantum-env/Scripts/activate
```

Then install packages:

```bash
pip install package-name
```

---

## Problem: Git push asks for username/password

GitHub no longer accepts normal account passwords for Git over HTTPS.

### Solutions

Use one of these:

1. GitHub Personal Access Token
2. GitHub CLI
3. SSH key

For beginners, HTTPS + Personal Access Token is usually easiest.

---

# Recommended first commit

After setup is complete:

```bash
git add .
git commit -m "Initial quantum software development setup"
```

If remote is already added:

```bash
git push
```

If remote is not added:

```bash
git remote add origin https://github.com/YOUR_USERNAME/quantum-software-roadmap.git
git branch -M main
git push -u origin main
```

Replace `YOUR_USERNAME` with your GitHub username.

---

# Final setup checklist

```text
Python 3.12 installed
Git installed
VS Code installed
Project folder created
Git initialized
Virtual environment created
Virtual environment activated
Packages installed
requirements.txt created
.gitignore created
Qiskit basic test passed
Qiskit Aer test passed
PennyLane test passed
JupyterLab opened
Initial commit pushed to GitHub
```

---

# Next step after setup

Start with:

```text
week-01-foundations/01_qubit_basics.ipynb
```

Suggested first topic:

```text
Classical bit vs qubit
|0⟩ and |1⟩
Superposition
Measurement
Probability
```
