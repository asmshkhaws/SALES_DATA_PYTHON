## 1. Exploring VALUE_COUNTS analysis method
### What is the primary country of residence for the majority of our customers?
* `value_counts()`:	Returns the number of unique rows
```
country_frequency = final_df['country'].value_counts()
country_frequency
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/0a90f034-cd84-40be-a73a-9db874cc3f6b)

* `matplotlib.pyplot` creates a figure, creates a plotting area in a figure, plots some lines in a plotting area, decorates the plot with labels, etc.
```
import matplotlib.pyplot as plt
```
* Create a bar plot for the `'country_frequency'`
* Pandas uses the plot() method to create diagrams.
```
country_frequency.plot(kind='bar', color='skyblue', edgecolor='black', figsize=(8, 5))
plt.title('The primary country of residence for the majority of our customers')
plt.xlabel('Country')
plt.ylabel('Frequency')
# plt.xticks(rotation=90) # Rotate x-axis labels if needed
plt.show()
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/73d018f8-d07c-4603-b456-457394c9e832)

### Which product category has the highest frequency of sales?
```
productcat_frequency = final_df['category'].value_counts()
productcat_frequency
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/f9b2dbe0-350d-4948-81ba-fa5203bcd24f)

Create a bar plot for the 'country_frequency'

```
productcat_frequency.plot(kind = 'bar', color = 'orange', edgecolor = 'darkblue', figsize = (8,5))
plt.title('The product category has the highest frequency of sales')
plt.xlabel('Product Category')
plt.ylabel('Frequency')
plt.show()
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/c95c432c-adfb-47a5-820e-fff29dc84c80)

### Identify the top 5 customers with the most repeat purchases.
```
top_5_customers_frequency = final_df['customer_name'].value_counts().head(5)
top_5_customers_frequency
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/ff5418e8-8f08-41c7-ae9b-48dbf0f5a0fb)

### Who among the sales managers has achieved the highest number of sales?
```
salesman_frequency = final_df['sales_manager'].value_counts()
salesman_frequency
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/f19c63d5-a620-4c83-a6b3-accac8bed2fc)

### Who are the top 5 sales representatives with the highest number of sales?
```
salesrep_frequency = final_df['sales_rep'].value_counts()
salesrep_frequency
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/37bf58e6-5aaf-4661-8316-7fd7af8783b9)

### Which device is predominantly used for making product purchases?
```
devtype_frequency = final_df['device_type'].value_counts()
devtype_frequency
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/bc6bc608-f9f0-4649-b881-508ababf1729)

* A Percentage is calculated by the mathematical formula of dividing the value by the sum of all the values and then multiplying the sum by 100.
* This is also applicable in Pandas Dataframes.

  `df[percent] = (df['column_name'] / df['column_name'].sum()) * 100`
  ```
  # Calculate relative frequencies (percentages)
  devtype_percent = (devtype_frequency*100)/devtype_frequency.sum()
  devtype_percent
  
  # Create a pie chart for the percentages
  devtype_percent.plot(kind ='pie', labels=devtype_percent.index, autopct='%1.1f%%', startangle=140, figsize=(7.50, 3.50))
  
  plt.title('The device is predominantly used for making product purchases')
  plt.axis('equal')  # Equal aspect ratio ensures that pie is drawn as a circle.
  plt.legend(title = "Products:", loc="best")
  
  # Show the pie chart
  plt.show()
  ```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/b9de2d33-ef8c-4ce8-a4d2-8d05e3811343)

## 2. DESCRIPTIVE ANALYSIS METHOD
### Find the descriptives of order value, cost and refund.
* The `describe()` method returns description of the data in the DataFrame.
```
numeric_columns = ['order_value_EUR', 'cost', 'refund']
numeric_summery = final_df[numeric_columns].describe()
numeric_summery
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/0ac26e1a-6039-4404-b2cb-4452828073e1)

* With the `subplot()` function you can draw multiple plots in one figure:

  The `subplot()` function takes three arguments that describes the layout of the figure.

    `plt.subplot(1, 2, 1)`

  The layout is organized in rows and columns, which are represented by the first and second argument.

  The third argument represents the index of the current plot.
* `Seaborn`: provides a high-level interface for drawing attractive and informative statistical graphics.
* With Seaborn, histograms are made using the `histplot` function.

  You can add a kde curve to a histogram by setting the `kde` argument to True.
  
```
import seaborn as sns

