# Exno:1
Data Cleaning Process

# Coding and Output

### Developed by: Pragadeeswaran L
### Reg.No: 212223240120

# AIM :-
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation :-
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm :-
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers


# Data Cleaning :-
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/0260abd1-88a8-4113-b4f1-ea1dc838442e)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/1cd6e434-f020-413a-a69c-c44fca2a2708)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/7f1b2882-a6a1-4fca-94c2-a980855879b7)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/b81e0f1b-138f-4ebd-9fd8-58367b77a71c)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/0c16b027-bdd1-4664-98bc-dd1eb96cb300)
```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/eebaee6a-bd82-42cf-b653-6545c3ec2d4c)
```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/1ed6c9cf-a0ae-4d54-951e-e26684254219)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/11102dbe-2426-421e-9052-8ed25af34462)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/a94f1230-465b-47a9-8ae9-e7e81a2787cd)

# IQR (Inter Quartile Range) :-
```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/5b9f74f5-e392-40cc-96d4-2c7905900b61)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/78b4abff-c221-44c2-af7e-96fca5f5d900)
```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/1d3c4ddd-cb4f-4d4a-b508-65dfd4b7d44d)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/962f4b83-aa98-4987-9d3d-acea05154b2c)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/3bc1b5fa-5515-4eb9-853d-863ce410e632)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/5898bfcb-c925-4993-bdeb-9c02a2dd67d9)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/83275bd5-6ee6-4dc3-b78a-6cf2b56fea5c)

# Z-Score :-
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/f6e4a44b-4566-4dde-b680-3eb0a5b243cc)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
```
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/9d937a31-4e43-4279-9062-c88bc5097497)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/7b2096a0-069e-48a6-9fa6-42b6db5a7ae1)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/dc4451df-a54c-4dda-95e3-8de6b3e44fae)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/865a669c-da3d-4fc1-b72d-01b819a0ae4c)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/dc6d8b59-6668-44a2-8af2-386e695cc710)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/a68a703a-79bd-46a0-92b6-78276c18fae6)

# Result :-
  Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.        
