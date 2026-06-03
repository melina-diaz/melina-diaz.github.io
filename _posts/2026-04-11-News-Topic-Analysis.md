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
This project analyzes **108,000 news headlines** all from the 1st half of August 2020, and maps them into 1 vocabulary space, revealing how categories like **Science, Business, Entertainment, Health, Sports, World Events, and National Events** establish their own distinct linguistic territory.
<br>
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

## Interactive Visualizations
Each blue point is a word that occurred 5+ times in the news title dataset. Its position shows how it relates to every category, which are the non-blue points. Its size reflects overall frequency. 
<br>

For example, you can think of the light red point at the top of the graph as the essense of the Sports news category. The words closeby like "arsenal" and "transfer" show that although they might be used in other news categories, they are used significantly more frequently in the Sports category. Words that are equidistant to 2 or more category points show that they are used about the same frequency between the categories. For example, "game" is equally between Sports and Technology. 
<br>
<br>
Feel free to *hover* over points to see the represented word and frequency, use the icons on the top right of the graphs and *drag* to pan, rotate, or zoom, or *click* on the legend key to filter by color.
{% include news_plotly_2D_scatter.html %} 
{% include news_plotly_3D_scatter.html %} 

<br>
<br>

## Observations
- There are not only relationships between the words and the categories, but also relationships between categories and other categories. Health and World are the closest pair, while Entertainment and Sports are the farthest apart. (This is easier to notice in the 3D graph rather than the 2D.) In fact, Science, Health, World, and Nation are all clustered together, suggesting there are a lot of overlapping words between these categories. In the context of August 2020, that makes sense and is supported by the most frequent words within the cluster being "coronavirus" (5566 times), "vaccine" (1533), and "covid" (1397).
- The highest frequencies among the words most unique to a category greatly vary.
    - Among the Sports-unique words, "league" (1214) and "transfer" (1068) have the highest frequencies. 
    - Among the Entertainment-unique words, ...
    - Among the Technology-unique words, "apple" (1206), "google" (1100), "galaxy" (950) have the highest frequencies. There are many other brand names too.
    - Among the Business-unique words, "market" (3435) has the highest frequency.
    - Among the Science-unique words, "nasa" (461) and "mars" (353) have the highest frequencies.
    - Among the Health-unique words, ...
    - Among the World-unique words, ...
    - Among the Nation-unique words, "police" (792) has the highest frequency.
- There are a lot of proper nouns amongst the high frequency words that are most
<br>
<br>

### What to Explore Further
- How does the vocabulary space change over time? If there were datasets that represent different months or years of news articles, we can see which words maintain to be used frequently and if there's a shift in how they are associated to the categories.
- Instead of using words, use phrases of X-length of consecutive words. Finding the sweet spot for X might be a bit tricky, but it would provide a bit more context with how the words are being used and when using a threshold, filter out less common occurences.
- Flag words by their part of speech (verb, noun, adjective, etc.) This can be difficult with words that have ambiguous parts of speech, and might not be relevant since cleaning text can remove part of speech by simplifying into root words.
- Color code each word in graph to the closest category (classification).

#### Sources: 
Dataset: [Labelled News Articles](https://www.kaggle.com/datasets/kotartemiy/topic-labeled-news-dataset)
