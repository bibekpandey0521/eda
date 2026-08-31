# Titanic Data Quality Checks Project

This repository contains a Jupyter Notebook (`data_quality_checks.ipynb`) dedicated to loading, modifying, and performing rigorous data quality validations on the Titanic dataset[cite: 1]. The notebook acts as a step-by-step guide to identifying common data anomalies such as missing values, incorrect data types, and formatting inconsistencies[cite: 1].

## Repository Contents

*   `data_quality_checks.ipynb`: The main notebook containing all executable Python code[cite: 1].
*   `titanic_dataset.csv`: The primary dataset required to run the analysis (must be located in the same directory as the notebook)[cite: 1].
*   `requirements.txt`: The required Python packages for this project.

## Step-by-Step Notebook Breakdown

The `data_quality_checks.ipynb` notebook is structured into four primary sections[cite: 1]:

### 1. Set Up
*   Installs the required Python packages (`pandas` and `numpy`) and upgrades `pip` via magic commands[cite: 1].
*   Imports the libraries and configures `pandas` to display a maximum of 50 columns to improve data readability[cite: 1].

### 2. Load the Dataset
*   Loads the `titanic_dataset.csv` into a pandas DataFrame[cite: 1].
*   Performs initial exploratory data analysis (EDA) by checking the DataFrame's dimensions (782 rows, 15 columns), previewing the first and last five rows, checking non-null counts via `.info()`, and generating basic descriptive statistics using `.describe()`[cite: 1].

### 3. Adding Columns for Demonstrating Data Issues
This section deliberately injects "dirty" data to simulate real-world data engineering scenarios[cite: 1]:
*   **Dirty Categoricals:** Creates a new column named `embark_town_dirty`[cite: 1]. It samples 6 non-missing rows and applies problematic transformations: converting strings to uppercase, injecting leading and trailing whitespaces, and replacing values with the string "unknown"[cite: 1].
*   **Unique Identifiers:** Generates a synthetic `passenger_id` column using a sequential `numpy` array from 1 to the total length of the dataset[cite: 1].
*   **Constant Columns:** Injects a `constant_column` where every row contains the exact same integer value (`1`)[cite: 1].

### 4. Data Quality Validations
The core of the notebook focuses on executing data quality checks[cite: 1]:

*   **4.1 Basic Dataset Overview:** Retrieves the new DataFrame shape (now 18 columns) and calculates the number of unique values for every column using `.nunique()`[cite: 1]. It also generates a comprehensive statistical summary covering both categorical and numerical columns[cite: 1].
*   **4.2 Missing Values Summary:** Computes the total count and the exact percentage of missing values (NaNs) for each feature[cite: 1]. The results are compiled into a separate, sorted Summary DataFrame highlighting columns with the highest missing data rates (e.g., `deck` and `age`)[cite: 1].
*   **4.3 Duplicates:** Scans the dataset for perfectly duplicated rows, outputting a count (yielding 0 duplicates in this dataset)[cite: 1].
*   **4.4 Data Type Validations:** Compares the actual `pandas` data types against a predefined schema dictionary (`expected_types`)[cite: 1]. The schema expects columns like `sex` and `embark_town` to be `category` types, and `age` to be `float64`[cite: 1]. It includes type coercion steps, such as casting the `pclass` column to `int64`[cite: 1].
*   **4.5 Constant and Quasi-Constant Columns:** Programmatically searches the DataFrame for columns that provide no variance[cite: 1]. By checking if `nunique == 1`, it successfully flags the artificially created `constant_column`[cite: 1]. It also begins setting up logic to detect quasi-constant columns by inspecting frequency counts[cite: 1].

## Usage

1. Ensure Python 3 is installed.
2. Install the required dependencies using the command: `pip install -r requirements.txt`
3. Place `titanic_dataset.csv` in the root directory.
4. Execute `data_quality_checks.ipynb` sequentially from top to bottom.