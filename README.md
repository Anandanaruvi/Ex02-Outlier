# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
   
 ### Aim:
 
TO detect and remove the outliers in the given data set and save the final data.

### Algorithm:

# Step 1:

Import the required packages(pandas,numpy,scipy)

# Step 2:

Read the given csv file

### Step3:

Convert the file into a dataframe and get information of the data.

### Step 4:

Remove the non numerical data columns using drop() method.

### Step 5:

Detect the outliers in the data set using z scores method.

### Step 6:

Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

### Step 7:

Check if the outliersare removed from data set using graphical methods.

### Step 8:

Save the final data set into the file.

### Program:

### 1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

```
import pandas as pd
import numpy as np
import seaborn as sns
df = pd.read_csv("/content/bhp.csv")
df
df.head()
df.describe()
df.info()
df.isnull().sum()
df.shape
sns.boxplot(x="price_per_sqft",data=df)
q1 = df['price_per_sqft'].quantile(0.25)
q3 = df['price_per_sqft'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR
df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]
df1
df1.shape
sns.boxplot(x="price_per_sqft",data=df1)
```

### (3)Examine price_per_sqft column and use zscore of 3 to remove outliers.

```
from scipy import stats
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2
print(df2.shape)
sns.boxplot(x="price_per_sqft",data=df2)
```

### (4)(i) For the data set height_weight.csv detect weight outliers using IQR method.

```
import pandas as pd
import numpy as np
import seaborn as sns
df = pd.read_csv("/content/height_weight - Sheet1.csv")
df
df.head()
df.info()
df.describe()
df.isnull().sum()
df.shape
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR
df1 =df[((df['weight']>=ll)&(df['weight']<=ul))]
df1
df1.shape
sns.boxplot(x="weight",data=df1)
```

### (4)(ii) For the data set height_weight.csv detect height outliers using IQR method.

```
sns.boxplot(x="height",data=df)
q1 = df['height'].quantile(0.25)
q3 = df['height'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR
df2 =df[((df['height']>=ll)&(df['height']<=ul))]
df2
df2.shape
sns.boxplot(x="height",data=df2)
```

### OUTPUT:

(1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.

### Dataset:

![image](https://user-images.githubusercontent.com/120443233/227695867-1391bc4f-62d7-40ca-b526-6e7c7e48ab2b.png)

### Dataset Head :

![image](https://user-images.githubusercontent.com/120443233/227695901-2dbd742a-c85b-4ca2-a84e-d5d959820838.png)

### Dataset Info :

![image](https://user-images.githubusercontent.com/120443233/227716088-f9b065d4-f556-450f-a1eb-8da1422218d9.png)

### Dataset Describe:

![image](https://user-images.githubusercontent.com/120443233/227716131-e0ba028f-820f-4b3c-a8fc-14a4731885f2.png)

### Null Values:

![image](https://user-images.githubusercontent.com/120443233/227716160-9f800ef2-ef6e-4228-ae2d-6c37ee3cebb5.png)

### Dataset Shape:

![image](https://user-images.githubusercontent.com/120443233/227716184-8b81ea17-e7f5-4e74-b3b4-0b5720d2a07a.png)

### Box plot of price_per_sqft column with outliers:

![image](https://user-images.githubusercontent.com/120443233/227716213-cad98607-1157-4162-a4a7-5fa8b9beca26.png)

### price_per_sqft - Dataset after removing outliers:

![image](https://user-images.githubusercontent.com/120443233/227716255-315cf47e-1f5f-456e-998d-ce5e9eee36c9.png)

### price_per_sqft - Shape of Dataset after removing outliers :

![image](https://user-images.githubusercontent.com/120443233/227716322-161e7275-b12f-4798-9083-4b2a61eafe79.png)

### Box Plot of price_per_sqft column without outliers:

![image](https://user-images.githubusercontent.com/120443233/227717142-657ff0fd-2259-489a-be78-599ba4e57e06.png)

### Examine price_per_sqft column and use zscore of 3 to remove outliers.

### Dataset after removal of outlier using z score:

![image](https://user-images.githubusercontent.com/120443233/227716378-ccb43a98-8df7-40e7-a802-2b18ef85830f.png)

### Shape of Dataset after removal of outlier using z score:

![image](https://user-images.githubusercontent.com/120443233/227716403-d510d098-f3d3-4849-853a-0d7913bccbf1.png)

![image](https://user-images.githubusercontent.com/120443233/227717266-ff6fee7b-a816-4063-813c-9367a87ea8c2.png)


### (4) For the data set height_weight.csv detect weight and height outliers using IQR method:

### Dataset:

![image](https://user-images.githubusercontent.com/120443233/227716465-98f06c73-0bb6-4a51-862e-9e799d460bf1.png)

### Dataset Head:

![image](https://user-images.githubusercontent.com/120443233/227716507-a2600819-bbda-45e2-9dc1-4ce9048b1bc6.png)

### Dataset Info:

![image](https://user-images.githubusercontent.com/120443233/227716550-c2e3454d-914e-4279-ab94-4306f3983523.png)

### Dataset Describe:

![image](https://user-images.githubusercontent.com/120443233/227716589-88bbc704-a202-48dc-8efc-575973f4c8d0.png)

### Null Values:

![image](https://user-images.githubusercontent.com/120443233/227716606-787eac0e-8934-4072-8977-1e4970e1406a.png)

### Dataset Shape:

![image](https://user-images.githubusercontent.com/120443233/227716619-e460e3ea-17bd-4db8-8caf-1317b3bd1ba8.png)

### Weight - With outliers:

![image](https://user-images.githubusercontent.com/120443233/227716658-4ab071f6-5bd6-441f-8c3a-9d7175bfedb3.png)

### Weight - Dataset after removing Outliers using IQR method:

![image](https://user-images.githubusercontent.com/120443233/227716675-077706bc-344b-45d8-bd07-bc24766ace99.png)

### Weight - Shape of Dataset after removing Outliers using IQR method:

![image](https://user-images.githubusercontent.com/120443233/227716716-36f0a213-5157-4bc3-82c9-7faea4bb127d.png)

### Weight - Without Outliers using IQR method:

![image](https://user-images.githubusercontent.com/120443233/227716755-5a813422-b37a-4dcf-a43d-0b0f58b1fae4.png)

### Height - With outliers:

![image](https://user-images.githubusercontent.com/120443233/227716767-d58b8496-5b0e-457b-9f0f-bf5512ae8b25.png)

### Height - Dataset after removing Outliers using IQR method:

![image](https://user-images.githubusercontent.com/120443233/227716799-67bf228f-94e2-4f2b-9ab9-5bef869ca078.png)

### Height - Shape of Dataset after removing Outliers using IQR method:

![image](https://user-images.githubusercontent.com/120443233/227716856-f6acd389-a51b-49fe-80af-64c486b39a86.png)

Height - Without Outliers using IQR method:

![image](https://user-images.githubusercontent.com/120443233/227716871-8573389c-4b6a-4e96-8e7a-b0f6d1ea9165.png)

### Result:

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.

 
