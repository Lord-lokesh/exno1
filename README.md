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
df=pd.read_csv("SAMPLEIDS.csv")
df
```

<img width="1093" height="890" alt="data science ex1 0 1" src="https://github.com/user-attachments/assets/5af582ad-a125-4e5a-a677-acb035dfb1cc" />

```
df.head()
```

<img width="1037" height="316" alt="data science ex1 0 2" src="https://github.com/user-attachments/assets/8cccabb0-18b6-46e2-9e4d-b567c44c75c2" />

```
df.tail()
```

<img width="1062" height="282" alt="data science ex1 0 3" src="https://github.com/user-attachments/assets/3f31140c-3f30-4d43-9ecf-4552ad7b1ade" />

```
df.isnull()
```

<img width="908" height="912" alt="data science ex1 0 4" src="https://github.com/user-attachments/assets/1aec3983-0e4b-4750-b903-9933c8e12b47" />

```
df.notnull()
```

<img width="915" height="905" alt="data science ex1 0 5" src="https://github.com/user-attachments/assets/f7a00f68-3c32-437d-8a8a-fdf2eb5608c5" />

```
df.isnull().sum()
```

<img width="328" height="611" alt="data science ex1 0 6" src="https://github.com/user-attachments/assets/54f002c3-838c-404f-bc86-cb508a7618cd" />

```
df.isnull().any()
```

<img width="462" height="908" alt="data science ex1 0 7" src="https://github.com/user-attachments/assets/1f93fb1e-9471-450a-84a7-8a3b9c257b76" />

```
df.dropna(axis=0)
```

<img width="1140" height="600" alt="data science ex1 0 8" src="https://github.com/user-attachments/assets/f0506289-84c6-4489-95b2-dd1b5e419e97" />

```
df.dropna(axis=1)
```

<img width="398" height="900" alt="data science ex1 0 99" src="https://github.com/user-attachments/assets/475294e6-81ff-478c-9c0e-7d23aaa2c241" />

```
df.fillna(_)
```

<img width="1112" height="925" alt="data science ex1 0 9" src="https://github.com/user-attachments/assets/7f603c62-cd12-48ba-9f20-ad3f8d619502" />

```
df.fillna(method='ffill')
```

<img width="1482" height="920" alt="data science ex1 0 10" src="https://github.com/user-attachments/assets/826e4916-404b-4db1-99ef-9a342ca04088" />

```
df.fillna(method='bfill')
```

<img width="1482" height="923" alt="data science ex1 0 11" src="https://github.com/user-attachments/assets/a2b45c1f-8676-490a-a4cb-ac1bae9ce112" />

```
df.fillna({'GENDER':'MALE','NAME':'SANTHOSH','ADDRESS':'KANCHIPURAM','M1':'76.0','M2':'69.0','M3':'80.0','M4':'76.0','TOTAL':'301.0','AVG':'100.333333'})
```

<img width="1482" height="902" alt="data science ex1 0 12" src="https://github.com/user-attachments/assets/c67bc947-90c7-4b3c-9d5e-1709fb889539" />

```
import pandas as pd
ir=pd.read_csv("iris.csv")
ir
```

<img width="737" height="625" alt="data science ex1 0 13" src="https://github.com/user-attachments/assets/27db37ac-0165-46c9-94b5-038dd44cd822" />

```
ir.describe()
```

<img width="657" height="433" alt="data science ex1 0 14" src="https://github.com/user-attachments/assets/fd84bbf9-1434-4446-b5cc-f4ce5d244c2f" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

<img width="836" height="636" alt="data science ex1 0 15" src="https://github.com/user-attachments/assets/b6f608f1-1464-4d2a-aa47-777eddaa36ec" />

```
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
IQR=Q3-Q1
print(IQR)
```

<img width="502" height="147" alt="data science ex1 0 16" src="https://github.com/user-attachments/assets/1519f0a4-927a-48b8-9541-09f389d83345" />

```
rid=ir[(ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR))]
rid['sepal_width']
```

<img width="832" height="333" alt="data science ex1 0 17" src="https://github.com/user-attachments/assets/82a82044-799c-4d21-8851-037d4aa3b252" />

```
delid=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
delid
```

<img width="820" height="577" alt="data science ex1 0 18" src="https://github.com/user-attachments/assets/bb80a6c7-a5a2-4212-a8b9-b596fa4beecb" />

```
sns.boxplot(x='sepal_width',data=delid)
```

<img width="791" height="640" alt="data science ex1 0 19" src="https://github.com/user-attachments/assets/ad790689-9504-46b9-9cec-07b1ed6f91fc" />

```
import numpy as np
import scipy.stats as stats
xyz=np.abs(stats.zscore(ir['sepal_width']))
xyz
```

<img width="772" height="783" alt="data science ex1 0 20" src="https://github.com/user-attachments/assets/018b8889-d25e-4ff0-a54a-6c2d1591abd2" />

```
ir1=ir[xyz>3]
ir1
```

<img width="825" height="217" alt="data science ex1 0 21" src="https://github.com/user-attachments/assets/e7b70031-c240-40df-82fa-4b6fd6a63c66" />








# Result
The given data and perform data cleaning and save the cleaned data to a file is completed successfully
