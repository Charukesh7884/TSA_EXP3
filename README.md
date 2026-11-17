# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
### Date: 31/10/2026

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

data = pd.read_csv('NVIDIA_STOCK.csv', skiprows=2, header=None)

data.columns = ['Date', 'Adj Close', 'Close', 'High', 'Low', 'Open', 'Volume']

data = data['Close'].dropna().values

N = len(data)

lags = range(35)

autocorr_values = []

mean_data = np.mean(data)

variance_data = np.var(data)

normalized_data = (data - mean_data) / np.sqrt(variance_data)

for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)

plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation of Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```
### OUTPUT:
<img width="1163" height="710" alt="image" src="https://github.com/user-attachments/assets/6d745a57-1d1a-41c5-9d49-9b68e7f9e189" />


### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
