# Exno:1 Data Cleaning Process
# Date: 12/03/2025
# Regno: 212223040208
# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
# STEP 1:
Read the given Data

# STEP 2:
Get the information about the data

# STEP 3: 
Remove the null values from the data

# STEP 4: 
Save the Clean data to the file

# STEP 5: 
Remove outliers using IQR

# STEP 6:  
Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/e3800258-4401-4614-8118-b50e247dcafe)


```
df.head()
```
![image](https://github.com/user-attachments/assets/13d88e71-0dff-49be-95da-cbcd9ce9bc1e)


```
df.tail()
```
![image](https://github.com/user-attachments/assets/b3fe0add-0550-44f9-beb7-13e1ff391c88)


```
df.isnull()
```
![image](https://github.com/user-attachments/assets/d7cc14ee-f7c9-41cd-b900-1ae292569114)


```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/c65a4f99-bac3-4b99-a482-eeb24efbfab8)


```
df.dropna(axis=1)
```
![image](https://github.com/user-attachments/assets/43a13c30-0032-44f1-a845-c8a300a3a9fa)


```
df.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/100ed027-5864-409b-a878-a49cb084d4b6)


```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/38432717-8ee6-4bc7-891f-ffa6c9688c02)


```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/0e436dd8-fae6-4037-9737-719daad11043)


```
df.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/39f10da0-fd2d-4721-9ca1-94e87d0b618c)


```
df.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/7e3e6b23-e6d8-485f-8b59-0c82d0d4c9a8)


```
df.fillna({'GENDER':'FEMALE','NAME':'SAHANA','ADDRESS':'PUTHOOR'})
```
![image](https://github.com/user-attachments/assets/1f7669dd-3f51-41bf-9b62-976873813b83)


```
ir=pd.read_csv("/content/iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/98a39b78-4124-452d-b544-8aa4ddfcfe87)


```
ir.describe()
```
![image](https://github.com/user-attachments/assets/75e8fc4c-262f-4ebf-981c-65870717452e)


```
ir.info()
```
![image](https://github.com/user-attachments/assets/8cc47629-3ed3-4905-99b7-fe3781498b94)


```
ir.shape
```
![image](https://github.com/user-attachments/assets/85293ca6-6b54-40ae-8f54-296fb1234ae6)


```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/1531a348-1a1f-4c29-bffe-4afd0bbed867)


```
ir.isnull().sum()
```
![image](https://github.com/user-attachments/assets/65e92bf6-bb91-46e1-b4d6-a04523cb0b3b)


```
q1=ir.sepal_width.quantile(0.25)
q1
```
![image](https://github.com/user-attachments/assets/10ee2310-6dde-4c20-83ef-24e02e5b7f57)


```
q3=ir.sepal_width.quantile(0.75)
q3
```
![image](https://github.com/user-attachments/assets/4d38dfbb-6289-4cdb-85b7-6d7f48370c5b)


```
iqr=q3-q1
print(iqr)
```
![image](https://github.com/user-attachments/assets/2bcedeb0-778e-4d94-8161-fca57dc704af)


```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))| (ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/329733fc-67c2-4b92-9264-c3d16248cbe1)


```
d=ir[~((ir.sepal_width<(q1-1.5*iqr))| (ir.sepal_width>(q3+1.5*iqr)))]
d
```
![image](https://github.com/user-attachments/assets/0c2ecd4b-57d1-47a8-bfa1-c536e6724aad)


```
sns.boxplot(x='sepal_width',data=d)
```
![image](https://github.com/user-attachments/assets/85f5639f-7935-42cb-978f-b384224c5b45)



```
import scipy.stats as stats
import numpy as np
```
```
z=np.abs(stats.zscore(ir['sepal_width']))
z
```
![image](https://github.com/user-attachments/assets/77d87fa3-1c4d-446b-bdbe-e99c2fd96e0d)



```
df1=ir[z<0.8]
df1
```
![image](https://github.com/user-attachments/assets/6116f490-08a7-4d8c-a013-ff40674ccc2c)

            
# Result
 Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.         
