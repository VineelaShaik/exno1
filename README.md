# Ex. 1 Data Cleaning and Outlier Detection & Removal

## AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

## Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is
incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about
erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the
information.
## ALGORITHM:
STEP 1 : Read the given Data<br>
STEP 2 : Get the information about the data<br>
STEP 3 : Remove the null values from the data<br>
STEP 4 : Save the Clean data to the file<br>
STEP 5 : Remove outliers using IQR<br>
STEP 6 : Use zscore of to remove outliers<br>
## PROGRAM:
DEVELOPED BY : SHANMUGA RAJ.K <br>
REG NO : 212223040192
## CODING:
### Data Cleaning:

```
import pandas as pd
data=pd.read_csv("/content/SAMPLEIDS.csv")
data
```
![Screenshot 2025-03-04 102727](https://github.com/user-attachments/assets/8c258a9d-6196-48f2-baad-83a832345213)
```
data.head(5)
```
![Screenshot 2025-03-04 102738](https://github.com/user-attachments/assets/a9f92709-e8a5-4b78-815f-b1e800834eb1)
```
data.tail(5)
```
![Screenshot 2025-03-04 102746](https://github.com/user-attachments/assets/688fe387-de29-4e46-aab3-fe0a598112cf)
```
data.isnull().sum()
```
![Screenshot 2025-03-04 102806](https://github.com/user-attachments/assets/9413a0cf-9a69-485e-94c1-60c3b330f6c6)
```
data.isnull().any()
```
![Screenshot 2025-03-04 102813](https://github.com/user-attachments/assets/84439138-1928-4427-a74c-1ed9d53bcf0a)
```
data.dropna()
```
![Screenshot 2025-03-04 102824](https://github.com/user-attachments/assets/a5c1eca6-9a35-4d12-a0e1-e4fcd82a58f0)
```
data.fillna(0)
```
![Screenshot 2025-03-04 102836](https://github.com/user-attachments/assets/e6a44033-3f79-435e-812d-a3765579156e)
```
data.fillna(method = 'ffill')
```
![Screenshot 2025-03-04 102851](https://github.com/user-attachments/assets/e2e050ea-164a-4dcf-ba9d-f8a0e3a5ca71)
```
data.fillna(method = 'bfill')
```
![Screenshot 2025-03-04 102902](https://github.com/user-attachments/assets/7e77692e-2efb-4782-9ac3-972f383eab47)
```
data_dropped = data.dropna()
data_dropped
```
![Screenshot 2025-03-04 102912](https://github.com/user-attachments/assets/5c4f8e44-ac08-4ab2-8213-6ccf1e9f9bbc)
```
data.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![Screenshot 2025-03-04 102925](https://github.com/user-attachments/assets/b0dbd700-e932-4af0-9e58-0c6907d1514e)

### IQR(Inter Quartile Range)
```
 import pandas as pd
 import seaborn as sns
 ir=pd.read_csv('/content/iris.csv')
 ir
```
![Screenshot 2025-03-04 104418](https://github.com/user-attachments/assets/40cf326b-4101-4c3d-99f9-2673a26dff38)
```
ir.describe()
```
![Screenshot 2025-03-04 104425](https://github.com/user-attachments/assets/9e45fd25-1c49-4bb7-b4c7-8cc11fa4ea22)
```
sns.boxplot(x='sepal_width',data=ir)
```
![Screenshot 2025-03-04 104434](https://github.com/user-attachments/assets/a4352ffd-057d-4276-ae03-64181cf849d1)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![Screenshot 2025-03-04 105333](https://github.com/user-attachments/assets/22181ea8-90b1-45f8-907a-2054b0092c7a)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![Screenshot 2025-03-04 104441](https://github.com/user-attachments/assets/3549c967-6fa0-40fd-b4c1-19d4e437ff43)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![Screenshot 2025-03-04 104458](https://github.com/user-attachments/assets/6246e0a1-416e-4c61-9dc5-ec535b6f146e)
```
 sns.boxplot(x='sepal_width',data=delid)
```
![Screenshot 2025-03-04 104505](https://github.com/user-attachments/assets/e783ee3c-b07e-4a8b-bf5e-3a95b4673028)
### Z-Score:
```
 import matplotlib.pyplot as plt
 import numpy as np
 import scipy.stats as stats
 dataset=pd.read_csv("/content/heights.csv")
 dataset
```
![Screenshot 2025-03-04 104512](https://github.com/user-attachments/assets/216cfefe-2807-48f0-a8db-f24dd0e46db4)
```
 df = pd.read_csv("heights.csv")
 q1 = df['height'].quantile(0.25)
 q2 = df['height'].quantile(0.5)
 q3 = df['height'].quantile(0.75)
 iqr = q3-q1
 iqr
```
![Screenshot 2025-03-04 104525](https://github.com/user-attachments/assets/6d55796b-7b73-497d-be18-8d249eafc0fb)
```
 low = q1- 1.5*iqr
 low
```
![Screenshot 2025-03-04 104533](https://github.com/user-attachments/assets/a695edb9-c09c-41fd-8770-98b0bfc340e7)
```
 high = q3 + 1.5*iqr
 high
```
![Screenshot 2025-03-04 104541](https://github.com/user-attachments/assets/015c1ab6-efa1-4915-a1a8-ce3c2b95def5)
```
 df1 = df[((df['height'] >=low)& (df['height'] <=high))]
 df1
```
![Screenshot 2025-03-04 104550](https://github.com/user-attachments/assets/cdc8e7c7-407b-4eb9-9676-c277ea45ed2e)
```
 z = np.abs(stats.zscore(df['height']))
 z
```
![Screenshot 2025-03-04 104559](https://github.com/user-attachments/assets/482b9bc0-f22b-4bad-97a5-2587c290ed4e)
```
df1 = df[z<3]
df1
```
![Screenshot 2025-03-04 104608](https://github.com/user-attachments/assets/28823442-4103-45a1-a4f2-f064f9e5ea01)

## RESULT
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.








