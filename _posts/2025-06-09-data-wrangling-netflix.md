
---
![Netflix Data Wrangling](/assets/images/Data%20wrangling.jpeg)
Data wrangling — also known as data cleaning — is one of the most crucial steps in any data science project. It's where raw, inconsistent, and messy data gets transformed into a format that's clean, organized, and ready for analysis. In this project, I worked on wrangling the [Netflix Movies and TV Shows dataset from Kaggle](https://www.kaggle.com/datasets/shivamb/netflix-shows).

## 🧹 The Dataset

The dataset contains information about Netflix titles, including attributes like:
- Title
- Director
- Cast
- Country
- Date added
- Release year
- Rating
- Duration
- Type
- Category

But like many real-world datasets, it wasn’t clean.

## 🛠️ Tools Used
- **Python**
- **Pandas**
- **Jupyter Notebook**

## 🔍 Problems I Encountered

During initial inspection (`df.info()` and `df.isnull().sum()`), I noticed:
- **Missing values** in `director`, `cast`, `country`, `date_added`
- Inconsistent date formats
- Duplicates
- Mixed values in the `duration` column (e.g., “1 Season” vs “90 min”)
- Typos and inconsistent capitalization in categorical data

## 🧽 Cleaning Process

1. **Removed Duplicates**

```python
df.drop_duplicates(inplace=True)
Absolutely, Printon! Here's a well-structured blog post on **Data Wrangling**, based on the Netflix dataset assignment you worked on. This version is markdown-ready for your `_posts/` folder and includes placeholder spots for images if you want to add snapshots later.

---

### 📄 File Name (save in `_posts/`):

`2025-06-11-data-wrangling-netflix.md`

---

### ✅ Full Blog Markdown Code:

````markdown
---
title: "Cleaning the Mess: Data Wrangling with the Netflix Dataset"
date: 2025-06-11
layout: single
categories: [projects, data-science]
author_profile: true
read_time: true
---

Data wrangling — also known as data cleaning — is one of the most crucial steps in any data science project. It's where raw, inconsistent, and messy data gets transformed into a format that's clean, organized, and ready for analysis. In this project, I worked on wrangling the [Netflix Movies and TV Shows dataset from Kaggle](https://www.kaggle.com/datasets/shivamb/netflix-shows).

## 🧹 The Dataset

The dataset contains information about Netflix titles, including attributes like:
- Title
- Director
- Cast
- Country
- Date added
- Release year
- Rating
- Duration
- Type
- Category

But like many real-world datasets, it wasn’t clean.

## 🛠️ Tools Used
- **Python**
- **Pandas**
- **Jupyter Notebook**

## 🔍 Problems I Encountered

During initial inspection (`df.info()` and `df.isnull().sum()`), I noticed:
- **Missing values** in `director`, `cast`, `country`, `date_added`
- Inconsistent date formats
- Duplicates
- Mixed values in the `duration` column (e.g., “1 Season” vs “90 min”)
- Typos and inconsistent capitalization in categorical data

## 🧽 Cleaning Process

1. **Removed Duplicates**

```python
df.drop_duplicates(inplace=True)
````

2. **Handled Missing Values**

For critical fields like `title` or `type`, I dropped rows. For others like `director`, I used `"Unknown"`:

```python
df['director'].fillna('Unknown', inplace=True)
```

3. **Date Standardization**

The `date_added` column had mixed formats. I converted it to datetime:

```python
df['date_added'] = pd.to_datetime(df['date_added'], errors='coerce')
```

4. **Standardized Text Data**

```python
df['rating'] = df['rating'].str.upper().str.strip()
df['country'] = df['country'].str.title().str.strip()
```

5. **Separated Duration**

I split the `duration` column into numeric and unit components:

```python
df[['duration_int', 'duration_type']] = df['duration'].str.extract('(\d+)\s+(\w+)')
df['duration_int'] = df['duration_int'].astype(float)
```

## 🧾 Before and After Cleaning

Before cleaning:

```plaintext
title       director    duration    rating     country
--------    ---------   --------    -------    --------
Movie A     NaN         1 Season    TV-14      United States
Movie A     NaN         1 Season    TV-14      United States
```

After cleaning:

```plaintext
title       director    duration_int    duration_type    rating     country
--------    ---------   -------------   --------------   -------    --------
Movie A     Unknown     1.0             Season           TV-14      United States
```

## ✅ Final Result

* Clean, deduplicated, and standardized dataset
* Separated duration and normalized text fields
* Handled all NaNs and removed irrelevant rows

## 🧠 Key Takeaways

* Always inspect your data before jumping to analysis.
* Missing data doesn’t always need to be dropped — sometimes it can be labeled, filled, or transformed.
* Clean data is **the backbone** of accurate insights.

## 📊 What's Next?

Now that the data is clean, I’m planning to:

* Visualize content trends by year and country
* Compare movie vs. TV show growth over time
* Build a recommendation system using genres and user ratings

Stay tuned for the next post.
