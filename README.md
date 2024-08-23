### Developed By: ABISHEK XAVIER A
### Register No: 212222230004
### Date:

# Ex.No: 1B CONVERSION OF NON STATIONARY TO STATIONARY DATA


## AIM:
To perform regular differncing,seasonal adjustment and log transformatio on sales of furniture store

## ALGORITHM:
```
1.Load and preprocess the data by filtering for furniture sales 
2.Apply log transformation to the sales data to stabilize variance.
3.Perform regular differencing on the log-transformed data to remove trends.
4.Conduct seasonal differencing on the differenced series to eliminate seasonality.
5.Check for stationarity using the ADF test and visualize the final stationary time series.
```

## PROGRAM:
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the data
data = pd.read_csv("/content/Super_Store_data.csv",encoding='ISO-8859-1')
# Create DataFrame
df = pd.DataFrame(data)

# Regular differencing
df['Regular Difference'] = df['Sales'].diff()

# Seasonal adjustment
result = seasonal_decompose(df['Sales'], model='additive', period=12)
df['Seasonal Adjustment'] = result.resid

# Log transformation
df['Log Transformation'] = np.log(df['Sales'])

# Plotting
plt.figure(figsize=(14, 10))

plt.subplot(4, 1, 1)
plt.plot(df['Sales'], label='Original')
plt.legend(loc='best')
plt.title('Original Data')

plt.subplot(4, 1, 2)
plt.plot(df['Regular Difference'], label='Regular Difference')
plt.legend(loc='best')
plt.title('Regular Differencing')

plt.subplot(4, 1, 3)
plt.plot(df['Seasonal Adjustment'], label='Seasonal Adjustment')
plt.legend(loc='best')
plt.title('Seasonal Adjustment')

plt.subplot(4, 1, 4)
plt.plot(df['Log Transformation'], label='Log Transformation')
plt.legend(loc='best')
plt.title('Log Transformation')

plt.tight_layout()
plt.show()
```
## OUTPUT:
![Screenshot 2024-08-23 221711](https://github.com/user-attachments/assets/ffd8e051-90ec-4f76-b28e-ff9e49d34638)
![Screenshot 2024-08-23 221729](https://github.com/user-attachments/assets/93341a28-89cc-40cc-b8a6-ef6e44c6066e)


# RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on sales of furniture store
