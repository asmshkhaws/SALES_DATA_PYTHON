# STAGE 4 STATISTICAL DATA ANALYSIS

## Detecting Normality
* A kernel density estimate (KDE) plot is a method for visualizing the distribution of observations in a dataset, analogous to a histogram.
* KDE plot is implemented through the `kdeplot` function in Seaborn `sns`.
```
# Create subplots for the KDE plots
fig, ax = plt.subplots(figsize=(10, 5))

# Plot the order KDE plot
sns.kdeplot(final_df['order_value_EUR'], label="Order Value", fill=True)

# Plot the cost KDE plot
sns.kdeplot(final_df['cost'], label="Cost", fill=True)

# Plot the refund KDE plot
sns.kdeplot(final_df['refund'], label="Refund", fill=True)

# Set plot title and labels
plt.title('KDE Plots for Three Numeric Variables')
plt.xlabel('Value')
plt.ylabel('Density')

# Add a legend
plt.legend()

# Show the plot
plt.show()
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/e5a6d6db-91cb-4ddf-8335-8eba6d549a88)
