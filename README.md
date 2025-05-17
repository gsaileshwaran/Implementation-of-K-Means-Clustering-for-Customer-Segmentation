# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Data Loading & Inspection: Load the customer dataset and inspect it for structure and missing values.
2. Feature Selection: Use 'Annual Income' and 'Spending Score' for clustering.
3. Elbow Method: Apply the elbow method to determine the optimal number of clusters using WCSS.
4. K-Means Clustering: Fit the K-Means model with 5 clusters and predict the cluster for each customer.
5. Visualization: Plot the clusters using a scatter plot to visualize customer segments.
## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Saileshwaran Ganesan
RegisterNumber:  212224230237
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
```
```
data = pd.read_csv('Mall_Customers.csv')
print(data.head())
```
```
print(data.info())
```
```
print(data.isnull().sum())
```
```
wcss = []
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init="k-means++")
    # using 'Annual Income' and 'Spending Score'
    kmeans.fit(data.iloc[:, 3:])
    wcss.append(kmeans.inertia_)
```
```
plt.plot(range(1, 11), wcss)
plt.xlabel("Number of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()
```
```
km = KMeans(n_clusters=5)
print( km.fit(data.iloc[:, 3:]))
```
```
y_pred = km.predict(data.iloc[:, 3:])
print(y_pred)
```
```
data["cluster"] = y_pred
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
```
```
plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c="red", label="cluster0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c="black", label="cluster1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c="blue", label="cluster2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c="green", label="cluster3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c="magenta", label="cluster4")
plt.legend()
plt.title("Customer Segments")
plt.show()
```




## Output:
LOAD AND DISPLAY DATASET

![image](https://github.com/user-attachments/assets/7c779cc6-d34e-417a-8a5d-01c8d50dce97)

DATA INFO

![image](https://github.com/user-attachments/assets/d7f45eff-9c8c-48ea-8c2c-f1d938c2b7e6)

COUNT OF NULL VALUES

![image](https://github.com/user-attachments/assets/b68f49ed-b4bc-4863-9e74-5b7d99145cac)

ELBOW GRAPH

![image](https://github.com/user-attachments/assets/c1bc9a9b-7394-44d7-8ac3-f20e143280e2)

FITITNG K MEAN

![image](https://github.com/user-attachments/assets/b3717bd6-6350-42a4-9402-47700bbfcdbe)

CLUSTER LABELS

![image](https://github.com/user-attachments/assets/964da2aa-329b-4be3-aa60-fc7ea18c7036)

VISUALISATION

![image](https://github.com/user-attachments/assets/b9b0cb26-a204-42f3-9b6c-eec95334bb41)




## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
