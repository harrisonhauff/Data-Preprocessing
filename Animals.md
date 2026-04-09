# 🐾 Unstructured Animal Data – Data Cleaning & Preprocessing Pipeline

## Overview
This project focuses on transforming a highly unstructured and inconsistent animal observation dataset into a clean, analysis-ready format using **Python (Pandas)**.

The raw dataset contained severe formatting issues, missing values, and inconsistent categorical data, simulating real-world data quality challenges.

---

## Key Challenges
- Entire dataset stored in a **single column** due to incorrect delimiter usage
- Mixed and inconsistent delimiters (`;`)
- Corrupted rows with missing structured values (e.g. `;;;;;;;;;`)
- Inconsistent categorical values (e.g. `"European bison™"`, `"European bisson"`)
- Missing values across multiple features (weight, length, gender, country)
- Incorrect or ambiguous country labels (e.g. `"PL"`, `"CC"`, `"Australia"` vs `"Austria"`)

---

## Data Processing Pipeline

### 1. Data Restructuring
- Parsed raw CSV using correct delimiter (`sep=';'`)
- Converted single-column data into a structured **tabular DataFrame**

### 2. Categorical Cleaning & Standardisation
- Normalised animal species using pattern matching:
  - Variants of *European Bison*, *Lynx*, *Red Squirrel*, *Hedgehog*
- Standardised country names:
  - `"PL"` → `"Poland"`
  - `"Czech"` / `"CZ"` / `"CC"` → `"Czech Republic"`
  - Corrected mislabelled entries (e.g. `"Australia"` → `"Austria"`)

### 3. Geospatial Validation
- Used **latitude and longitude** to validate and correct country assignments
- Identified incorrectly labelled regions based on geographic coordinates

### 4. Missing Data Handling
Applied **context-aware imputation strategies** instead of naive filling:

- **Animal Type Inference**
  - Classified missing animal types using weight thresholds

- **Numerical Imputation**
  - Imputed missing `Weight` and `Body Length` using **group-wise means** (by animal type and gender)

- **Gender Inference**
  - Inferred missing or ambiguous gender values using:
    - Weight distributions
    - Body length characteristics

- **Country Filtering**
  - Removed records where country could not be reliably determined

### 5. Feature Reduction
- Dropped irrelevant columns (e.g. `Animal code` with 100% missing values)

---

## Tools & Technologies
- Python
- Pandas
- NumPy

---

## Outcome
- Transformed raw, unstructured data into a **clean dataset (999 records × 10 features)**
- Eliminated categorical inconsistencies
- Reduced missing values through informed imputation
- Produced a dataset suitable for **analysis or machine learning tasks**

---

## Key Skills Demonstrated
- Data cleaning and preprocessing
- Handling messy, real-world datasets
- Feature engineering and inference
- Geospatial data validation
- Pandas-based data manipulation
- Problem-solving with domain assumptions

---

## Future Improvements
- Implement a reusable **data cleaning pipeline (modular functions)**
- Add validation metrics (e.g. missing value reduction, consistency checks)
- Perform exploratory data analysis (EDA) and visualisation
- Integrate with a downstream machine learning task
