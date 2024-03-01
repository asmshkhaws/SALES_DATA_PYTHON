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
