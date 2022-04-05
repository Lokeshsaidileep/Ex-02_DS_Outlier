# Ex-02_DS_Outlier
# AIM
To detect and remove the outliers in the given data set and save the final data.
# EXPLANATION
Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.
# ALGORITHM
# Step 1
Import the required packages(pandas,numpy,scipy)
# Step 2
Read the given csv file
# Step 3
Convert the file into a dataframe and get information of the data.
# Step 4
Remove the non numerical data columns using drop() method.
# Step 5
Detect the outliers in the data set using z scores method.
# Step 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
# Step 7
Check if the outliersare removed from data set using graphical methods.
# Step 8
Save the final data set into the file.
# PROGRAM
```
Developed by: Lokesh sai dileep
Register number:212221230111


import pandas as pd
df=pd.read_csv('weight.csv')
df

#removing non numerical columns
df=df.drop("Gender",axis=1)
print('After removing Non numeric columns:')
df

#graph to display outliers
df.boxplot()

#calculating z scores to detect outliers
import numpy as np
from scipy import stats
z=np.abs(stats.zscore(df))
print(z)

#removing outliers from weight
df1=df.copy()
df1=df1[(z<3).all(axis=1)]
df1

#checking if outliers are removed through graph
df1.boxplot()

#removing outliers from height
df2=df.copy()
q1=df2.quantile(0.25)
q3=df2.quantile(0.75)
IQR=q3-q1
df_new=df2[((df2>=q1-1.5*IQR)&(df2<=q3+1.5*IQR)).all(axis=1)]
df_new

#checking if outliers are removed through graph
df_new.boxplot()

#final dataset
df_new

#saving data file
df.to_csv('weight.csv', index=False)
```
# OUTPUT
# Initial data set
 ![image](https://user-images.githubusercontent.com/94883079/161675746-88e97f6b-0d94-432d-a475-fe3083165162.png)

# Data set after removing non numerical sets
 ![image](https://user-images.githubusercontent.com/94883079/161675773-d378f1c8-04cc-4d76-a6aa-79ae7c395659.png)

# Graph displaying initial dataset with outliers
![image](https://user-images.githubusercontent.com/94883079/161675818-c78d6014-e64c-4739-84fc-863add84ea62.png)
 
# Z scores to detect outliers
![image](https://user-images.githubusercontent.com/94883079/161675848-f15fd90d-a99d-4ff0-a463-b14fc93e3042.png)
 
# Data set after removing outliers in weight using z scores and list manupilation
 ![image](https://user-images.githubusercontent.com/94883079/161675874-2f078f21-c513-4ec5-9ceb-109109da44bb.png)

# Graph after removing outliers in weight
 ![image](https://user-images.githubusercontent.com/94883079/161675904-eca43e6e-4577-445b-a3d6-5777da2ca136.png)

# Data set after removing outliers in height using Interquartile Range(IQR)
 ![image](https://user-images.githubusercontent.com/94883079/161675945-7b172a9e-e42b-4a5c-a00f-8dc5241d528f.png)

# Final graph after removing all outliers
![image](https://user-images.githubusercontent.com/94883079/161675970-cb909fba-fd23-409d-bd2a-a3a173948fd8.png)
 
# Final data set
 ![image](https://user-images.githubusercontent.com/94883079/161675986-6c746248-9832-4633-91f3-ed4d339e94a0.png)

# RESULT
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.

