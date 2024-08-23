### Developed By : Shriram S
### Register No. 212222240098
###  Date:

# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
Date:
### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

### ALGORITHM:
Import necessary libraries (NumPy, Matplotlib)

Load the dataset

Calculate the linear trend values using least square method

Calculate the polynomial trend values using least square method

End the program

### PROGRAM:

```py
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import PolynomialFeatures
import numpy as np
```
```py
data = pd.read_csv('/content/prices.csv')
```

```py
data['Price Dates'] = pd.to_datetime(data['Price Dates'], format='%d-%m-%Y')
```

```py
X = np.array(data.index).reshape(-1, 1)
y = data['Methi']
```

```py
linear_regressor = LinearRegression()
linear_regressor.fit(X, y)
y_pred_linear = linear_regressor.predict(X)
```

```py
poly = PolynomialFeatures(degree=2)
X_poly = poly.fit_transform(X)
```

```py
poly_regressor = LinearRegression()
poly_regressor.fit(X_poly, y)
y_pred_poly = poly_regressor.predict(X_poly)
```

```py
plt.figure(figsize=(12, 6))
plt.plot(data['Price Dates'], data['Methi'], label='Methi Price')
plt.xlabel('Date')
plt.ylabel('Price')
plt.title('Price of Methi Over Time')
plt.grid(True)
plt.show()

plt.figure(figsize=(35, 5))
plt.subplot(1,3,2)
plt.plot(data['Price Dates'], y, label='Methi Price')
plt.plot(data['Price Dates'], y_pred_linear, color='red', label='Linear Trend')
plt.xlabel('Date')
plt.ylabel('Price')
plt.title('Linear Trend Estimation for Methi Price')
plt.legend()
plt.grid(True)


plt.figure(figsize=(35, 5))
plt.subplot(1,3,3)
plt.plot(data['Price Dates'], y, label='Methi Price')
plt.plot(data['Price Dates'], y_pred_poly, color='green',linestyle='--', label='Polynomial Trend (Degree 2)')
plt.xlabel('Date')
plt.ylabel('Price')
plt.title('Polynomial Trend Estimation for Methi Price')
plt.legend()
plt.grid(True)
plt.show()
```
### OUTPUT

![image](https://github.com/user-attachments/assets/54127092-e7e6-4dd7-b516-0de55d68f186)


A - LINEAR TREND ESTIMATION

![image](https://github.com/user-attachments/assets/069a9110-cdb6-4f5f-9016-2f84da68dbcb)


B- POLYNOMIAL TREND ESTIMATION

![image](https://github.com/user-attachments/assets/4866a9de-a5a3-47d2-8378-02898ccbbcd8)


### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
