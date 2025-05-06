# python-week-7


import pandas as pd

# Load the dataset
data = pd.read_csv('iris.csv')  # Replace 'iris.csv' with the path to your CSV file

# Display the first few rows
print("First few rows of the dataset:")
print(data.head())

# Explore the structure of the dataset
print("\nDataset Info:")
print(data.info())

# Check for missing values
print("\nMissing values in each column:")
print(data.isnull().sum())

# Clean the dataset by filling missing values (example: fill with column mean)
data = data.fillna(data.mean())

# Verify that there are no missing values
print("\nMissing values after cleaning:")
print(data.isnull().sum())

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
data = pd.read_csv('iris.csv')  # Replace 'iris.csv' with the path to your CSV file

# Display the first few rows
print("First few rows of the dataset:")
print(data.head())

# Compute basic statistics for numerical columns
print("\nBasic Statistics:")
print(data.describe())

# Perform groupings on a categorical column and compute the mean of numerical columns
# Replace 'species' with the name of your categorical column
if 'species' in data.columns:
    print("\nMean of numerical columns grouped by species:")
    print(data.groupby('species').mean())

# Identify patterns or findings
print("\nInteresting Findings:")
if 'species' in data.columns:
    print("Different species have distinct average measurements for numerical columns.")
else:
    print("No categorical column named 'species' found for grouping.")

# Line chart (example: cumulative sum of sepal length over rows)
plt.figure(figsize=(8, 5))
plt.plot(data.index, data['sepal_length'].cumsum(), label='Cumulative Sepal Length')
plt.title('Cumulative Sepal Length Over Rows')
plt.xlabel('Index')
plt.ylabel('Cumulative Sepal Length')
plt.legend()
plt.show()

# Bar chart (average petal length per species)
if 'species' in data.columns:
    plt.figure(figsize=(8, 5))
    data.groupby('species')['petal_length'].mean().plot(kind='bar', color=['blue', 'green', 'orange'])
    plt.title('Average Petal Length per Species')
    plt.xlabel('Species')
    plt.ylabel('Average Petal Length')
    plt.show()

# Histogram (distribution of sepal length)
plt.figure(figsize=(8, 5))
plt.hist(data['sepal_length'], bins=10, color='purple', edgecolor='black')
plt.title('Distribution of Sepal Length')
plt.xlabel('Sepal Length')
plt.ylabel('Frequency')
plt.show()

# Scatter plot (sepal length vs. petal length)
plt.figure(figsize=(8, 5))
sns.scatterplot(x='sepal_length', y='petal_length', hue='species', data=data)
plt.title('Sepal Length vs. Petal Length')
plt.xlabel('Sepal Length')
plt.ylabel('Petal Length')
plt.legend(title='Species')
plt.show()


