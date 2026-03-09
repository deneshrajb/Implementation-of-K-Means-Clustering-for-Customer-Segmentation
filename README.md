# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Start the program.

2.Import required libraries like pandas, matplotlib, and sklearn.

3.Load the Mall_Customers.csv dataset.

4.Select Annual Income and Spending Score as features.

5.Initialize an empty list to store WCSS values.

6.Apply K-Means for cluster values from 1 to 10.

7.Store inertia (WCSS) for each cluster value.

8.Plot the Elbow graph to find the optimal number of clusters.

9.Train K-Means again using the chosen number of clusters (e.g., 5).

10.Predict clusters, assign them to customers, and visualize the clusters using scatter plot.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Denesh Raj Balaji Rao
RegisterNumber:  25005647
*/
```
```

import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++",n_init=10)
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters=5, n_init=10)
km.fit(data.iloc[:, 3:])
y_pred = km.predict(data.iloc[:,3:])
y_pred
data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster1")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster2")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster3")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster4")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="pink",label="cluster5")
plt.legend()
plt.title("Customer Segments")
```
## Output:
<img width="975" height="577" alt="image" src="https://github.com/user-attachments/assets/6a5327d3-c5f5-4092-9796-0a0468c1d46c" />
<img width="1062" height="611" alt="image" src="https://github.com/user-attachments/assets/1c8dc08b-f91c-4b3c-85c1-f136e0e5d6eb" />
<img width="788" height="226" alt="image" src="https://github.com/user-attachments/assets/b214d7db-441b-4b4c-91c1-74822122a29d" />
<img width="892" height="577" alt="image" src="https://github.com/user-attachments/assets/ad5e777c-1c4f-4ab0-a6eb-b0db00e65c2b" />

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
