
---

### 📘 Week 8 – Classification Models

**File:** `_posts/2025-07-08-classification-models.md`

```markdown
---
layout: post
title: "Building Classification Models in Python"
date: 2025-07-08
categories: [Python, Machine Learning]
---

In Week 8, I explored **classification algorithms** to predict categories (e.g., spam/not spam, churn/no churn).

---

## 🧠 Models Implemented

- Logistic Regression
- Decision Trees
- Random Forest
- Support Vector Machines

---

## 💻 Sample Code

```python
from sklearn.ensemble import RandomForestClassifier
clf = RandomForestClassifier()
clf.fit(X_train, y_train)
print("Accuracy:", clf.score(X_test, y_test))

