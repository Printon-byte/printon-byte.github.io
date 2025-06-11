
---

## 📝 Blog Post 3: Exploratory Data Analysis with Titanic Dataset

**Filename**: `_posts/2025-06-12-eda-titanic.md`

```markdown
---
layout: single
title: "Exploratory Data Analysis on Titanic Dataset"
date: 2025-06-12
author: "Printon Mauda"
categories: [data-science, eda]
tags: [titanic, seaborn, pandas]
excerpt: "I used seaborn and pandas to explore the Titanic dataset, visualizing patterns in survival across age, gender, and class."
---
![Exploratory Data Analysis](/assets/images/EDA.jpeg)

## 🚢 Introduction

The Titanic dataset is a classic in data science. I performed EDA to understand survival trends and how they relate to other variables.

## 🔍 Key Questions Explored

- Did gender affect survival chances?
- Was class a major factor?
- What age group survived the most?

## 📊 Visuals & Code

```python
sns.barplot(x='Sex', y='Survived', data=df)
plt.title("Survival Rate by Gender")

~38% survived, ~62% did not

2. Gender-based Analysis
python
Copy
Edit
sns.countplot(x='Survived', hue='Sex', data=df)
Females had higher survival rates than males

3. Class and Fare
python
Copy
Edit
sns.boxplot(x='Pclass', y='Fare', data=df)
First-class passengers paid more and survived more

4. Age Distribution
python
Copy
Edit
sns.histplot(df['Age'].dropna(), bins=30, kde=True)
5. Correlation Heatmap
python
Copy
Edit
sns.heatmap(df.corr(), annot=True)
📊 Visual Insights
Age, class, and gender had strong correlations with survival

Family members aboard (SibSp/Parch) showed weak-to-moderate relationships

<!-- Optional Image --> <!-- ![EDA heatmap](/assets/images/titanic-eda-heatmap.png) -->
🧠 Conclusion
EDA helped me make sense of the Titanic data and prepare it for modeling. It's an essential phase in any data science workflow.
