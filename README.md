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
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/7ec78671-e9c2-40b1-8633-6bba047484cc)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/ff5a0d43-82e8-4934-ac2a-e9379f5a86a4)

```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/9ecd4868-50d1-4c12-851e-ea7c27498496)

```
df.dropna()
```
![image](https://github.com/user-attachments/assets/4914bf38-039f-4b1f-89e6-6e079cbd4105)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/e83389dd-ec1a-4b34-aaa3-7eb5a8914019)
```
df.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/81842716-1fb6-42d7-a1ad-6270030f5f21)
```
df.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/e5e09564-d4cf-42de-9cc3-664c4d3f85d7)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/9fc67c07-1cdc-4dfd-a135-4c0d391b3440)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/48c0b14e-e8d3-4072-aa8e-021cfde991d7)
```
ir=pd.read_csv("/content/iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/c5d099aa-aea4-4e80-bf0f-6bf4a42ce527)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/daae6dfd-a29c-416f-9206-2034c71a8890)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/4caaef6e-a74a-49ff-9bfc-48351e97f0a7)
```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iq=q3-q1
print(q3)
```
![image](https://github.com/user-attachments/assets/4c68c961-6211-4576-856d-2e69bc02fdeb)
```
rid=ir[((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/d73aec93-6f0b-4557-8e65-e8f4a04caf60)
```
delid=ir[~((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/fd2d624d-04a1-40bc-b2c9-716b8387097a)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/6396e86a-6979-4bd0-ae80-0e3d43a4828d)
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
![image](https://github.com/user-attachments/assets/56ed578b-e736-4dd7-aba9-68840b8daa45)
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
![image](https://github.com/user-attachments/assets/7a0d745f-ebe6-4cf9-8d6f-c08fdd346eee)
```
low = q1- 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/af7f624f-430a-4a22-82f9-61f0a422e32d)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/24c202df-d5fb-4869-98f1-ccef44b681a1)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/447f35b8-8000-4e2c-a72e-849bf5e64a30)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/2a0928e5-354d-4f61-a1ea-cb1ffa0efc32)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/a371cdde-15fd-4292-9122-822805fb5f13)
# Result
    Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
