# data_cleaning_ml
 This pandas script simplifies data cleaning by removing duplicates, handling missing values, and counting entries. Learn to drop rows/columns with nulls, fill gaps with mean or median, and prepare clean, reliable data for analysis or machine learning.
 
import pandas as pd
import numpy as np
df = pd.read_csv('day0.csv')

# remove duplicates value
df_no_duplicate = df.drop_duplicates()
print(df_no_duplicate)
print("------------")

# remove duplicates with Specific Column
df_unique_name = df.drop_duplicates(subset=['Name'],keep='first')
print(df_unique_name)
print("------------")

#Remove Rows with Any Null Values
df_no_null = df.dropna()
print(df_no_null)
print("------------")

#Fill Null Values with a Default Value
df_no_null_age = df.dropna(subset=['Age'])
print(df_no_null_age)
print("------------")

#Fill Null Values with the Mean of a Column
df['Age']= df['Age'].fillna(df['Age'].mean())
df['Salary']= df['Salary'].fillna(df['Salary'].mean())
print(df)
print("------------")

#Fill Null Values with the Median of a Column
df['Age']= df['Age'].fillna(df['Age'].median())
df['Salary']= df['Salary'].fillna(df['Salary'].median())
print(df)
print("------------")

#Drop Columns with Null Values
df_no_null_coloumn = df.dropna(axis=1)
print(df_no_null_coloumn)
print("------------")

#Drop Columns with More Than 50% Null Values
shresold = len(df)*0.5
df_no_null_coloumn_50 = df.dropna(thresh= shresold,axis=1)
print(df_no_null_coloumn_50)
print("------------")

#Count Duplicates
duplicate_count = df.duplicated().sum()
print(duplicate_count)
print("------------")

#Count Null Values
null_count = df.isnull().sum()
print(null_count)
print("------------")

#Count Unique Values
unique_count = df['Name'].nunique()
print(unique_count)
print("------------")

#Replace Null Values with Forward Fill
df_ffill = df.fillna(method='ffill')
print(df_ffill)
print("------------")

#replace Null values with backword fill
df_bfill = df.fillna(method='bfill')
print(df_bfill)
print("------------")
