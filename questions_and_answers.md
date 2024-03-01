# Stage 1: Data Cleaning
## 1. Import Data
Once Pandas is installed, import it in your applications by adding the import keyword:
```
import pandas as pd
```
Load Excel data into a pandas DataFrame
```
df = pd.read_excel(r"H:\Data Analyst\Udemy - Data Analysis A-Z - Become Data Analyst in 30 Days\3. Stage 1 Data Cleaning A - Z\Practice datasets\sales data.xlsx")
```
Now, you can work with the data in the 'df' DataFrame

For example, you can print the first few rows of the DataFrame
```
df.head()
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/50a78a4b-1322-4580-8e6c-13aa38b38e19)

## 2. Missing Values / Simpleimputer
Check for missing values in the entire DataFrame
```
missing_values = df.isnull().sum()
```
To check for missing values in a specific column, you can use:
```
missing_values = df['column_name'].isnull().sum()
```
Print the columns with missing values and their respective counts
```
print("Missing Values:")
print(missing_values[missing_values > 0])
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/76c5cee0-1cb0-4ee2-81d4-d7e44976647a)

Univariate imputer for completing missing values with simple strategies.
```
target_column = 'order_value_EUR'
```
Create a SimpleImputer instance to impute missing values with a strategy (e.g., 'mean', 'median', 'most_frequent')

Other strategies include 'constant' to replace missing values with a constant value
```
imputer = SimpleImputer(strategy='median')
```
Fit the imputer on the selected column and transform it to impute missing values
```
df[target_column] = imputer.fit_transform(df[[target_column]])
```
To find missing value
```
df.isnull().sum()
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/6ba3f397-e0fd-47ad-98b9-d4a983b41d09)

```
df.device_type.describe()
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/5ceb75fa-6fc4-4b4f-8a33-82125908c2b4)

```
target_column = 'device_type'
```
Create a SimpleImputer instance to impute missing values with a strategy (e.g., 'mean', 'median', 'most_frequent')

Other strategies include 'constant' to replace missing values with a constant value
```
imputer = SimpleImputer(strategy='most_frequent')
```
Fit the imputer on the selected column and transform it to impute missing values
```
df.device_type = imputer.fit_transform(df['device_type'].values.reshape(-1,1))[:,0]
```
To find missing value
```
df.isnull().sum()
```
We can see no missing value

![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/7d903169-3c6c-4e9e-966e-30d23a181c52)

## 3. Dealing with Inconsistant Values/ Change DataType
To check various data types
```
df.dtypes
```
Identify Inconsistent value in 'cost' column
Sample variable containing mixed data
```
mixed_data = df['cost']
```
Create an empty list to store non-numeric values
```
non_numeric_values= []
```
Iterate through the elements in the variable
```
for value in mixed_data:
    if isinstance(value,str) and not value.isnumeric():
        non_numeric_values.append(value)
```
Print the non-numeric values
```
print("Non-Numeric Values:")
print(non_numeric_values)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/02818322-9b13-4ff2-93f3-046743877832)

Select rows from a dataframe based on column value (ie XXX in 'cost' column)
```
df_new = df[df['cost'] == 'XXX']
print(df_new)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/e12a003c-4f4c-4014-bfce-0f4fd4731cab)

## 4. Remove non-numeric rows in one column with pandas
Using pd.to_numeric

This will coerce all non-numeric values to NaN, which will then be flagged as False using notnull(). 

Other numeric values will be converted to True.
```
df = df[pd.to_numeric(df['cost'], errors='coerce').notnull()]
df
```
Another Method to remove miss-identified data
```
mask = (df['cost'] == 'XXX')
```
Remove rows that match the mask
```
df = df[~mask]
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/3df1bd99-06df-491c-b447-60dc45cabd25)

### Convert DataType

To Convert DataType of 'cost' from object to float
```
df['cost'] =df['cost'].astype(float)
```
To Convert DataType of 'date' from object to datetime64

Here we need to assign datetime64[ns] in ''
```
df['date'] = df['date'].astype('datetime64[ns]')
```
```
df.dtypes
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/443c532b-76eb-412b-ba8b-bd36b63b4f2a)

Data type changed

## 5. Remove Duplicates
Identify Duplicates
```
duplicates = df[df.duplicated()]
```
Print Duplicate rows
```
print("Duplicated Rows:")
print(duplicates)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/bd99bf50-6d20-4f53-9fce-f3bbf85ab265)

Remove Duplicates and keeping df as it is
```
df_no_duplicates = df.drop_duplicates()
df_no_duplicates
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/3ab18461-b147-4eb6-87e0-0092f6d171dd)

```
cleaned_data = df_no_duplicates
cleaned_data.head(10)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/9b07eb60-30c8-4404-a9f7-9169ac8c2274)
