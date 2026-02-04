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

<img width="833" height="256" alt="Screenshot 2026-02-04 113528" src="https://github.com/user-attachments/assets/b5b44478-9d56-470a-aef5-aae71dec03f0" />

<img width="821" height="567" alt="Screenshot 2026-02-04 113604" src="https://github.com/user-attachments/assets/cfb0e0a0-6bbe-4f37-bcd7-e5581cdb2d34" />

<img width="521" height="420" alt="Screenshot 2026-02-04 113613" src="https://github.com/user-attachments/assets/37fc2dea-cb02-4c26-a94b-ae25dbd4930e" />

<img width="838" height="349" alt="Screenshot 2026-02-04 113622" src="https://github.com/user-attachments/assets/da2c2dc8-5050-41bd-8ad7-2126dfc60c49" />

<img width="372" height="644" alt="Screenshot 2026-02-04 113634" src="https://github.com/user-attachments/assets/ca51695f-1c4c-48ef-bb3a-7acc517937b3" />

<img width="401" height="348" alt="Screenshot 2026-02-04 113648" src="https://github.com/user-attachments/assets/af476d40-a16b-48a4-983c-cfe5c8cdb7db" />


# Result

<img width="786" height="598" alt="Screenshot 2026-02-04 111525" src="https://github.com/user-attachments/assets/3eb7e9c4-7ef3-4dd1-8d65-851dc82b1ef7" />

<img width="797" height="595" alt="Screenshot 2026-02-04 111550" src="https://github.com/user-attachments/assets/e1416ba4-595b-4bd9-91d9-ef0db160f89f" />

<img width="800" height="598" alt="Screenshot 2026-02-04 111602" src="https://github.com/user-attachments/assets/40f69233-2b9e-46d8-8bda-1b3b3249d42f" />

<img width="792" height="593" alt="Screenshot 2026-02-04 111612" src="https://github.com/user-attachments/assets/d4117445-1e9c-49a8-a7b9-3a0627d64c94" />

<img width="799" height="597" alt="Screenshot 2026-02-04 111625" src="https://github.com/user-attachments/assets/90c6d8bd-3e94-4c82-81d9-cd390e4077f7" />



