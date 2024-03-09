# STAGE 2: Data Manipulation
## 1. Sorting
* The `sort_values()` method sorts the DataFrame by the specified label.
```
df_sorted = cleaned_data.sort_values(by = 'cost')
df_sorted
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/d2797516-7b50-481b-aa39-e41df83dda06)

## 2. Conditional Formating
```
df_filter = df[(df['country'] == 'Germany') & (df['category'] == 'Games')]
df_filter
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/6fe91432-f470-4533-802a-591df1725f39)

```
Not_Germany_df = df[df['country'] != 'Germany']
Not_Germany_df
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/2f253361-0540-4a28-a8ac-cca04800498d)

## 3. Data Merging
* Load Excel data('Extra Variable.xlsx') into a pandas DataFrame
```
extra_vars = pd.read_excel(r"H:\Data Analyst\Udemy - Data Analysis A-Z - Become Data Analyst in 30 Days\3. Stage 1 Data Cleaning A - Z\Practice datasets\Extra Variable.xlsx")
extra_vars
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/099ccab6-e818-4a49-b9ee-18f5ca88d28a)

* The`merge()` method updates the content of two DataFrame by merging them together, using the specified method(s).
* Merge 'cleaned_data' with 'extra_vars' on 'order_id'
```
merged_df = cleaned_data.merge(extra_vars, on = 'order_id')
merged_df
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/1bbb0dd0-b756-4763-87af-5dea6df61f94)

## 4. Data Concatenate
* Load Excel data('Extra Data.xlsx') into a pandas DataFrame
```
extra_data = pd.read_excel(r"H:\Data Analyst\Udemy - Data Analysis A-Z - Become Data Analyst in 30 Days\3. Stage 1 Data Cleaning A - Z\Practice datasets\Extra Data.xlsx")
extra_data
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/c09413b5-8652-4d66-bc73-0d194f5d1c23)

* The `concat()` function is used to concatenate pandas objects along a particular axis with optional set logic along the other axes.
```
final_df = pd.concat([merged_df, extra_data], ignore_index=True)
final_df
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/b07bbc90-d193-4217-9d5e-b250d49c39d2)

