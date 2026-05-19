---
layout: post
title: What makes news? Uncovering word patterns across categories using NLP
date: 2026-04-11
---
## Why does news language matter?
Each news category has its own vocabulary. Publishers chose words strategically to signal relevance, evoke emotion, or frame a narrative. But which words do publishers rely on most, and how do those words differ across categories?
<br>

 <!--more-->

<br>
This project analyzes **108,000 news headlines** and maps them into 1 vocabulary space, revealing how categories like **Science, Business, Entertainment, Health, Sports, World Events, and National Events** establish their own distinct linguistic territory.
<br>
*This post contains a summary and interactive visualizations of the project. For the code and more in-depth explanations, please see [my Github](https://github.com/melina-diaz/NewsArticles). Thank you!*
<br>
<br>

## From raw headlines to visualization

#### 1. Text cleaning & preprocessing
Cleaned text by removing stopwords, URLs, punctuation, uppercase, and numeric characters using NLTK and regex.

#### 2. Word frequency extraction per category
Combined all headlines per category and counted word frequencies. Words appearing fewer than 5 times were filtered to reduce noise.

#### 3. Normalization & reference points
Normalize word frequency for each category to balance a dataset that's biased to certain categories. Include each category word ("Science", "Business", etc) as reference points.

#### 4. Dimensionality reduction & visualization
Compressed 10,000 word frequencies using PCA to 3 components, then plotted each word in a Plotly scatterplot.

<br>

### Interactive Visualization
Each blue point is a word that occurred 5+ times in the news title dataset. Its position shows how it relates to every category, which are the non-blue points. For example, you can think of the light red point at the top of the graph as the essense of the Sports news category. The words closeby like "arsenal" and "transfer" show that although they might be used in other news categories, they are most related to the Sports category. Size reflects overall frequency.
<br>
Feel free to *hover* over points to see the represented word and frequency, use the icons on the top right of the graphs and *drag* to pan, rotate, or zoom, or *click* on the legend key to filter by color.
{% include news_plotly_2D_scatter.html %} 
{% include news_plotly_3D_scatter.html %} 

<br>
<br>

#### Sources: 
Dataset: [Labelled News Articles](https://www.kaggle.com/datasets/kotartemiy/topic-labeled-news-dataset)
