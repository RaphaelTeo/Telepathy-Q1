# QUESTION 1 (Software Design and Implementation)

## Metadata

Language: Python

Environment Setup:

1. Create new virtual environment with venv
2. Activate with <venv name>\scripts\activate
3. Install required packages
    - pandas
    - openpyxl


## Submission (main)

This interpretation takes **"Canonical Models" as the base** and supplements it with **additional data from the "Car Models [X]" sheets** where possible, then tries to **fill in any data gaps**. As **"Car Models 2"** does not provide any additional data, we **discard** it.

Where there is missing data, the code will try to **fill in the missing data based on the other rows with similar data** (e.g. for missing Makes, it refers to the Makes of other rows where the Canoncial Make is the same). If there are multiple options (e.g. HYD vs HYUN or EXCE vs EXCEL), it **chooses the one with more entries and standardises all the rows**. If no data can be found at all, it simply refers to the available data in the Canonical Models.

After which, the columns are formatted to make them match that of the desired output.


## Submission (Interpretation 2)

This interpretation **augments the 2 Car Models sheets using the Canonical Models**. In the context of a sample scenario, we assume that a client has provided us with 2 lists of car models (e.g. "Car Models [X]"), and we need to **correct their entries to match what we have in our official database ("Canonical Models")**. Hence, we **take each "Car Models [X]" sheet** as the base of comparison and try to **augment its data using "Canonical Models"**.

"Car Models 2", however, is missing the full spelling of "Make", and we cannot eliminate the possibility that different Makes use the same Model names, which affects the reliability of the key used to compare between sheets. Therefore, while "Car Models 1" can be augmented directly with "Canonical Models", **"Car Models 2" needs to use the output from the previous step ("df_m1_m2_merged in the code")**.

2 sheets are produced, one for "Car Models 1" and one for "Car Models 2".


## Considerations and Issues Encountered

1. **Missing spaces and capitalisation** are handled by using .lower() and .strip().
2. When creating the key values, the **strings were forced to lowercase and stripped** (remove leading and trailing spaces). Format validation (string) is not required here since it would throw an error if the values were not strings, and it can be forced to be strings via str(x) if needed.
3. **Extra spaces("G80 EV" vs "G80EV") are noted** but we will clarify with the customer before assuming that they are duplicates. If needed, they can be handled by adding the parameter `replace(" ", "")` when making the keys.
4. There was an **extra whitespace** for " model" in the "Canonical Models" headers.