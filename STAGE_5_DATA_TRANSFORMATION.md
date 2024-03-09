# STAGE 5 DATA TRANSFORMATION
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/e5a6d6db-91cb-4ddf-8335-8eba6d549a88)
* It was observed that `cost` & `order value` column had data which were positively skewed distributed.
* Numerical variables may have high skewed and non-normal distribution caused by outliers, highly exponential distributions, etc.
* Therefore we go for data transformation.

__Method of data transformation__
  1. Square-Root
  2. Logrithmic
  3. Box-Cox
  4. Yeo-Johnson

## 1. SQUARE ROOT TRANSFORMATION
* This transformation will give a moderate effect on distribution.
* The main advantage of square root transformation is, it can be applied to zero values.

```
#Square root
import numpy as np

# Apply the square root transformation
sqrt_order = np.sqrt(final_df['order_value_EUR'])
sns.kdeplot(sqrt_order, fill=True)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/eefe6b6c-168b-46dd-8466-7b4adcb55bc8)

```
sqrt_cost = np.sqrt(final_df['cost'])
sns.kdeplot(sqrt_cost, fill=True)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/0d9aabce-1668-486c-9382-bc25795991e2)

```
sqrt_refund = np.sqrt(final_df['refund'])
sns.kdeplot(sqrt_refund, fill=True)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/41b563ab-57d4-4c62-b701-f3e252d8b8e4)

## 2. LOGRITHMIC METHOD TRANSFORMATION
* In Log transformation each variable of x will be replaced by log(x) with base 10, base 2, or natural log.
```
#Logarithmic

# Apply the log transformation
log_orderval = np.log(final_df['order_value_EUR'])

sns.kdeplot(log_orderval, fill=True)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/80ec6149-ad97-4c53-bc8e-a1c1d080c9f9)

```
log_cost = np.log(final_df['cost'])
sns.kdeplot(log_cost, fill=True)
```

![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/af3e72d7-3c5a-48b6-bc70-389c8a5bae78)

```
log_refund = np.log(final_df['refund'])
sns.kdeplot(log_refund, fill=True)
```

![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/ea4e1434-67ec-4650-9f9f-e691d0ad47da)

## 3. BOX-COX TRANSFORMATION
* Box-cox transformation works pretty well for many data natures.
```
#Box - cox
from scipy import stats

# Apply the Box-Cox transformation
boxcox_orderval, lambda_value = stats.boxcox(final_df['order_value_EUR'])
sns.kdeplot(boxcox_orderval, fill=True)
```

![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/99b3b813-5854-4859-ae43-9625c05a9a1c)

```
boxcox_cost, lambda_value = stats.boxcox(final_df['cost'])
sns.kdeplot(boxcox_cost, fill=True)
```

![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/88f723ad-6fde-438e-abc9-89839c70e10e)

```
boxcox_refund, lambda_value = stats.boxcox(final_df['refund'])
sns.kdeplot(boxcox_refund, fill=True)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/77db78b5-185d-48e3-958d-7066603eb80b)

## 4. YEO-JOHNSON TRANSFORMATION
* This is one of the older transformation technique which is very similar to Box-cox transformation but does not require the values to be strictly positive.

```
#Yeo - Johnson

# Apply the Yeo-Johnson transformation
yeo_orderval, lambda_value = stats.yeojohnson(final_df['order_value_EUR'])
sns.kdeplot(yeo_orderval, fill=True)
```
![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/72510818-0be6-4759-8f4a-2be15f072668)

```
yeo_cost, lambda_value = stats.yeojohnson(final_df['cost'])
sns.kdeplot(yeo_cost, fill=True)
```

![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/2c7d19b5-33e9-4f90-8a4b-6026c9d84b95)

```
yeo_refund, lambda_value = stats.yeojohnson(final_df['refund'])
sns.kdeplot(yeo_refund, fill=True)
```

![image](https://github.com/asmshkhaws/SALES_DATA_PYTHON/assets/119579424/ddc4169e-46e6-4467-bb37-9ddaa26da54f)
