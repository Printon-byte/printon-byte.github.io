
---
layout: post
title: "Exploring Regression Models in Python"
categories: [Python, Machine Learning]
---

In Week 7, I dove into **regression analysis** using Python to predict continuous variables based on feature inputs.

---

## 📘 Models Used

- Linear Regression
- Polynomial Regression
- Lasso and Ridge Regression

---

## 💻 Sample Code

```python
from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X_train, y_train)
print("R² Score:", model.score(X_test, y_test))
