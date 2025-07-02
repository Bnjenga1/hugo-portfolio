---
title: "A Beginner’s Guide to Data Cleaning Using Pandas"
date: 2025-07-01
description: "Learn how to clean messy datasets using pandas with real examples from a Nairobi real estate dataset."
tags: ["data cleaning", "pandas", "Python", "beginner", "Nairobi"]
categories: ["Data Science Blog"]
draft: false
---

Most real-world datasets are messy. Before you can run any analysis or build a model, you need to deal with missing values, strange outliers, inconsistent formatting, and incorrect data types. This post walks through the basics of data cleaning using `pandas`, one of the most popular Python libraries for data manipulation.

We'll use a dataset of Nairobi property listings as our example. It contains information like location, price, number of bedrooms, and date posted. Let’s get started.

## 1. Load the Data

We'll begin by loading the dataset and looking at the first few rows.

```python
import pandas as pd

df = pd.read_csv("nairobi_real_estate.csv")
df.head()
```

## 2. Basic Checks

Before cleaning, understand what you're dealing with.

```python
df.shape
df.columns
df.info()
df.describe()
```

This tells you how many rows and columns you have, what types each column is, and some summary statistics for numeric columns.

## 3. Handle Missing Values

Let’s check which columns have missing data.

```python
df.isnull().sum()
```

You can choose to drop rows, fill missing values, or leave them depending on the context. Here’s how to fill missing prices with the median value:

```python
df['price'].fillna(df['price'].median(), inplace=True)
```

## 4. Fix Data Types

Some columns might look like numbers or dates but are stored as strings. Fix them like this:

```python
df['date_posted'] = pd.to_datetime(df['date_posted'])
df['price'] = pd.to_numeric(df['price'], errors='coerce')
```

The `errors='coerce'` option turns non-numeric values into NaN, which you can handle afterward.

## 5. Remove Duplicates and Outliers

To avoid repeated records or extreme values that skew your analysis:

```python
df = df.drop_duplicates()

# Remove listings with unreasonable prices
df = df[(df['price'] > 10000) & (df['price'] < 1000000)]
```

You can also use quantiles to remove the top and bottom 1%:

```python
q_low = df['price'].quantile(0.01)
q_high = df['price'].quantile(0.99)
df = df[(df['price'] >= q_low) & (df['price'] <= q_high)]
```

## 6. Clean Text and Categorical Data

Text columns often have inconsistent formatting.

```python
df['neighborhood'] = df['neighborhood'].str.strip().str.lower()
```

If some categories are written differently, standardize them:

```python
df['bedrooms'] = df['bedrooms'].replace({'two': 2, 'three': 3})
```

## 7. Final Checks and Save Clean Data

After cleaning, check again to make sure everything looks good:

```python
df.info()
```

Then save the clean dataset:

```python
df.to_csv("nairobi_cleaned.csv", index=False)
```

## Conclusion

Data cleaning may not be the most glamorous part of data science, but it’s essential. Clean data leads to better analysis, more reliable models, and clearer insights.

Want to see how I used this dataset in a real project?  
👉 [Check out my Nairobi housing analysis project here](/projects/nairobi-real-estate)

If you found this helpful, stay tuned for more beginner-friendly guides. You can also follow me on [LinkedIn](https://www.linkedin.com/in/brian-mwaura1/) or explore more on my [Projects](/projects) page.
