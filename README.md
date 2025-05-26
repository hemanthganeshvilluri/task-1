🎯 Objective
Learn how to clean and prepare the Iris dataset for machine learning. This includes exploring the data, handling missing values (if any), encoding (if needed), scaling, and detecting/removing outliers.

🛠️ Tools Used
Python 3

Pandas – Data manipulation

NumPy – Numerical operations

Matplotlib / Seaborn – Visualization

Scikit-learn – Loading dataset, preprocessing, ML

📂 Dataset Info
The Iris dataset contains 150 flower samples from 3 species:

setosa, versicolor, and virginica

Features:

sepal length

sepal width

petal length

petal width

species (target)

You can load it directly using scikit-learn or seaborn.

📋 Steps Followed
1. Import Libraries & Load Dataset
from sklearn.datasets import load_iris
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

iris = load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
df['species'] = iris.target
2. Explore the Data
print(df.head())
print(df.info())
print(df.describe())
3. Check for Missing Values
print(df.isnull().sum())
5. Standardize the Features
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
features = df.columns[:-1]  # All except 'species'
df[features] = scaler.fit_transform(df[features])
6. Visualize and Remove Outliers (Optional)
sns.boxplot(data=df[features])
plt.title("Boxplots of Features (Standardized)")
plt.xticks(rotation=45)
plt.show()
for col in features:
    Q1 = df[col].quantile(0.25)
    Q3 = df[col].quantile(0.75)
    IQR = Q3 - Q1
    lower = Q1 - 1.5 * IQR
    upper = Q3 + 1.5 * IQR
    df = df[(df[col] >= lower) & (df[col] <= upper)]
✅ Final Output
Cleaned, standardized version of the Iris dataset

Ready for use in machine learning tasks
