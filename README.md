# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
### AIM:

TO detect and remove the outliers in the given data set and save the final data.

#### Algorithm:

### Step 1

Import the required packages(pandas,numpy,scipy)

### Step 2
 
Read the given csv file use read_csv()

### Step 3 

Convert the file into a dataframe and get information of the data.

### Step 4

Remove the non numerical data columns using drop() method.

### Step 5

Detect the outliers in the data set using z scores method.

### Step 6:

Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

### Step 7:

Check if the outliersare removed from data set using graphical methods.

### Step 8:

Save the final data set into the file.

### Program:

(i)For the data set height_weight.csv detect weight outliers using IQR method
```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
df=pd.read_csv("/content/height_weight.csv")
df
sns.boxplot(x="weight",data=df)
q1 = df["weight"].quantile(0.25)
q3 = df['weight'].quantile(0.75)
print("First Quantile = ",q1,"\nSecond Quantile = ",q3)
IQR = q3-q1
low = q1-1.5*IQR
high = q3+1.5*IQR
df4 =df[((df['weight']>=low)&(df['weight']<=high))]
df4
sns.boxplot(x="weight",data=df4)
```

(ii) For the data set height_weight.csv detect height outliers using IQR method.
```
sns.boxplot(x="height",data=df)
q1 = df["height"].quantile(0.25)
q3 = df['height'].quantile(0.75)
print("First Quantile = ",q1,"\nSecond Quantile = ",q3)
IQR = q3-q1
low = q1-1.5*IQR
high = q3+1.5*IQR
df4 =df[((df['height']>=low)&(df['height']<=high))]
df4
sns.boxplot(x="height",data=df4)
sns.scatterplot(data=df4)
sns.boxplot(data=df4)
```

### Examine Height column and use IQR to remove outliers and create new dataframe
```
import pandas as pd
import seaborn as sns
df=pd.read_csv("/content/heights.csv")
df
sns.boxplot(data=df)
median=df.quantile(0.50)
q1=df.quantile(0.25)
q3=df.quantile(0.75)
iqr=q3-q1
q1
df1=df[((df>=q1-1.5*iqr)&(df<=q3+1.5*iqr))]
df1
sns.boxplot(data=df1)
```
### Examine price_per_sqft column and use IQR to remove outliers and create new dataframe
```
import pandas as pd
import seaborn as sns
df=pd.read_csv("/content/bhp.csv")
df
d2=df['price_per_sqft']
d2
sns.boxplot(data=df)
sns.boxplot(data=df['price_per_sqft'])
q1 = df["price_per_sqft"].quantile(0.25)
q3 = df['price_per_sqft'].quantile(0.75)
print("First Quantile = ",q1,"\nSecond Quantile = ",q3)
IQR = q3-q1
low = q1-1.5*IQR
high = q3+1.5*IQR
df2 =df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]
df2
sns.boxplot(data=df2['price_per_sqft'])
```

### Examine price_per_sqft column and use zscore of 3 to remove outliers.
```
from scipy import stats
import numpy as np
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2
df2.shape
sns.boxplot(y="price_per_sqft",data=df2)
```

### Output:

DATASET FOR WEIGHT_HEIGHT_CSV
![image](https://user-images.githubusercontent.com/118679646/227786950-f37544a8-e700-49bb-a2d9-4b5bf78b6434.png)

DATASET BOXPLOT WITH OUTLIERS(WEIGHT_HEIGHT)

![image](https://user-images.githubusercontent.com/118679646/227787056-949f04ce-afca-49c8-a6f9-a315ebb97180.png)

DATASET BOXPLOT WITHOUT OUTLIERS(WEIGHT_HEIGHT)

![image](https://user-images.githubusercontent.com/118679646/227787195-c569d82f-3b75-4ed8-8f2f-e5a0d7c59c66.png)

![image](https://user-images.githubusercontent.com/118679646/227787246-52a3c2e8-ba82-4583-81f1-bbd1ecb9b8f0.png)


DATASET FOR HEIGHT_CSV

![image](https://user-images.githubusercontent.com/118679646/227787326-52914cad-49e9-442f-95fd-c877fe6c1429.png)

DATASET BOXPLOT WITH OUTLIERS

![image](https://user-images.githubusercontent.com/118679646/227787355-5e6ad198-2e98-44e6-b376-058ebadbe6a8.png)

DATASET BOXPLOT WITHOUT OUTLIERS

![image](https://user-images.githubusercontent.com/118679646/227787386-159346f6-8217-4e13-b254-3292e3b33408.png)

DATASET FOR bhp.csv

![image](https://user-images.githubusercontent.com/118679646/227787416-caffa934-e1a9-4f85-9322-731d2207180a.png)

bhp Boxplot

![image](https://user-images.githubusercontent.com/118679646/227787483-6f042c70-8f06-4567-ae6d-85d7f9efbc76.png)

price_per_sqft BoxPlot

![image](https://user-images.githubusercontent.com/118679646/227787512-cdffb46f-c542-4ac5-a6a6-5202925c7d1d.png)

WITHOUT OUTLIERS IN DATABASE

![image](https://user-images.githubusercontent.com/118679646/227787614-a787493f-330e-4428-9394-2a905e42f0be.png)

DATASET BOXPLOT AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)

![image](https://user-images.githubusercontent.com/118679646/227787634-ba9cb461-07eb-4277-aea4-9f840d2c1755.png)

