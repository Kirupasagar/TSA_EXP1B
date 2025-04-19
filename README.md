# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

data = pd.read_csv('rainfall.csv')

print("Column Names:", data.columns)

date_column = 'date'
humidity_column = 'humidity'

x = data[date_column]
y = data[humidity_column]

plt.figure(figsize=(10, 5))
plt.xlabel('Date')
plt.ylabel(humidity_column)
plt.plot(x, y, label="Original Data")
plt.legend()
plt.show()

data['diff'] = data[humidity_column].diff()
data.dropna(inplace=True)

x = data[date_column]
y = data['diff']
plt.figure(figsize=(10, 5))
plt.xlabel('Date')
plt.ylabel('Differenced Data')
plt.plot(x, y, label="Differenced Data", color='r')
plt.show()

data['SeasonalAdjustment'] = data[humidity_column] - data[humidity_column].rolling(window=12).mean()
data.dropna(inplace=True)

x = data[date_column]
y = data['SeasonalAdjustment']
plt.figure(figsize=(10, 5))
plt.xlabel('Date')
plt.ylabel('Seasonally Adjusted Data')
plt.plot(x, y, label="Seasonal Adjustment", color='g')
plt.show()

data['log'] = np.log(data['diff'])
data.dropna(inplace=True)

x = data[date_column]
y = data['log']
plt.figure(figsize=(10, 5))
plt.xlabel('Date')
plt.ylabel('Log Transformed Data')
plt.plot(x, y, label="Log Transformation", color='m')
plt.show()

### OUTPUT:
![Screenshot 2025-04-19 152308](https://github.com/user-attachments/assets/c43b09a2-4cf6-48a6-86e5-fcc908fcd347)


REGULAR DIFFERENCING:
![Screenshot 2025-04-19 152332](https://github.com/user-attachments/assets/d170d59a-01a0-4b59-954b-175365b4e6d9)



SEASONAL ADJUSTMENT:
![Screenshot 2025-04-19 152349](https://github.com/user-attachments/assets/c16f4551-0b93-43a1-9497-056b16f680d1)





LOG TRANSFORMATION:
![Screenshot 2025-04-19 152401](https://github.com/user-attachments/assets/39091766-65a4-4c1b-8a16-7eeb10f9d1c3)




### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
