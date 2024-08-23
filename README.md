### DEVELOPED BY: S JAIGANESH
### REGISTER NO: 212222240037
### DATE: 

# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA


## AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
## ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
## PROGRAM:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

### Load the data
data = pd.read_csv('coffee_sales.csv')

### Convert 'date' to datetime format
data['date'] = pd.to_datetime(data['date'])

### Group by date and calculate the average money spent per day
daily_average = data.groupby('date')['money'].mean().reset_index()

### Log transformation
daily_average['Log_Money'] = np.log(daily_average['money'])

### Regular differencing
daily_average['Diff_Log_Money'] = daily_average['Log_Money'].diff()

### Seasonal differencing (assuming daily data with weekly seasonality, period=7)
daily_average['Seasonal_Diff_Log_Money'] = daily_average['Log_Money'].diff(7)

### Plotting
plt.figure(figsize=(14, 12))

### Original data
plt.subplot(4, 1, 1)
plt.plot(daily_average['date'], daily_average['money'], label='Original')
plt.title('Original Data')
plt.ylabel('Average Money')
plt.grid()

### Log transformed data
plt.subplot(4, 1, 2)
plt.plot(daily_average['date'], daily_average['Log_Money'], label='Log Transformed', color='orange')
plt.title('Log Transformed Data')
plt.ylabel('Log(Average Money)')
plt.grid()

### Regular differenced data
plt.subplot(4, 1, 3)
plt.plot(daily_average['date'], daily_average['Diff_Log_Money'], label='Differenced', color='green')
plt.title('Differenced Log Data')
plt.ylabel('Diff(Log(Average Money))')
plt.grid()

### Seasonally differenced data
plt.subplot(4, 1, 4)
plt.plot(daily_average['date'], daily_average['Seasonal_Diff_Log_Money'], label='Seasonally Differenced', color='red')
plt.title('Seasonally Differenced Log Data')
plt.ylabel('Seasonal Diff(Log(Average Money))')
plt.grid()

plt.tight_layout()
plt.show()
```

## OUTPUT:

ORIGINAL DATA: 
![image](https://github.com/user-attachments/assets/7114c3dc-4ce8-48c2-bbbe-185d47deb1e2)


REGULAR DIFFERENCING:
![image](https://github.com/user-attachments/assets/58cd43ed-f7a5-4636-9bf0-fee1bbb8b916)


SEASONAL ADJUSTMENT:
![image](https://github.com/user-attachments/assets/9bf9a420-e1ba-449e-80fc-d7cda1788c78)


LOG TRANSFORMATION:
![image](https://github.com/user-attachments/assets/50639d5a-caab-4147-842e-db5dc7fa1586)



## RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
