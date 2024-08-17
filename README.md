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
data=pd.read_csv("SAMPLEIDS.csv")
data
```

![image](https://github.com/user-attachments/assets/48f86756-6760-449e-a6c0-869312aaafc1)

```
data.head()
```

![image](https://github.com/user-attachments/assets/fa717b05-3485-4a67-8ca1-c63548ea7711)

```
data.tail()
```

![image](https://github.com/user-attachments/assets/a8cb7cd3-7955-48d6-b17f-deb9125ac5e2)

```
data.isnull().sum()
```

![image](https://github.com/user-attachments/assets/a8cf5ce3-63ee-443c-b1e9-89bca952a970)

```
data.isnull().any()
```

![image](https://github.com/user-attachments/assets/cd6f6628-1b14-4e85-be65-2146bc4f42b8)

```
data.fillna(0)
```

![image](https://github.com/user-attachments/assets/d7eeab21-b8a0-4b98-a765-33eefabb83a8)

```
data.fillna(method = 'ffill')
```

![image](https://github.com/user-attachments/assets/ecb86f73-94c1-42ab-b644-6240b3b5f0f3)

```
data.fillna(method = 'bfill')
```

![image](https://github.com/user-attachments/assets/bdaa471b-a34a-473b-8123-d55cfb1b6ff7)

```
data.dropna()
```

![image](https://github.com/user-attachments/assets/a72678b7-2d1f-43d9-b05b-d7d7f64b5095)

```
data.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```

![image](https://github.com/user-attachments/assets/c371fdc2-b8b4-4b09-b614-42c474b39985)

```
ir=pd.read_csv("iris.csv")
ir
```

![image](https://github.com/user-attachments/assets/765aa087-230c-4b76-a919-e3422a77476b)

```
ir.describe()
```

![image](https://github.com/user-attachments/assets/09ed0df9-e434-42d9-8ca8-640fd43bd56e)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

![image](https://github.com/user-attachments/assets/df65ea90-f472-4698-bdb3-af65acaa061a)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```

![image](https://github.com/user-attachments/assets/eb682e51-b5cb-415d-ba13-ddc8e8df8c53)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```

![image](https://github.com/user-attachments/assets/553304e1-6aab-46ea-904a-b41960a87e26)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```

![image](https://github.com/user-attachments/assets/8945c0e9-943c-4898-8c59-3365bd1ab18a)

```
sns.boxplot(x='sepal_width',data=delid)
```

![image](https://github.com/user-attachments/assets/7a2f1cce-58c9-4f9e-b49c-ac01633ccc98)

```
import matplotlib.pyplot as plt
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```

![image](https://github.com/user-attachments/assets/3f2a8e3f-86f7-48e8-a657-de3c621ed847)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iq
```

![image](https://github.com/user-attachments/assets/65431a2c-2511-4a44-aea8-44aad23b5a94)

```
low = q1 - 1.5*iqr
low
```

![image](https://github.com/user-attachments/assets/20fc6fd5-4a63-44d2-8435-a63ca36f9bcf)

```
high = q3 + 1.5*iqr
high
```

![image](https://github.com/user-attachments/assets/18f49ac5-9582-4858-8dcc-8bcf40e52045)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

![image](https://github.com/user-attachments/assets/53df9d71-8076-47db-adde-d25c23b15b1c)

```
z = np.abs(stats.zscore(df['height']))
z
```

![image](https://github.com/user-attachments/assets/3cf0f44c-8434-4b58-8141-4b7291c9576d)

```
df1 = df[z<3]
df1
```

![image](https://github.com/user-attachments/assets/0635e6c2-8011-4a80-982b-3d5b001a1d9c)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
