# Data Quality Checks Demonstration[cite: 1]

This repository contains a Jupyter Notebook named `data_quality_checks.ipynb` that demonstrates how to load data, perform basic exploration, and intentionally introduce data quality issues for practice or testing[cite: 1].

## Overview[cite: 1]

The notebook works with a local `titanic_dataset.csv` file and performs the following steps[cite: 1]:

* **Setup**: Installs and imports necessary data manipulation libraries (`pandas` and `numpy`)[cite: 1].
* **Data Loading**: Loads the Titanic dataset (which initially contains 782 rows and 15 columns) into a pandas DataFrame[cite: 1].
* **Exploration**: Uses standard pandas functions like `.head()`, `.shape`, `.info()`, and `.describe()` to inspect the data[cite: 1].
* **Data Manipulation**: Adds standard columns like `passenger_id` and a `constant_column`[cite: 1]. 
* **Simulating Dirty Data**: Creates an `embark_town_dirty` column and randomly injects messy formatting, such as uppercase strings, extra whitespace, and "unknown" values, to simulate real-world data issues[cite: 1].

## Requirements[cite: 1]

To run the code, you will need[cite: 1]:
* Python 3[cite: 1]
* `pandas`[cite: 1]
* `numpy`[cite: 1]

*Note: The notebook includes `%pip install` commands in the first few cells to automatically set up these dependencies for you[cite: 1].*

## Files[cite: 1]

* `data_quality_checks.ipynb`: The main notebook containing all the setup and data manipulation code[cite: 1].
* `titanic_dataset.csv`: The dataset needed to run the notebook successfully[cite: 1].