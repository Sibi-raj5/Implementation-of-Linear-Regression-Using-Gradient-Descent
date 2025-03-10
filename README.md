# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import the required library and read the dataframe.

2.Write a function computeCost to generate the cost function.

3.Perform iterations og gradient steps with learning rate.

4.Plot the Cost function using Gradient Descent and generate the required graph.

## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: sbiraj e
RegisterNumber:
*/
import numpy as np
import pandas as pd
from sklearn.preprocessing import StandardScaler

def linear_regression(X1,y,learning_rate = 0.1, num_iters = 1000):
    X = np.c_[np.ones(len(X1)),X1]
    
    theta = np.zeros(X.shape[1]).reshape(-1,1)
    
    for _ in range(num_iters):
        
        #calculate predictions
        predictions = (X).dot(theta).reshape(-1,1)
        
        #calculate errors
        errors=(predictions - y ).reshape(-1,1)
        
        #update theta using gradiant descent
        theta -= learning_rate*(1/len(X1))*X.T.dot(errors)
    return theta
                                        
data=pd.read_csv("C:/classes/ML/50_Startups.csv")
data.head()

#assuming the lost column is your target variable 'y' 

X = (data.iloc[1:,:-2].values)
X1=X.astype(float)

scaler = StandardScaler()
y=(data.iloc[1:,-1].values).reshape(-1,1)
X1_Scaled = scaler.fit_transform(X1)
Y1_Scaled = scaler.fit_transform(y)
print(X)
print(X1_Scaled)

#learn modwl paramerers

theta=linear_regression(X1_Scaled,Y1_Scaled)

#predict target value for a new data
new_data=np.array([165349.2,136897.8,471784.1]).reshape(-1,1)
new_Scaled=scaler.fit_transform(new_data)
prediction=np.dot(np.append(1,new_Scaled),theta)
prediction=prediction.reshape(-1,1)
pre=scaler.inverse_transform(prediction)
print(prediction)
print(f"Predicted value: {pre}")

```

## Output:
data information

![image](https://github.com/Sibi-raj5/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/160597836/ea8e27cb-6f9f-4277-b224-1231304a698d)

value of X:

![image](https://github.com/Sibi-raj5/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/160597836/6bd59982-6adb-48d1-bc7f-d0ec2b3c4676)

value of X1_Scaled:

![image](https://github.com/Sibi-raj5/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/160597836/a217e6db-287b-497f-8be5-509497cc89ef)

predicted value:

![image](https://github.com/Sibi-raj5/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/160597836/b02d4d70-36f7-4ef5-83e5-ce7870084ffe)

## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
