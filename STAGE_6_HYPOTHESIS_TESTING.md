# STAGE 6 HYPOTHESIS TESTING
STATISTICAL TEST:
* One way ANOVA: There is a significant difference in SOMETHING among TWO or MORE groups.
* Pearson Correlation Test: There is a significant RELATIONSHIP between/among NUMERIC variables.
* Regression analysis: There is a significant IMPACT/INFLUENCE/AFFECT of one or more variables to another variable.
## 1. ONE-WAY ANOVA
### Is there any significant difference in the cost of goods sold among the three types of devices used by the customers while placing an order?
```
# For finding significant difference in SOMETHING among TWO or MORE groups we use ONE-WAY ANOVA
final_df['yeo_cost'] = yeo_cost

# Create sample data for three or more groups (replace this with your actual data)
PC_data = final_df[final_df['device_type'] == 'PC']
Tab_data = final_df[final_df['device_type'] == 'Tablet']
Mob_data = final_df[final_df['device_type'] == 'Mobile']

# Perform one-way ANOVA
f_statistic, p_value = stats.f_oneway(PC_data['yeo_cost'], Tab_data['yeo_cost'], Mob_data['yeo_cost'])

# Print the results
print("One-way ANOVA F-statistic:", f_statistic)
print("P-value:", p_value)

# Determine if the results are statistically significant
alpha = 0.05  # Significance level
if p_value < alpha:
    print("Reject the null hypothesis: There is a significant difference among the groups.")
else:
    print("Fail to reject the null hypothesis: There is no significant difference among the groups.")
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/d7298ba5-ffea-4cec-ad71-ebd32e0beb01)

## 2. PEARSON CORRELATION TEST
### Is there any statistically significant relationship between order value, cost and refund?
```
# For finding significant RELATIONSHIP between/among NUMERIC variables we use PEARSON CORRELATION TEST
# PEARSON CORRELATION follows only two variable so for 3 variable we use:

# Perform Pearson correlation tests
correlation1, p_value1 = stats.pearsonr(boxcox_orderval, yeo_cost)
correlation2, p_value2 = stats.pearsonr(boxcox_orderval, final_df['refund'])
correlation3, p_value3 = stats.pearsonr(final_df['refund'], yeo_cost)

# Print the correlation coefficients and p-values
print("Correlation between order value and cost:", correlation1)
print("P-value:", p_value1)
print("Correlation between order value and refund:", correlation2)
print("P-value:", p_value2)
print("Correlation between cost and refund:", correlation3)
print("P-value:", p_value3)

# Determine if the correlations are statistically significant
alpha = 0.05  # Significance level
if p_value1 < alpha:
    print("Correlation between order value and cost is statistically significant.")
else:
    print("Correlation between  order value and cost is not statistically significant.")

if p_value2 < alpha:
    print("Correlation between order value and refund is statistically significant.")
else:
    print("Correlation between order value and refund is not statistically significant.")

if p_value3 < alpha:
    print("Correlation between cost and refund is statistically significant.")
else:
    print("Correlation between cost and refund is not statistically significant.")
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/240f8278-b93e-48cd-a7ce-e43599c19c8a)

## 3. MULTIPLE REGRESSION
### Is there any significant impact of order value and cost on the refund amount?
```
import statsmodels.api as sm

# Add a constant term to the independent variables
X = sm.add_constant(np.column_stack((boxcox_orderval, yeo_cost)))

# Fit the linear regression model
model = sm.OLS(final_df['refund'], X).fit()

# Get the regression coefficients
coefficients = model.params

# Print the regression results
print("Regression Coefficients:")
print("Intercept:", coefficients[0])
print("Order Value Coefficient:", coefficients[1])
print("Cost Coefficient:", coefficients[2])

# Print the summary of the regression model
print("\nRegression Summary:")
print(model.summary())
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/1faa3759-9574-4ef2-838e-8c945b925d76)
