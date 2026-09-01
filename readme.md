# Titanic Data Quality Validations

This project contains a Jupyter Notebook designed to execute comprehensive data quality checks on a subset of the Titanic dataset[cite: 2]. The notebook outlines a structured workflow for identifying and handling common data anomalies, including missing values, type mismatches, string inconsistencies, and non-informative columns[cite: 2].

## Repository Content

*   **Notebook (`data_quality_checks.ipynb`)**: The primary Python script containing the step-by-step data validation workflow[cite: 2].
*   **Dataset (`titanic_dataset.csv`)**: The source data utilized for the analysis[cite: 2].

## Step-by-Step Workflow

### 1. Set Up & Initialization
*   Installs and upgrades `pip`, followed by the installation of the core analytical packages `pandas` and `numpy`[cite: 2].
*   Imports the libraries and sets the pandas display option to show a maximum of 50 columns[cite: 2].

### 2. Loading the Dataset
*   Loads `titanic_dataset.csv` into a pandas DataFrame[cite: 2].
*   Validates the initial dimensions of the dataset, resulting in 782 rows and 15 columns[cite: 2].
*   Executes preliminary exploratory commands including `.head()`, `.shape`, `.info()`, `.describe()`, and `.tail()` to understand the initial state of the data[cite: 2].

### 3. Simulating Data Issues
To demonstrate robust data cleaning techniques, the notebook intentionally introduces several problematic columns[cite: 2]:
*   **Unique ID:** Generates a synthetic `passenger_id` column using a sequential numpy array[cite: 2].
*   **Constant Column:** Creates a `constant_column` where all rows are assigned the exact same integer value of 1[cite: 2].
*   **Dirty Strings:** Copies the `embark_town` column into a new `embark_town_dirty` column and applies destructive transformations to a sample of rows, including uppercase conversion, trailing/leading whitespaces, and hardcoded "unknown" strings[cite: 2].

### 4. Comprehensive Data Validations
The core of the notebook focuses on systematically identifying data issues[cite: 2]:

*   **4.1 Basic Overview:** Retrieves the expanded shape (18 columns) and calculates unique counts and descriptive statistics across the entire DataFrame[cite: 2].
*   **4.2 Missing Values Summary:** Computes the total count and percentage of missing values (NaNs) for every column, compiling the results into a dedicated Summary DataFrame[cite: 2].
*   **4.3 Duplicates Check:** Evaluates the dataset for completely duplicated rows, confirming 0 duplicate records[cite: 2].
*   **4.4 Data Type Validations:** Defines an expected schema dictionary and programmatically compares it against actual DataFrame types[cite: 2]. It successfully identifies type mismatches (e.g., `sex` loaded as string instead of category) and casts `pclass` to an `int64` type[cite: 2].
*   **4.5 Constant and Quasi-Constant Columns:** Identifies columns with zero variance (`constant_column`) by checking if the unique count equals 1[cite: 2]. It also includes logic to flag quasi-constant columns where a single value constitutes more than 95% of the data[cite: 2].
*   **4.6 1D-Like Columns:** Scans for columns where the number of unique values matches the total number of rows in the DataFrame, accurately flagging the simulated `passenger_id` column[cite: 2].
*   **4.7 String Inconsistencies:** Selects all string columns and resolves the injected messiness[cite: 2]. It creates a cleaned version (`embark_town_clean`) by stripping whitespace, standardizing to lowercase, and replacing the string "unknown" with `np.nan`[cite: 2].
*   **4.8 High Null Columns:** Filters the missing values summary to flag any feature missing more than 40% of its data, which correctly isolates the `deck` column at ~76.9% missing[cite: 2].
*   **4.9 High Zero Columns (Numeric):** Calculates the proportion of absolute zero values across all numerical columns[cite: 2]. It highlights features like `parch` (~76.7% zeros) and `sibsp` (~67.6% zeros)[cite: 2].

## Usage Requirements
*   Python 3 environment capable of running Jupyter Notebooks[cite: 2].
*   Required packages: `numpy` and `pandas`[cite: 2].