# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
# ==================================================
# EXPERIMENT 01
# DATA CLEANING & OUTLIER DETECTION USING PYTHON
# ==================================================

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import os

print("\n================ EXPERIMENT 01 ================\n")

# --------------------------------------------------
# STEP 1: LOAD DATASET
# --------------------------------------------------
print("STEP 1: Loading Dataset")

print("\nCurrent Working Directory:")
print(os.getcwd())

print("\nFiles in Directory:")
print(os.listdir())

file_name = "Data_set.csv"

if file_name not in os.listdir():
    print(f"\nERROR: {file_name} not found")
    exit()

df = pd.read_csv(file_name)

print("\nDataset Loaded Successfully")

# --------------------------------------------------
# STEP 2: DISPLAY DATASET
# --------------------------------------------------
print("\nSTEP 2: Displaying Dataset")

print("\nFirst 10 Records:")
print(df.head(10))

print("\nDataset Shape (Rows, Columns):")
print(df.shape)

print("\nColumn Names:")
print(df.columns)

# --------------------------------------------------
# STEP 3: DATASET INFORMATION
# --------------------------------------------------
print("\nSTEP 3: Dataset Information")
print(df.info())

# --------------------------------------------------
# STEP 4: STATISTICAL SUMMARY
# --------------------------------------------------
print("\nSTEP 4: Statistical Summary")
print(df.describe(include='all'))

# --------------------------------------------------
# STEP 5: MISSING VALUE ANALYSIS
# --------------------------------------------------
print("\nSTEP 5: Missing Value Analysis")

print("\nMissing Values Before Cleaning:")
print(df.isnull().sum())

numeric_cols = df.select_dtypes(include=np.number).columns

df[numeric_cols] = df[numeric_cols].fillna(df[numeric_cols].mean())

df = df.drop_duplicates()

print("\nMissing Values After Cleaning:")
print(df.isnull().sum())

print("\nDataset Shape After Removing Duplicates:")
print(df.shape)

# --------------------------------------------------
# STEP 6: OUTLIER DETECTION USING IQR
# --------------------------------------------------
print("\nSTEP 6: Outlier Detection Using IQR Method")

Q1 = df[numeric_cols].quantile(0.25)
Q3 = df[numeric_cols].quantile(0.75)
IQR = Q3 - Q1

outliers = ((df[numeric_cols] < (Q1 - 1.5 * IQR)) |
            (df[numeric_cols] > (Q3 + 1.5 * IQR)))

print("\nOutliers Count in Each Column:")
print(outliers.sum())

df_cleaned = df[~outliers.any(axis=1)]

print("\nDataset Shape After Removing Outliers:")
print(df_cleaned.shape)

# --------------------------------------------------
# STEP 7: VISUALIZATION
# --------------------------------------------------
print("\nSTEP 7: Boxplot Visualization")

for col in numeric_cols:
    plt.figure()
    sns.boxplot(x=df[col])
    plt.title(f"Boxplot of {col}")
    plt.show()

# --------------------------------------------------
# FINAL OUTPUT
# --------------------------------------------------
print("\n=============== RESULT ===============")
print("Data cleaning and outlier detection were successfully performed.")

print("\n=============== END OF EXPERIMENT 01 ===============")

```
<img width="833" height="256" alt="Screenshot 2026-02-04 113528" src="https://github.com/user-attachments/assets/61aae008-da92-4b61-9306-f20cd489e8a1" />

<img width="821" height="567" alt="Screenshot 2026-02-04 113604" src="https://github.com/user-attachments/assets/fbaf15e8-aa7c-4da7-9458-6644f81584f8" />

<img width="521" height="420" alt="Screenshot 2026-02-04 113613" src="https://github.com/user-attachments/assets/0e76edb0-3fb4-45f8-bec8-90b790001aa7" />

<img width="838" height="349" alt="Screenshot 2026-02-04 113622" src="https://github.com/user-attachments/assets/3cc18b7f-99a5-44dd-93e2-0b30510f7a0f" />

<img width="372" height="644" alt="Screenshot 2026-02-04 113634" src="https://github.com/user-attachments/assets/36458adb-7aeb-498b-a469-109167ad8601" />

<img width="401" height="348" alt="Screenshot 2026-02-04 113648" src="https://github.com/user-attachments/assets/b339fab6-d108-4787-a10f-5874c65e22b0" />

# Result
<img width="786" height="598" alt="Screenshot 2026-02-04 111525" src="https://github.com/user-attachments/assets/c82ce990-2c30-431b-8d78-44f062d426bc" />

<img width="797" height="595" alt="Screenshot 2026-02-04 111550" src="https://github.com/user-attachments/assets/ffa97f1c-39c1-4c3e-9a17-0f357fa7459d" />

<img width="800" height="598" alt="Screenshot 2026-02-04 111602" src="https://github.com/user-attachments/assets/ebeee3da-f0c7-491e-8c8b-533e14a4c057" />

<img width="792" height="593" alt="Screenshot 2026-02-04 111612" src="https://github.com/user-attachments/assets/bc8367c8-2879-41a9-b937-d393de1002b6" />

<img width="799" height="597" alt="Screenshot 2026-02-04 111625" src="https://github.com/user-attachments/assets/0142f550-4c7d-428b-9246-599aa783db53" />




Data Cleaning Process is verified
