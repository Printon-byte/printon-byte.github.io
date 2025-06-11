---
title: "Scraping the Web: Collecting Netflix Data with Python"
date: 2025-06-10
layout: single
categories: [projects, data-science]
author_profile: true
read_time: true
---
![Web scraping with Python](/assets/images/Webscraping.jpeg)

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
