### Developed by: Ragavendran A
### Reg.no: 212222230114
### Date: 
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION

### AIM:
To Illustrates how to perform time series analysis and decomposition on the Summer olympic medals.

### ALGORITHM:
1. Load the dataset and inspect the columns and initial rows.
2. Convert the 'Year' column to datetime format and set it as the index.
3. Create the 'Total_Medals' column if it doesn't exist by summing 'Gold', 'Silver', and 'Bronze'.
4. Perform seasonal decomposition on the 'Total_Medals' data.
5. Plot and display the original data, seasonal component, trend component, and residuals.
### PROGRAM

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the dataset (replace the path with the correct file path)
df = pd.read_csv('/content/Summer_olympic_Medals.csv')

# Print column names to find the correct column for analysis
print("Available columns in the dataset:", df.columns)

# Inspect the first few rows to understand the dataset structure
print(df.head())

# Convert the 'Year' column to datetime format and set it as the index
df['Year'] = pd.to_datetime(df['Year'], format='%Y')
df.set_index('Year', inplace=True)

# Assuming 'Total_Medals' is the column with the number of medals (adjust based on your dataset)
# If there is no 'Total_Medals' column, sum the gold, silver, and bronze columns to create it
if 'Total_Medals' not in df.columns:
    df['Total_Medals'] = df['Gold'] + df['Silver'] + df['Bronze']

# Now, proceed with the 'Total_Medals' column
medal_data = df['Total_Medals']

# Perform seasonal decomposition directly with the data's existing index
decomposition = seasonal_decompose(medal_data, model='additive', period=4)  # Assuming 4-year Olympic cycles

trend = decomposition.trend
seasonal = decomposition.seasonal
residuals = decomposition.resid

# Plot the original time series data (Total Medals)
plt.figure(figsize=(12, 6))
plt.plot(medal_data, label='Original Medals Data')
plt.title('Original Total Medals Data')
plt.legend()
plt.show()

# Plot the seasonal component
plt.figure(figsize=(12, 6))
plt.plot(seasonal, label='Seasonal Component', color='orange')
plt.title('Seasonal Component')
plt.legend()
plt.show()

# Plot the trend component
plt.figure(figsize=(12, 6))
plt.plot(trend, label='Trend Component', color='green')
plt.title('Trend Component')
plt.legend()
plt.show()

# Plot the residuals
plt.plot(residuals, label='Residuals', color='red')
plt.legend(loc='best')
plt.tight_layout()
plt.show()





```





### OUTPUT:
#### FIRST FIVE ROWS:
![image](https://github.com/user-attachments/assets/b6059ce6-ef2f-4c9f-8123-62a06a0b585b)



#### PLOTTING THE DATA:

![image](https://github.com/user-attachments/assets/40f1e373-8131-4076-985f-09380bba1b28)


#### SEASONAL PLOT REPRESENTATION :


![image](https://github.com/user-attachments/assets/3b4c560f-1169-4531-8389-1d2a16572109)

#### TREND PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/57e5e8c7-34ce-4920-8779-959b40caca9c)



#### OVERALl REPRESENTATION:

![image](https://github.com/user-attachments/assets/6ce95797-8d4f-4f8a-a181-832e1d330e9f)


### RESULT:
Thus the python code for the time series analysis and decomposition was created successfully.
