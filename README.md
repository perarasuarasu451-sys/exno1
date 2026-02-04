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
import pandas as pd
science=pd.read_csv("/content/SAMPLEIDS.csv")
science
```

<img width="1057" height="710" alt="image" src="https://github.com/user-attachments/assets/b8493b11-34ff-48a2-b169-0b9308452a20" />

```
science.head()
```
<img width="1000" height="203" alt="image" src="https://github.com/user-attachments/assets/ecbe335b-f53c-41ce-89fc-e1ea35d98c71" />

```
science.tail()
```

<img width="1020" height="202" alt="image" src="https://github.com/user-attachments/assets/7881ea9f-a092-442f-9377-48025da883c5" />

```
science.info()
```

<img width="780" height="339" alt="image" src="https://github.com/user-attachments/assets/2921a94b-3491-4fe5-8eed-61913ff19c98" />

```
science.describe()
```

<img width="913" height="291" alt="image" src="https://github.com/user-attachments/assets/ce988410-b2ac-4ef0-9b5d-6e8b48dadd10" />

```
science.isnull().sum()
```
<img width="1137" height="452" alt="image" src="https://github.com/user-attachments/assets/9d8f0240-1b47-486e-9f24-3eac67290ac1" />

```
science.notnull()
```

<img width="1156" height="696" alt="image" src="https://github.com/user-attachments/assets/e33159f7-e025-42e0-900c-9eba20adf331" />

```
science.dropna()
```
<img width="1000" height="441" alt="image" src="https://github.com/user-attachments/assets/3980b862-c154-4ea3-bb28-cddc12684fcd" />

```
science.fillna(5)
```

<img width="1081" height="695" alt="image" src="https://github.com/user-attachments/assets/cab62bb5-727b-4d0d-8330-6eecc9c14730" />

```
science.fillna(method='ffill')
```
<img width="1407" height="735" alt="image" src="https://github.com/user-attachments/assets/b72e70b5-3e14-442c-ab8d-26408317851a" />


```
science.fillna(method='bfill')
```

<img width="1409" height="737" alt="image" src="https://github.com/user-attachments/assets/ae8a8677-9d82-45fa-86ca-81a072c3796e" />


```
science.fillna({'GENDER':'MALE','NAME':'SRI'})
```

<img width="1423" height="695" alt="image" src="https://github.com/user-attachments/assets/d2a1cb86-3dfe-4c49-b9ee-5714639c2280" />



```
ir=pd.read_csv("/content/iris.csv")
ir
```


<img width="878" height="415" alt="image" src="https://github.com/user-attachments/assets/55d8cddc-8f97-40c3-baf4-b6a19a11eca3" />


```
ir.head()
```

<img width="650" height="235" alt="image" src="https://github.com/user-attachments/assets/59fcc911-7ab3-4051-898e-28e718b99f5d" />

```
ir.tail()
```


<img width="769" height="193" alt="image" src="https://github.com/user-attachments/assets/e11a7871-d154-4f16-8c9a-0e50faf28341" />

```
ir.info()
```


<img width="763" height="210" alt="image" src="https://github.com/user-attachments/assets/6bcc9cb4-2a5c-4d5c-bf4f-a19f96c1a88d" />

```

ir.describe()
```
<img width="940" height="317" alt="image" src="https://github.com/user-attachments/assets/ea2ae5ae-1439-4e9d-a9a0-429e4afd194f" />

```
ir.isnull().sum()
```
<img width="567" height="225" alt="image" src="https://github.com/user-attachments/assets/63fa042d-8500-41f9-9f96-98f5b70e6a85" />


```
ir.isnull().any()
```
<img width="466" height="211" alt="image" src="https://github.com/user-attachments/assets/065afded-b426-4334-b93d-b88c69e8394b" />


```
ir.notnull()
```
<img width="648" height="407" alt="image" src="https://github.com/user-attachments/assets/63172f32-8202-4d2f-9e0d-415e9197821d" />


```
ir.dropna()
```
<img width="748" height="408" alt="image" src="https://github.com/user-attachments/assets/0624991b-c84f-4c04-80b5-6cbcd804c45c" />


```
ir.dropna(axis=1)
```
<img width="732" height="399" alt="image" src="https://github.com/user-attachments/assets/1112fbdc-cdb4-404b-a1a5-b679655686ce" />


```
ir.fillna(8)
```

<img width="693" height="411" alt="image" src="https://github.com/user-attachments/assets/e736a8c4-028e-424c-a057-389b361b110c" />

```
ir.fillna(method='ffill')
```
<img width="1398" height="445" alt="image" src="https://github.com/user-attachments/assets/ec51edbc-64a6-4f8e-b7b5-235500e8e202" />

```
ir.fillna(method='bfill')
```
<img width="1455" height="436" alt="image" src="https://github.com/user-attachments/assets/ba1737c8-a38b-4fb7-bcb5-cfeb34ed703e" />


```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
<img width="986" height="453" alt="image" src="https://github.com/user-attachments/assets/44460e1a-3f84-4918-a0cc-95d20826bf72" />

```
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
(IQR)=Q3-Q1
print(IQR)
```
<img width="801" height="32" alt="image" src="https://github.com/user-attachments/assets/f3e0cda7-a30c-4fec-93be-753085852d63" />

```
ran=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
```

<img width="572" height="198" alt="image" src="https://github.com/user-attachments/assets/a923e41e-df83-44e2-b2f1-1b69c8cb21cb" />

```
sns.boxplot(x='sepal_width',data=ran)
```

<img width="748" height="644" alt="image" src="https://github.com/user-attachments/assets/a4ef9627-9a9b-419d-a7fe-f9a73e5b5f6c" />

```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir['petal_length']))
z
```
<img width="1137" height="523" alt="image" src="https://github.com/user-attachments/assets/87441152-797f-43c4-a4a7-57f1b03a0d53" />


```
ir1=ir[z<3]
ir1
```
<img width="810" height="407" alt="image" src="https://github.com/user-attachments/assets/11fd49d8-35eb-48a1-b938-8765016f0c0e" />

RESULT:

Data Cleaning Process is verified