# Create a figure with three subplots for the numeric variables
plt.figure(figsize=(12, 4))

# Plot the distribution of 'order_value_EUR' in the first subplot
plt.subplot(131) # 1 row, 3 columns, first subplot
sns.histplot(final_df['order_value_EUR'], kde=True)
plt.title('Order value Distribution')

# Plot the distribution of 'cost' in the first subplot
plt.subplot(132) # 1 row, 3 columns, second subplot
sns.histplot(final_df['cost'], kde = True)
plt.title('Cost Distribution')

# Plot the distribution of 'refund' in the first subplot
plt.subplot(133) # 1 row, 3 columns, third subplot
sns.histplot(final_df['refund'], kde=True)
plt.title('Refund Distribution')

# Adjust layout and show the figure
plt.tight_layout()
plt.show()
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/c23856e1-2ecd-4908-bd05-0c8fca6660c9)

* Box Plot is the visual representation of the depicting groups of numerical data through their quartiles.

  Boxplot is also used for detect the outlier in data set. 
```
# Create a figure with three subplots for the boxplot
plt.figure(figsize=(12, 4))

# Plot the distribution of 'order_value_EUR' in the first subplot
plt.subplot(131) # 1 row, 3 columns, first subplot
sns.boxplot(data = final_df['order_value_EUR'])
plt.title('Order value Distribution')

# Plot the distribution of 'cost' in the first subplot
plt.subplot(132) # 1 row, 3 columns, second subplot
sns.boxplot(data = final_df['cost'])
plt.title('Cost Distribution')

# Plot the distribution of 'refund' in the first subplot
plt.subplot(133) # 1 row, 3 columns, third subplot
sns.boxplot(data = final_df['refund'])
plt.title('Refund Distribution')

# Adjust layout and show the figure
plt.tight_layout()
plt.show()
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/669cbf15-4b61-40b5-8eb2-7ec04b2269a3)

## 3. GROUPBY
### Identify the top 3 product categories based on both order value and cost.
* The `groupby()` method allows you to group your data and execute functions on these groups.
```
median_order_value = final_df.groupby('category')['order_value_EUR'].median()
median_order_value.sort_values(ascending = False)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/1d250075-b7db-412d-9dac-c83f46665ec0)

```
median_cost_values = final_df.groupby('category')['cost'].median()
median_cost_values.sort_values(ascending = False)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/3cca7db7-b369-4950-b409-bbf68352efd8)

### Determine the top 3 customers who contribute the most to profitability and have the highest expenses.
```
median_customer_profitability = final_df.groupby('customer_name')['order_value_EUR'].median()
median_customer_profitability.sort_values(ascending=False)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/f0b9d449-7020-4133-bd8c-bfa821a285ce)

```
median_customer_expenses = final_df.groupby('customer_name')['cost'].median()
median_customer_expenses.sort_values(ascending=False)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/2bc33fde-2a69-4d0c-b598-6dce80177d4b)

### Which sales representative's transactions resulted in the highest amount of refunds to customers?
```
median_sal_rep_refund = final_df.groupby('sales_rep')['refund'].median()
median_sal_rep_refund.sort_values(ascending=False)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/7e8f427d-9659-4477-bbd4-0132252614bf)

