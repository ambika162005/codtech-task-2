NAME:mocharla ambika INTENSHIP ID:CITS3162 NO:OF:WEEKS:8 weeks PROJECT NAME: Data science PROJECT SCOPE:predictive maintenance for machinery


Step 1: Import Libraries
Python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression

Step 2: Create Machinery Dataset
Python
data = {
    'Machine_ID':[101,102,103,104,105,106,107,108],
    'Operating_Hours':[100,200,300,400,500,600,700,800],
    'Temperature':[50,55,58,60,65,68,72,75],
    'Vibration':[0.20,0.25,0.28,0.32,0.38,0.42,0.48,0.55],
    'Maintenance_Cost':[500,700,900,1200,1500,1800,2200,2600]
}

Step 3: Data Cleaning
Python
print("Missing Values")

print(df.isnull().sum())

df.drop_duplicates(inplace=True)

print("Data Cleaning Completed")

Step 4: Analysis
Python
print(df.describe())

Additional Analysis Commands
Python
print("Average Temperature =", df['Temperature'].mean())

print("Maximum Temperature =", df['Temperature'].max())

print("Average Vibration =", df['Vibration'].mean())

print("Total Maintenance Cost =", df['Maintenance_Cost'].sum())

Step 5: Visualization 1 – Temperature Trend
Python
plt.figure(figsize=(8,5))

plt.plot(
    df['Machine_ID'],
    df['Temperature'],
    marker='o'
)

plt.title("Machine Temperature Analysis")
plt.xlabel("Machine ID")
plt.ylabel("Temperature")

plt.grid(True)

plt.show()

Step 6: Visualization 2 – Maintenance Cost
Python
plt.figure(figsize=(8,5))

plt.bar(
    df['Machine_ID'],
    df['Maintenance_Cost']
)

plt.title("Maintenance Cost Analysis")
plt.xlabel("Machine ID")
plt.ylabel("Cost")

plt.show()

Step 7: Visualization 3 – Vibration Distribution
Python
plt.figure(figsize=(6,6))

plt.pie(
    df['Vibration'],
    labels=df['Machine_ID'],
    autopct='%1.1f%%'
)

plt.title("Vibration Distribution")

plt.show()

Step 8: Prediction Model
Predict future maintenance cost based on operating hours.
Python
X = df[['Operating_Hours']]

y = df['Maintenance_Cost']

model = LinearRegression()

model.fit(X,y)

prediction = model.predict([[900]])

print("Predicted Maintenance Cost =", prediction[0])

Step 9: Prediction Graph
Python
plt.figure(figsize=(8,5))

plt.scatter(
    df['Operating_Hours'],
    df['Maintenance_Cost']
)

plt.plot(
    df['Operating_Hours'],
    model.predict(df[['Operating_Hours']])
)

plt.title("Operating Hours vs Maintenance Cost")

plt.xlabel("Operating Hours")

plt.ylabel("Maintenance Cost")

plt.show()

Step 10: Dashboard Creation
fig, axs = plt.subplots(2,2, figsize=(12,8))

axs[0,0].plot(
    df['Machine_ID'],
    df['Temperature']
)
axs[0,0].set_title('Temperature')

axs[0,1].bar(
    df['Machine_ID'],
    df['Maintenance_Cost']
)
axs[0,1].set_title('Maintenance Cost')

axs[1,0].plot(
    df['Machine_ID'],
    df['Vibration']
)
axs[1,0].set_title('Vibration')

axs[1,1].scatter(
    df['Operating_Hours'],
    df['Maintenance_Cost']
)
axs[1,1].set_title('Prediction Analysis')

plt.tight_layout()

plt.show()
Python
