## EXNO-3-Feature Encoding and Transformation

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
df
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/9e38148f-3b4b-4267-ac89-155114224907)
```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/3ca08fce-b326-4096-b5ea-540df3fa25de)
```
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/0500a478-3e15-4e4b-ae2c-9e57894d362c)

```
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/89c48d43-d877-4e5a-a4a6-190203afdb06)
```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
df2=pd.concat([df2,enc],axis=1)
df2
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/851c61c8-6164-4f9d-89cc-2da16de83751)
```
pd.get_dummies(df2,columns=["nom_0"])
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/f37bceb3-469b-4025-8d61-b7510ce44c44)
```
pip install --upgrade category_encoders
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/d1c13e8e-5405-45b4-81b0-360b141acb55)
```
from category_encoders import BinaryEncoder
df=pd.read_csv("/content/data.csv")
df
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/6324c705-4043-4c75-ad7a-350a7af8c913)
```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
df
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/2a4420ca-393c-4db5-b70d-0190aa5d3ed3)
```
dfb=pd.concat([df,nd],axis=1)
dfb
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/1fb334d7-af88-4985-b8c6-53bd67fdc4ae)
```
from category_encoders import TargetEncoder
te=TargetEncoder()
CC=df.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
CC
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/dc4bbaca-8056-45c1-9467-eae82365c593)
```
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("/content/Data_to_Transform.csv")
df
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/c7372cb3-e6f7-4968-9cea-f577dd1579a2)
```
df.skew()
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/9c11288b-8af9-4743-a61d-5f6a194002ef)
```
np.log(df["Highly Positive Skew"])
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/b3366acf-8258-4b17-9214-ba7f923051ba)
```
np.reciprocal(df["Moderate Positive Skew"])
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/eb00508a-b1f9-4246-9f79-1aca5a789934)
```
np.sqrt(df["Highly Positive Skew"])
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/06ef9046-039c-4f84-84c7-3168a0f8bf99)
```
np.square(df["Highly Positive Skew"])
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/e689a9a4-a0e7-4d18-9853-e15fd802cbad)
```
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/5b7d83ea-b2b5-4578-b5be-c9276349f943)
```
df.skew()
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/dda47781-24a8-4e67-ae72-bb3a61b516dc)
```
df["Moderate Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Moderate Negative Skew"])
df.skew()
```
![image](https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/859b098a-38ed-4237-9215-630b6197c55a)
```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
<img src="https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/db9383e3-08e3-4b0d-8cf9-7d730479ba15" width="400" height="300">
```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```
<img src="https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/35c3c643-d659-45a2-b41c-825f708bb77a" width="400" height="300">
```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)

df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])

sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
<img src="https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/f7660654-7cda-403c-80d2-076de26be3ec" width="400" height="300">
```
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line='45')
plt.show()
```

<img src="https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/2a80dd6d-d895-4ff2-bcf2-366cb4a048be" width="400" heigth="300">

```
sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show()
```
<img src="https://github.com/Vanisha0609/EXNO-3-DS/assets/119104009/fa3211cb-c8b8-4b8d-8719-b944a75e3c8d" width="400" height="300">


# RESULT:
Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.

       
