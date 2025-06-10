---
title: "Scraping the Web: Collecting Netflix Data with Python"
date: 2025-06-10
layout: single
categories: [projects, data-science]
author_profile: true
read_time: true
---

Web scraping is a fundamental technique for gathering large amounts of data from websites — especially when no official API is available. In this project, I simulated a scenario of scraping a dataset of Netflix titles, similar to those found on [Kaggle](https://www.kaggle.com/), to understand the logic and tools behind automated data extraction.

## 🛠️ Tools Used

- **Python**
- **BeautifulSoup**
- **Requests**
- **Pandas**

## 🧩 Objective

To collect information about Netflix content (titles, genre, release year, etc.) using scraping techniques, then format it into a structured dataset.

## 🔎 Steps Followed

1. **Target URL and Headers**
```python
import requests
from bs4 import BeautifulSoup

url = "https://example.com/netflix-titles"
headers = {'User-Agent': 'Mozilla/5.0'}
response = requests.get(url, headers=headers)
Parse HTML Content

python
Copy
Edit
soup = BeautifulSoup(response.content, 'html.parser')
titles = soup.find_all('div', class_='title-card')
Extract & Clean Data

python
Copy
Edit
data = []
for item in titles:
    name = item.find('h3').text
    year = item.find('span', class_='year').text
    data.append({'title': name, 'year': year})
Convert to DataFrame

python
Copy
Edit
import pandas as pd
df = pd.DataFrame(data)
df.to_csv('netflix_scraped.csv', index=False)
✅ Outcome
Successfully simulated a scraping workflow

Built a working CSV file from semi-structured HTML

Understood the ethical considerations and usage limits of scraping

<!-- Optional Image --> <!-- ![Web scraping result](/assets/images/netflix-scrape-preview.png) -->
📚 Learnings
The importance of User-Agent headers to avoid being blocked

Use of loops, parsing, and regex to clean web data

Value of saving structured data (CSV) for downstream analysis

yaml
Copy
Edit

---

## 📄 2. Blog Post: Exploratory Data Analysis (EDA) on Titanic  
**Filename**: `_posts/2025-06-12-eda-titanic.md`

```markdown
---
title: "Uncovering the Story: Exploratory Data Analysis on Titanic"
date: 2025-06-12
layout: single
categories: [projects, data-science]
author_profile: true
read_time: true
---

Once data is cleaned and structured, it’s time to explore it. Exploratory Data Analysis (EDA) is about uncovering patterns, identifying anomalies, testing hypotheses, and visualizing trends. In this project, I performed EDA on the [Titanic dataset](https://www.kaggle.com/c/titanic).

## 🧰 Tools Used
- Python
- Pandas
- Seaborn
- Matplotlib

## 🎯 Objective

To understand the factors that influenced survival rates aboard the Titanic.

## 🧮 Key Steps and Insights

### 1. Survival Rates
```python
df['Survived'].value_counts(normalize=True)
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

🧠 Conclusion
EDA helped me make sense of the Titanic data and prepare it for modeling. It's an essential phase in any data science workflow.
