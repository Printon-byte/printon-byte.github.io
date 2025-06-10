---
layout: single
title: "Web Scraping Netflix Data with Python"
date: 2025-06-10
author: "Printon Mauda"
categories: [data-science, web-scraping]
tags: [python, beautifulsoup, netflix]
excerpt: "Learn how I scraped and processed Netflix data for insights using BeautifulSoup and requests."
---

## 🕸️ Introduction

As part of my data science learning journey, I tackled a web scraping assignment to collect Netflix data. The goal was to fetch structured information from a webpage and prepare it for analysis.

## 🔧 Tools Used

- Python
- BeautifulSoup
- Requests
- Pandas

## 🛠️ The Process

I targeted a publicly available Netflix dataset and used `requests` to fetch the HTML, and `BeautifulSoup` to parse it.

```python
soup = BeautifulSoup(html, 'html.parser')
titles = soup.find_all('h1', class_='title')
