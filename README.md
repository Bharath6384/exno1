![image](https://github.com/user-attachments/assets/d27c270d-39a6-4e40-86a3-0b9e8d12763b)# Exno:1
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
~~~
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
~~~
![image](https://github.com/user-attachments/assets/2737194f-8114-4c97-a55e-174e38c8e5dd)
~~~
df.shape
~~~
![image](https://github.com/user-attachments/assets/474206d6-bf51-42e5-a5e6-b2fa2fc4180f)
~~~
df.describe()
~~~
![image](https://github.com/user-attachments/assets/c70d839a-d495-412a-84ab-6af30886937b)
~~~
df.info()
~~~
![image](https://github.com/user-attachments/assets/e7a3e920-3f06-4c27-95f5-192a3d0dc7b2)
~~~
df.head(10)
~~~
![image](https://github.com/user-attachments/assets/5f7fc591-235c-4c00-8d0b-849bf4812e86)
~~~
df.tail(10)
~~~
![image](https://github.com/user-attachments/assets/3f5fda8d-0cc4-4a95-8827-84ef358b92eb)
~~~
df.isna().sum()
~~~
![image](https://github.com/user-attachments/assets/fda785f6-eaa4-45f3-9656-46f31f7c0cfd)
~~~
df.dropna(how='any').shape
~~~
![image](https://github.com/user-attachments/assets/78f791e1-465d-41ce-9c67-07f08c53dc33)
~~~
df.shape
~~~
![image](https://github.com/user-attachments/assets/2969980a-1a2a-4b16-89e2-57a24b03e6c2)
~~~
d=df.dropna(how='any')
d
~~~
![image](https://github.com/user-attachments/assets/dd3ed857-c7eb-41e4-9907-71a8096ef46f)
~~~
mn=df.TOTAL.mean()
mn
~~~
![image](https://github.com/user-attachments/assets/34c4041c-30b0-4433-bb93-a717b5f63fbf)
~~~
df.TOTAL.fillna(mn,inplace=True)
df
~~~
![image](https://github.com/user-attachments/assets/ce41006c-7523-4629-bc80-f0405598b20f)
~~~
df.isnull().sum()
~~~
![image](https://github.com/user-attachments/assets/5561242e-59a8-465e-8720-3b0443507e03)
~~~
df.M1.fillna(method='ffill',inplace=True)
df
~~~
![image](https://github.com/user-attachments/assets/95f71346-4546-42ab-ad25-37c4b4c251e3)
~~~
df.isnull().sum()
~~~
![image](https://github.com/user-attachments/assets/858544fa-fc3a-495f-9143-306dfd3cb160)
~~~
df.M2.fillna(method='ffill',inplace=True)
df
~~~
![image](https://github.com/user-attachments/assets/1a0b5215-106c-4065-b0a2-b75835155162)
~~~
df.isnull().sum()
~~~
![image](https://github.com/user-attachments/assets/472f78a6-1acd-4dc3-ba4d-ede353281221)
~~~
df.M3.fillna(method='ffill',inplace=True)
df
~~~
![image](https://github.com/user-attachments/assets/d759d173-fac5-4092-8292-1798fa1400a7)
~~~
df.isnull().sum()
~~~
![image](https://github.com/user-attachments/assets/d157b9af-1031-401f-9faf-dcfe14e33c72)
~~~
 df.duplicated()
~~~
![image](https://github.com/user-attachments/assets/1aff3757-4004-45e4-aa9b-9441b6cbf019)
~~~
df.drop_duplicates(inplace=True)
df
~~~
![image](https://github.com/user-attachments/assets/7aece93e-f7a4-4347-aa12-238eb065fe35)
~~~
df.duplicated()
~~~
![image](https://github.com/user-attachments/assets/5af279de-5833-49b7-9af9-fc054aad00ae)
~~~
 df['DOB']
~~~
![image](https://github.com/user-attachments/assets/5fa797a5-312c-4b1c-9209-50e593aff087)
~~~
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
~~~
![image](https://github.com/user-attachments/assets/6606d8d6-fb84-40c6-91e1-9dc9a15e62ec)
~~~
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
~~~
![image](https://github.com/user-attachments/assets/66d8eeda-5a9a-4e65-9f08-73b115225860)
~~~
import pandas as pd
import seaborn as sns
import numpy as np
ans=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(ans)
df
~~~
![image](https://github.com/user-attachments/assets/6b29e931-d213-4c21-b3f3-be653552de01)
~~~
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df
~~~
![image](https://github.com/user-attachments/assets/e7faf849-4a1d-4685-b90f-a6b0f0ea4815)
~~~
sns.boxplot(data=ans)
~~~
![image](https://github.com/user-attachments/assets/6e7785ef-1478-4998-9d31-5ee62e243d4e)
~~~
sns.scatterplot(data=df)
~~~
![image](https://github.com/user-attachments/assets/acda417d-cebd-4216-9782-593b72550373)
~~~
q1=df.quantile(0.25)
q2=df.quantile(0.5)
q3=df.quantile(0.75)
iqr=q3-q1
iqr
~~~
![image](https://github.com/user-attachments/assets/5b0f0fdb-7871-4921-aa1f-5ab9e0141aa4)
~~~
upper_bound=q3+1.5*iqr
lower_bound=q1-1.5*iqr
upper_bound
~~~
![image](https://github.com/user-attachments/assets/f5feda5d-2b50-412e-9d43-83a37646b6c7)
~~~
lower_bound
~~~
![image](https://github.com/user-attachments/assets/fd09e801-3eb0-4503-8963-26bcd7035153)
~~~
outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",q1)
print("Q3:",q3)
print("IQR:",iqr)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)
~~~
![image](https://github.com/user-attachments/assets/403ea860-7cfb-43b0-acfc-bfd59cb953a8)
~~~
df=df[(df>=lower_bound)&(df<=upper_bound)]
df
~~~
![image](https://github.com/user-attachments/assets/707e5918-51a4-4b2d-86b2-467ff0d564c9)
~~~
df=df.dropna()
df
~~~
![image](https://github.com/user-attachments/assets/2f7a3e29-e4b8-4df2-9188-f518a2f17b1c)
~~~
sns.boxplot(data=df)
~~~
![image](https://github.com/user-attachments/assets/b4f8edc5-fdc1-42f7-a688-9f2d33c7e0e1)
~~~
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)
~~~
![image](https://github.com/user-attachments/assets/10656e18-ca85-46cb-aed6-0fd75a9b3155)
~~~
 threshold=3
 outlier=[]
 for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
 print('outlier in dataset is :',outlier)
~~~
![image](https://github.com/user-attachments/assets/647ca82e-d97b-4349-8db6-419e230dcce2)
~~~
 import pandas as pd
 import numpy as np
 import seaborn as sns
 from scipy import stats
 data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
 df=pd.DataFrame(data)
 df
~~~
![image](https://github.com/user-attachments/assets/8f435c9f-c456-48ae-8622-0293f949089c)
~~~
w=np.abs(stats.zscore(df))
print(df[w['weight']>3])
~~~
![image](https://github.com/user-attachments/assets/f4ed001a-adc7-4e72-959c-332765143f70)


# Result
Thus the given data and perform data cleaning and save the cleaned data to a file done successfully