## 4. PIVOT TABLE
### Who are the most loyal customers of your superstore?
* A pivot table in Pandas is a quantitative table that summarizes a large DataFrame, such as a large dataset.
```
# Create a pivot table based on median sales, cost, and counts for each product category
loyal_customer_pivot_table = final_df.pivot_table(index= 'customer_name',
                                                   values= ['order_value_EUR','cost'],
                                                    aggfunc={'customer_name':'count',
                                                             'order_value_EUR':'median', 
                                                             'cost':'median'})
# Rename the columns for clarity
loyal_customer_pivot_table = loyal_customer_pivot_table.rename(columns={'order_value_EUR': 'Median_Sales',
                                                                         'cost': 'Median_Cost',
                                                                         'customer_name': 'Count'})
# Print the pivot table
sorted_pivot_table = loyal_customer_pivot_table.sort_values(by = 'Count', ascending = False)
top_10 = sorted_pivot_table[0:10]
top_10
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/841fa17a-4229-4e92-88b9-786d5ba342b0)

```
# Create a figure with two subplots
fig, ax1 = plt.subplots(figsize=(30, 10))

# Plot the count in a line plot
sns.lineplot(data=top_10['Count'], marker='o', ax=ax1, color='tab:blue', label='Count')
ax1.set_xlabel('Customers Names')
ax1.set_ylabel('Count', color='tab:blue')
ax1.tick_params(axis='y', labelcolor='tab:blue')

# Create a second y-axis for the bar plots
ax2 = ax1.twinx()

# Plot the median sales and median cost in bar plots
bar_plot = top_10[['Median_Sales', 'Median_Cost']].plot(kind='bar', ax=ax2, width=0.3, color=['tab:orange', 'tab:green'], alpha=0.7)
ax2.set_ylabel('Values', color='black')
ax2.tick_params(axis='y', labelcolor='black')
bar_plot.set_xticklabels(top_10.index, rotation=90, ha='center')

# Customize the plot
plt.title('Median Sales, Cost, and Product Purchase by Customers')
ax2.legend(loc='upper left', labels=['Median Sales', 'Median Cost'])

# Show the plot
plt.show()
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/f1630c86-1992-41a6-a5fe-35d5be2fda21)

## 5. CROSSTABULATION
### Under which sales manager, which product category has the highest sales volume?
* CROSSTABULATION: help us to understand the relationship between two or more variable..
```
crosstab_sal_man = pd.crosstab(final_df['sales_manager'], final_df['category'])
crosstab_sal_man
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/0c2a2987-83de-4dc0-b432-134d4f8efd9f)

```
# Visualize the crosstabulation as a heatmap
plt.figure(figsize=(8, 6))
sns.heatmap(crosstab_sal_man, annot=True, cmap="YlGnBu", fmt='d', cbar=True)
plt.title('Crosstabulation Heatmap')
plt.xlabel('Product category')
plt.ylabel('Sales Managers')

# Show the plot
plt.show()
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/3cdbf36b-5f0e-4e85-9280-1146ce86d683)

### In which country did a particular sales representative achieve the highest sales volume?
```
crosstab_sal_rep = pd.crosstab(final_df['sales_rep'], final_df['country'])
crosstab_sal_rep
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/5d1a5508-29eb-4290-812f-065cbc7639f5)

```
# Visualize the crosstabulation as a heatmap
plt.figure(figsize=(8, 6))
sns.heatmap(crosstab_sal_rep, annot=True, cmap="YlGnBu", fmt='d', cbar=True)
plt.title('Crosstabulation Heatmap')
plt.xlabel('Product category')
plt.ylabel('Sales Managers')

# Show the plot
plt.show()
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/1da3a8a7-5199-4302-b1be-3f9c81fe833f)

## 6. CORRELATION
### Find the relationship between order value, cost and refund amount.
* The `corr()` method finds the correlation of each column in a DataFrame.
```
# Calculate the correlation matrix
correlation_matrix = final_df[['order_value_EUR','cost','refund']].corr()
correlation_matrix
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/05781858-0a6d-49a8-ba7e-84b33dafd3b1)

```
# Visualize the correlation matrix as a heatmap
plt.figure(figsize=(8, 6))
sns.heatmap(correlation_matrix, annot=True, cmap="coolwarm", linewidths=0.5)
plt.title('Correlation Matrix')
plt.show()
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/76814b8f-ebde-4684-b78d-1892facd01d8)
