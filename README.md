# QUESTION 1 (Software Design and Implementation)

## Metadata

Language: Python

Environment Setup:

1. Create new virtual environment with VSC and venv
2. Activate with .venv\scripts\activate
3. Install required packages with pip install --target=Lib\site-packages pandas 

Packages:
- pandas


## Understanding and Assumptions

1. Use "Canonical Models" as the base data to match entries from "Car Models 1" and "Car Models 2".
2. Match even if missing spaces cause it to seem different ("G80 EV" vs "G80EV").
3. Match even if the different model names refer to the same model ("HYUN, ACCE" vs "HYUN, ACCENT").
4. However, duplicates if any will be dropped.
5. Entries follow the order of "Canonical Models".