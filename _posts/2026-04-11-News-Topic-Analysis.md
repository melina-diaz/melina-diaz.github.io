---
layout: post
title: What makes news? Uncovering word patterns across categories using NLP
date: 2026-04-11
---
## Why does news language matter?
Every news category has its own vocabulary fingerprint. But which words do publishers actually lean on to capture attention and do those words differ across categories?
<br>
<br>
This project quantifies those patterns by mapping 100,000 news headlines into a shared language space, revealing how Science, Business, Entertainment, Health, Sports, World Politics, and National Politics establish their own distinct corner.
<br>
<br>
*This post contains a summary and interactive visualizations of the project. For the code and more in-depth explanations, please see [my Github](https://github.com/melina-diaz/NewsArticles). Thank you!*
<br>
<br>
## From raw headlines to visualization
#### 1. Text cleaning & preprocessing
Removed stopwords, URLs, punctuation, uppercase, and numeric characters from raw text using NLTK and regex.

#### 2. Word frequency extraction per category
Combined all headlines per topic and counted word frequencies. Words appearing fewer than 5 times were filtered to reduce noise.

#### 3. Normalization & reference points
Normalize word frequency for each category to balance a dataset that's biased to certain categories. Include each category word ("Science", "Business", etc) as reference points.

#### 4. Dimensionality reduction & visualization
Compressed 10,000 word frequencies using PCA to 3 components, then plotted each word in a Plotly scatterplot.

<br>

### Interactive Visualization
{% include news_plotly_2D_scatter.html %} 
{% include news_plotly_3D_scatter.html %} 

Each word is a point, its position shows how it relates to every category reference point, which are different colors. Size reflects word frequency.
<br>

*Hover* over the points to see the word represented and the frequency across the entire dataset.
<br>

*Click* on legend to filter points.
<br>

*Zoom in* to see more detail.
<br>
<br>

#### Sources: 
Dataset: [Labelled News Articles](https://www.kaggle.com/datasets/kotartemiy/topic-labeled-news-dataset)
