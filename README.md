# Ex02-Outlier

## AIM
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

 ## ALGORITHM

STEP 1:Read the given Data.

STEP 2:Get the information about the data.

STEP 3:Detect the Outliers using IQR method and Z score.

STEP 4:Remove the outliers:

STEP 5:Plot the datas using box plot.

## CODE and OUTPUT

```
NAME : R . JOYCE BEULAH
REG NO : 212222230058
```
```
import pandas as pd
import seaborn as sns
age = [1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![image](https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/fc5ee52e-bff9-4d8f-a227-e4af36ca806b)
```
sns.boxplot(data=af)
```
<img width="184" alt="image" src="https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/3493ba78-046c-488a-89fc-68fee1997c34">

```
sns.scatterplot(data=af)
```
<img width="180" alt="image" src="https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/4cffc6de-f7d7-41b5-b2ea-6f6d191428e7">

```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
```
```
low=q1-1.5*iqr
low
```
![image](https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/5182e987-1315-4d11-94bb-6816759a2cfc)
```
high=q1+1.5*iqr
high
```
![image](https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/068e10f9-81ec-44d3-b682-309490077ac3)
```
aq=af[((af>=low)&(af<=high))]
aq.dropna()
```
![image](https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/dcdc02f3-1422-448b-a1f3-d0797639246f)
```
sns.boxplot(data=af)
```
<img width="183" alt="image" src="https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/60b434cd-21dc-4a17-ab22-313fc376c3eb">

```
af=af[((af>=low)&(af<=high))]
af.dropna()
```
![image](https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/d1ae90a2-4c84-4d67-bcf4-2c69822d5611)
```
sns.boxplot(data=af)
```
<img width="185" alt="image" src="https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/cabc2255-7578-4db9-b744-e297b97db0e6">

```
sns.scatterplot(data=af)
```
<img width="192" alt="image" src="https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/fdda740b-a6d9-4ef7-a6c1-aba3b90f7d32">

```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data = {'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
![image](https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/fa6325fd-4c19-408a-89fd-4d68be364368)
```
sns.boxplot(data=df)
```
<img width="195" alt="image" src="https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/550e8b67-a4b3-42f2-8598-d317e25e9fbb">

```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
![image](https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/ad57ba39-0c68-4d0e-a325-accf17704636)
```
val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,69,202,72,75,78,81,84,232,87,90,93,96,99,258]
out=[]
def d_o(val):
  ts=3
  m=np.mean(val)
  sd=np.std(val)
  for i in val:
    z=(i-m)/sd
    if np.abs(z)>ts:
      out.append(i)
  return out
op=d_o(val)
op
```
![image](https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/ec8fe698-d4ba-4a26-941b-177d2f3ff9b6)
```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
id=pd.read_csv("iris.csv")
id.head()
```
![image](https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/98f65fba-1bf4-464d-ba9b-da1bc3a9ce1e)
```
sns.boxplot(x='sepal_width',data=id)
```
<img width="174" alt="image" src="https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/20fe4807-e5a2-4c18-9b8c-de7512400271">

```
c1=id.sepal_width.quantile(0.25)
c3=id.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/c920c8a9-0bb7-4a99-a56d-64cf916e8f48)
```
rid=id[((id.sepal_width<(c1-1.5*iq))|(id.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/d6606411-9bde-429c-9baf-35091efb1f37)
```
delid=id[~((id.sepal_width<(c1-1.5*iq))|(id.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/e7fd2d0d-0cde-4a63-a6d3-e6eae5b78c63)
```
sns.boxplot(x='sepal_width',data=delid)
```
<img width="183" alt="image" src="https://github.com/JoyceBeulah/ODD2023---Datascience---Ex-02/assets/118343698/cc194e48-51e4-4c2e-8c7e-f4ac1e15df5e">


## REAULT
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
