# EXNO:4-DS
# AIM:
To read the given data and perform Feature Scaling and Feature Selection process and save the
data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Scaling for the feature in the data set.
STEP 4:Apply Feature Selection for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE SCALING:
1. Standard Scaler: It is also called Z-score normalization. It calculates the z-score of each value and replaces the value with the calculated Z-score. The features are then rescaled with x̄ =0 and σ=1
2. MinMaxScaler: It is also referred to as Normalization. The features are scaled between 0 and 1. Here, the mean value remains same as in Standardization, that is,0.
3. Maximum absolute scaling: Maximum absolute scaling scales the data to its maximum value; that is,it divides every observation by the maximum value of the variable.The result of the preceding transformation is a distribution in which the values vary approximately within the range of -1 to 1.
4. RobustScaler: RobustScaler transforms the feature vector by subtracting the median and then dividing by the interquartile range (75% value — 25% value).

# FEATURE SELECTION:
Feature selection is to find the best set of features that allows one to build useful models. Selecting the best features helps the model to perform well.
The feature selection techniques used are:
1.Filter Method
2.Wrapper Method
3.Embedded Method

# CODING AND OUTPUT:
### NAME : NITEESH M
### REG NO :212222230098
```
import pandas as pd
from scipy import stats
import numpy as np
import seaborn as sns

df=pd.read_csv("/content/bmi.csv")
df1=pd.read_csv("/content/bmi.csv")
df2=pd.read_csv("/content/bmi.csv")

df.head()
```
![img](out.png)

```
df.dropna()
```
![img](out1.png)

```
max_vals = np.max(np.abs(df[['Height','Weight']]))
max_vals
```
![img](out2.png)
```
from sklearn.preprocessing import StandardScaler
sc=StandardScaler()
df1[['Height','Weight']]=sc.fit_transform(df1[['Height','Weight']])
df1.head(10)
```
![img](out3.png)

```
from sklearn.preprocessing import MinMaxScaler
scaler=MinMaxScaler()
df[['Height','Weight']]=scaler.fit_transform(df[['Height','Weight']])
df.head(10)
```
![img](out4.png)

```
from sklearn.preprocessing import Normalizer
scaler=Normalizer()
df2[['Height','Weight']]=scaler.fit_transform(df2[['Height','Weight']])
df2
```
![img](out5.png)

```
from sklearn.preprocessing import MaxAbsScaler
scaler=MaxAbsScaler()
df3[['Height','Weight']]=scaler.fit_transform(df3[['Height','Weight']])
df3
```
![img](out6.png)

```
df4=pd.read_csv("/content/bmi.csv")
from sklearn.preprocessing import RobustScaler
scaler=RobustScaler()
df4[['Height','Weight']]=scaler.fit_transform(df4[['Height','Weight']])
df4.head()
```
![img](out7.png)

```
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score, confusion_matrix
data=pd.read_csv('/content/income(1) (1).csv',na_values=[" ?"])
data
```
![img](out8.png)

```
data.isnull().sum()
```
![img](out9.png)

```
missing=data[data.isnull().any(axis=1)]
missing
```
![img](out10.png)

```
data2=data.dropna(axis=0)
data2
```
![img](out11.png)

```
sal=data['SalStat']
data2['SalStat']=data2['SalStat'].map({' less than or equal to 50,000':0,' greater than 50,000':1})
print(data2['SalStat'])
```
![img](out12.png)

```
sal2=data2['SalStat']
dfs=pd.concat([sal,sal2],axis=1)
dfs
```
![img](out13.png)

```
data2
```
![img](out14.png)

```
new_data=pd.get_dummies(data2,drop_first=True)
new_data
```
![img](out15.png)

```
columns_list=list(new_data.columns)
print(columns_list)
```
![img](out16.png)

```
features = list(set(columns_list)-set(['SalStat']))
print(features)
```
![img](out17.png)
```
y=new_data['SalStat'].values
print(y)
```
![img](out18.png)
```
x=new_data[features].values
print(x)
```
![img](out19.png)

```
import pandas as pd
from sklearn.feature_selection import SelectKBest, mutual_info_classif, f_classif

data={
    'Feature1':[1,2,3,4,5],
    'Feature2':['A','B','C','A','B'],
    'Feature3':[0,1,1,0,1],
    'Target':[0,1,1,0,1]

}
df=pd.DataFrame(data)
df
```
![img](out20.png)
```
X=df[['Feature1','Feature3']]
y=df[['Target']]
selector=SelectKBest(score_func=mutual_info_classif,k=1)
X_new=selector.fit_transform(X,y)
```
![img](out21.png)
```
selected_feature_indices=selector.get_support(indices=True)
selected_features=X.columns[selected_feature_indices]
print("Selected Features:")
print(selected_features)
```
![img](out22.png)
```
import pandas as pd
import numpy as np
from scipy.stats import chi2_contingency
import seaborn as sns
tips=sns.load_dataset('tips')
tips.head()
```
![img](out23.png)

```
contingency_table=pd.crosstab(tips['sex'],tips['time'])
print(contingency_table)
```
![img](out24.png)
```
chi2, p, _, _=chi2_contingency(contingency_table)
print(f"Chi-Square Statistic: {chi2}")
print(f"P-value: {p}")
```
![img](out25.png)

# RESULT:
     Thus to read the given data and perform Feature Scaling and Feature Selection process was performed successfully.
