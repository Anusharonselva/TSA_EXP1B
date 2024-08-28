# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 
# Developed by: ANUSHARON.S
# Register no: 212222240010
### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.stattools import adfuller


df = pd.read_csv('/content/Paris 2024 Olympics Nations Medals.csv')


time_series = df['Total'] 



def check_stationarity(series, title="Time Series"):
    result = adfuller(series)
    print(f"{title}:")
    print(f'ADF Statistic: {result[0]}')
    print(f'p-value: {result[1]}')
    if result[1] <= 0.05:
        print("The series is stationary\n")
    else:
        print("The series is non-stationary\n")

diff_series = time_series.diff().dropna()

log_series = np.log(time_series.replace(0, np.nan)).dropna()

seasonal_adjustment = time_series.diff(12).dropna()


plt.figure(figsize=(15, 10))

plt.subplot(4, 1, 1)
plt.plot(time_series, label='Original Series')
plt.title('Original Time Series')
plt.legend()

plt.subplot(4, 1, 2)
plt.plot(diff_series, label='Differenced Series', color='orange')
plt.title('Differenced Time Series')
plt.legend()

plt.subplot(4, 1, 3)
plt.plot(log_series, label='Log Transformed Series', color='green')
plt.title('Log Transformed Time Series')
plt.legend()

plt.subplot(4, 1, 4)
plt.plot(seasonal_adjustment, label='Seasonal Adjustment', color='red')
plt.title('Seasonally Adjusted Time Series')
plt.legend()

plt.tight_layout()
plt.show()

print("Original Series ADF Test:")
check_stationarity(time_series, "Original Series")

print("Differenced Series ADF Test:")
check_stationarity(diff_series, "Differenced Series")

print("Log Transformed Series ADF Test:")
check_stationarity(log_series, "Log Transformed Series")

print("Seasonally Adjusted Series ADF Test:")
check_stationarity(seasonal_adjustment, "Seasonally Adjusted Series")

```
### OUTPUT:
ORIGINAL TIME SERIES: 
![Screenshot 2024-08-28 091811](https://github.com/user-attachments/assets/0459b13f-7474-49cb-8d24-2f3bcd84eabc)

 DIFFERENCED TIME SERIES:

![Screenshot 2024-08-28 091857](https://github.com/user-attachments/assets/7bd7262f-5f47-4487-8ee2-5f47d162738d)

SEASONAL ADJUSTMENT:
![Screenshot 2024-08-28 091949](https://github.com/user-attachments/assets/b1463f12-c446-4497-87e5-edcb47fac672)


LOG TRANSFORMATION:

![Uploading Screenshot 2024-08-28 092017.png…]()


### RESULT:
Thus the python code for the conversion of non stationary to stationary data on international airline passenger
data is created.
