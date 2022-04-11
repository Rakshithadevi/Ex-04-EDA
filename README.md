# Ex-04-EDA
## AIM
To perform EDA on the given data set.

## Explanation
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM
```
STEP 1
Import the required packages(pandas,numpy,seaborn).

STEP 2
Read and Load the Dataset

STEP 3
Remove the null values from the data and remove the outliers.

STEP 4
Remove the non numerical data columns using drop() method.

STEP 5:
returns object containing counts of unique values using (value_counts()).

STEP 6:
Plot the counts in the form of Histogram or Bar Graph.

STEP 7:
find the pairwise correlation of all columns in the dataframe(.corr()).

STEP 8:
Save the final data set into the file.
```
## CODE
```
import pandas as pd 
import seaborn as sns
import matplotlib.pyplot as plt
df= pd.read_csv('supermarket.csv')
df.head()
df.info()
df.isnull().sum()
df.boxplot()
cols = ['Tax 5%', 'Total','gross margin percentage','Payment']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
df.boxplot()
df["Total"].value_counts()
plt.title('Grouped by Total')
sns.countplot(x="Total",data=df)
df["Payment"].value_counts()
plt.title('Grouped by Payment')
sns.countplot(x="Payment",data=df)
df["City"].value_counts()
plt.title('Grouped by City')
sns.countplot(x="City",data=df)
df["Product line"].value_counts()
plt.title('Grouped by Product line')
sns.countplot(x="Product line",data=df)
sns.displot(df["Quantity"])
sns.countplot(x="Gender",hue="Product line",data=df)
sns.countplot(x="Total",hue="Customer type",data=df)
pd.crosstab(df["Total"],df["Payment"])
pd.crosstab(df["Quantity"],df["City"])
df.corr()
sns.heatmap(df.corr(),annot=True)
```
## output:
![image](https://user-images.githubusercontent.com/94165326/162787563-030da021-e928-424b-8e0f-e67a60f6c46a.png)

![image](https://user-images.githubusercontent.com/94165326/162787624-b58a0618-26e0-42c1-ba2b-76d3e0a94e54.png)

![image](https://user-images.githubusercontent.com/94165326/162787663-eae9b014-fa5c-475d-b02b-e0f5390f48bf.png)

![image](https://user-images.githubusercontent.com/94165326/162787705-cf4025ba-a65a-4a01-a45d-7266f68e40c7.png)

![image](https://user-images.githubusercontent.com/94165326/162787763-5f3c66be-2f63-413a-96b7-6bb824479886.png)

![image](https://user-images.githubusercontent.com/94165326/162787813-20fd6fbf-5868-43fe-9c53-ddc6786d6356.png)

![image](https://user-images.githubusercontent.com/94165326/162787864-38e6c657-a583-47b8-8be1-5b4c60e09f23.png)

![image](https://user-images.githubusercontent.com/94165326/162787921-6feeb826-a0b3-4b9a-8ba1-580afd46f1ca.png)

![image](https://user-images.githubusercontent.com/94165326/162787998-271c5629-5e31-4ee7-ae82-75e341b45c5d.png)

![image](https://user-images.githubusercontent.com/94165326/162788033-659989f0-4c87-49c1-9001-4b09544e7508.png)

![image](https://user-images.githubusercontent.com/94165326/162788097-365fb680-a834-44ca-857d-4233b1dd82d6.png)

![image](https://user-images.githubusercontent.com/94165326/162788160-e7b4ffe3-4e03-42e3-889b-104139441bd7.png)

![image](https://user-images.githubusercontent.com/94165326/162788213-9977cec4-48c0-41f4-b6c2-c7f29c8f5e3d.png)



## RESULT
The data has been cleaned, outlier has been removed and the EDA on the given data has been performed.
