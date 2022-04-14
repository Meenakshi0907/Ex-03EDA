# Ex-03EDA

## AIM:
To perform EDA on the given data set. 

# Explanation:
The primary aim with exploratory analysis is to examine the data for distribution, outliers and 
anomalies to direct specific testing of your hypothesis.
 

# ALGORITHM:
### STEP 1:
Import the needed packages.
### STEP 2:
Using data cleaning method remove all the null values.
### STEP 3:
Detect and remove all outliers.
### STEP 4:
Plot the counts in the form of Histogram or Bar Graph
### STEP 5:
Find the pairwise correlation of all columns in the dataframe.corr()).
### STEP 6:
Save the final data set into the file.
# CODE:
```
import numpy as np
import pandas as pd 
import seaborn as sns
df=pd.read_csv("titanic_dataset.csv")
print(df)

df1=df.copy()
df1.drop("Cabin",axis=1,inplace=True)
df1.drop("Name",axis=1,inplace=True)
df1.drop("Sex",axis=1,inplace=True)
df1.drop("Ticket",axis=1,inplace=True)
df1.drop("Embarked",axis=1,inplace=True)

df.info()

df.isnull().sum()

df["Age"]=df["Age"].fillna(df["Age"].median())

df.boxplot()

import numpy as np 
from scipy import stats 
df2=df1.copy()
z=np.abs(stats.zscore(df1))
print(z)

df3=df1.copy()
q1=df3.quantile(0.25)
q2=df3.quantile(0.75)
IQR=q2-q1
df_new=df3[((df3>=q1-1.5*IQR)&(df3<=q2+1.5*IQR)).all(axis=1)]
print(df_new)

df_new.boxplot()

df.isnull().sum()

df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])

df["Embarked"].value_counts()
df["Pclass"].value_counts()
df["Survived"].value_counts()

sns.countplot(x="Survived",data=df)
sns.countplot(x="Pclass",data=df)
sns.countplot(x="Sex",data=df)

df.info()

sns.displot(df["Age"])
sns.displot(df["Fare"])

sns.countplot(x="Pclass",hue="Survived",data=df)
sns.countplot(x="Sex",hue="Survived",data=df)

sns.displot(df[df["Survived"]==0]["Age"])
sns.displot(df[df["Survived"]==1]["Age"])

pd.crosstab(df["Pclass"],df["Survived"])
pd.crosstab(df["Sex"],df["Survived"])

df.corr()

sns.heatmap(df.corr(),annot=True)
```
# OUPUT:
![output1](./Screenshot%20(23).png)
![output2](./Screenshot%20(24).png)
![output3](./Screenshot%20(25).png)
![output4](./Screenshot%20(26).png)
![output5](./Screenshot%20(27).png)
![output6](./Screenshot%20(28).png)
![output7](./Screenshot%20(30).png)
![output8](./Screenshot%20(73).png)
![output9](./Screenshot%20(134).png)
![output10](./Screenshot%20(135).png)
![output11](./Screenshot%20(136).png)
![output12](./Screenshot%20(137).png)
![output13](./Screenshot%20(138).png)
![output14](./Screenshot%20(139).png)
![output15](./Screenshot%20(140).png)
![output16](./Screenshot%20(142).png)
![output17](./Screenshot%20(143).png)
![output18](./Screenshot%20(144).png)
![output19](./Screenshot%20(145).png)
![output20](./Screenshot%20(146).png)

# RESULT:
The data has been cleaned, outlier has been removed and the EDA on the given data has been performed.
