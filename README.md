## 🛠 How to Use

Requirement: Ensure trained_names.txt (containing 1,000 names) is in the root directory.

Environment: Designed for Google Colab with T4 GPU support.

Execution:

Run the Task-1 cells to initialize model classes.

Use the Hyperparameter Comparison block to trigger the grid search across different model variants.

View the generated DataFrames for final metric reporting.


## 🔍 Qualitative Analysis

Realism: Vanilla RNN produced the most "Indian-sounding" names (e.g., Vimyra, Riprisha) but failed to create new ones without high temperature settings.

Failure Modes: * BLSTM: Characterized by "Panic Termination," where names were cut off prematurely (A, Nn).

Attention: Occasionally suffered from "Mode Collapse" or repetitive character loops (Mimvmimi) due to sharp attention weights.
