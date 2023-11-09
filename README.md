# EX-04 MULTIVARIATE ANALYSIS
## AIM:
To perform Multivariate EDA on the given data set.

## EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM:
1. Import the built libraries required to perform EDA and outlier removal.
2. Read the given csv file.
3. Convert the file into a dataframe and get information of the data.
4. Return the objects containing counts of unique values using (value_counts()).
5. Plot the counts in the form of Histogram or Bar Graph.
6. Use seaborn the bar graph comparison of data can be viewed.
7. Find the pairwise correlation of all columns in the dataframe.corr()
8. Save the final data set into the file.

## PROGRAM:
```
Name: JENISHA.J
Reg.No: 212222230056
```
### SuperStore.csv
```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
data=pd.read_csv("/content/SuperStore (1).csv")
df=pd.DataFrame(data)
df.head()
df.info()
df.describe()
df.isnull().sum()
df['Postal Code']=df['Postal Code'].fillna(df['Postal Code'].mode()[0])
df.isnull().sum()

sns.scatterplot(x=df['Region'],y=df['Sales'])

states=df.loc[:,["State","Sales"]]
states=states.groupby(by=["State"]).sum().sort_values(by="Sales")
plt.figure(figsize=(12,5))
plt.xticks(rotation=90)
sns.barplot(x=states.index,y="Sales",data=states)

states=df.loc[:,["Ship Mode","Row ID"]]
states=states.groupby(by=["Ship Mode"]).sum().sort_values(by="Row ID")
sns.barplot(x=states.index,y="Row ID",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("SHIP MODE")
plt.ylabel=("ROW ID")
plt.show()

sns.boxplot(x=df['Ship Date'],y=df['Sales'])
sns.displot(df, x="Region", hue="Category")
df.corr()
sns.heatmap(df.corr(),annot=True)
```

### diabetes.csv
```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
df=pd.read_csv("/content/diabetes (1).csv")
df
df.describe()
df.info
df.isnull().sum()

sns.scatterplot(x=df['Glucose'],y=df['BloodPressure'])

sns.scatterplot(x=df['Glucose'], y=df['BloodPressure'], hue=df['Outcome'])

Age=df.loc[:,["Age","BMI"]]
Age=Age.groupby(by=["Age"]).sum().sort_values(by="BMI")
plt.figure(figsize=(12,5))
plt.xticks(rotation=90)
sns.barplot(x=Age.index,y="BMI",data=Age)

Age=df.loc[:,["BloodPressure","Glucose"]]
Age=Age.groupby(by=["BloodPressure"]).sum().sort_values(by="Glucose")
sns.barplot(x=Age.index,y="Glucose",data=Age)
plt.xticks(rotation = 90)
plt.xlabel=("BloodPressure")
plt.ylabel=("Glucose")
plt.show()

sns.boxplot(x=df['DiabetesPedigreeFunction'],y=df['Insulin'])

sns.displot(df, x="Glucose", hue="Outcome")

df.corr()

sns.heatmap(df.corr(),annot=True)
```

## OUTPUT:
### SuperStore.csv
![Screenshot 2023-11-09 203359](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/462bc1e5-48ae-4793-bf2e-4eef42629752)
![Screenshot 2023-11-09 204022](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/788145a0-bf5b-40ce-b9ad-f1cd1c242eeb)
![Screenshot 2023-11-09 204101](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/eff748f8-e9f7-4b6c-8a4b-b9f62f6c7851)
![Screenshot 2023-11-09 203635](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/a7a06d42-358f-49d7-b499-6ce2b77e634a)
![Screenshot 2023-11-09 203710](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/ffaafa67-352a-4be0-ae94-bcc438557dc5)
![Screenshot 2023-11-09 203742](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/0e4158a3-af19-4b07-b5be-54db7e5abf35)
![Screenshot 2023-11-09 203816](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/bf95809e-88c4-43bb-932d-c23f03ab5620)
![Screenshot 2023-11-09 203839](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/f965db03-592a-42ea-8b4c-6567a914b27d)

### diabetes.csv
![Screenshot 2023-11-09 204936](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/6a01f46f-3406-44e7-b36b-436d8460f411)
![Screenshot 2023-11-09 205028](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/681d6468-5e42-4c67-b72c-d771eb454c27)
![Screenshot 2023-11-09 205116](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/cdf82a9d-11ef-429d-9025-cf1b31e589f3)
![Screenshot 2023-11-09 205210](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/9e1d837d-53d9-4955-b7d0-1b61eff9cc35)
![Screenshot 2023-11-09 205321](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/49bdf0c1-b458-4ac6-8399-73710ef4281d)
![Screenshot 2023-11-09 205350](https://github.com/Jenishajustin/ODD2023-Datascience-Ex-04/assets/119405070/646ec804-8d6a-432a-a309-ba12608c758f)

## RESULT::
Thus we have read the given data and performed the multivariate analysis with different types of plots.
