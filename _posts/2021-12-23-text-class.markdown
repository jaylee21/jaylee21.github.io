---
layout: post
title:  Text Classification for Proper Categorization of Postings
date:   2021-12-23 15:01:35 +0300
image:  '/images/2021-12-23-text-class/2021-12-23-main.jpg'
tags:   [Python, scikit-learn, NLP]
---


## Introduction

In this project, our group **aimed to develop a classification model** that correctly classifies each posting in the video gaming category in Craigslist into a corresponding brand to enhance user experience and the company's key business performance. 

* **Tools / Libraries used:** Python / beautiful soup, pandas, nltk, scikit-learn, keras, etc.

* **Dataset:** Web Scrapped / titles and reviews of posts in Craiglist / 3011 rows * 8 columns

* **Analyses Performed:** Web Scrapping, Data Cleaning/Manipulation, Keyword Extraction, Text Representation(Tokenization, Lemmatization, Vectorization), Machine Learning(Naive Bayes, Logistic Regression, Random Forest, SVC, Neural Network), Deep Learning(Recurrent Neural Network), Validation(Confusion Matrix), and Business Insights

## Analysis

FIrst, we performed web-scrapping in the video gaming cateogry in Craigslist. We collected posting id, datetime, city, title, price, place, and description. Then we cleaned the data by removing dollar sign in price and parentheses in place, making the description column in one line, and lowering the title case. 

<div style='text-align:center'>
<h5>[Date cleaning]</h5>
</div>
<div style="text-align:center;">
<img src="../images/2021-12-23-text-class/picture1.png" alt="picture1.png" style="zoom:70%;" class="center" />
</div><br><br><br>

Then to create target variables more efficiently, we wrote codes that count the number of words that are relevant to each brand, to assign each post to a corresponding category. For example, the first row in the table has the higest score in Aracde (4), so we assign that post to Arcade category. 

<div style='text-align:center'>
<h5>[Creating target variables - Keyword extraction]</h5>
</div>
<div style="text-align:center;">
<img src="../images/2021-12-23-text-class/picture2.png" alt="picture2.png" style="zoom:70%;" class="center" />
</div><br><br><br>

Next, using predictor variables(title + description) and response variables(corresponding brands), we built 6 different models. We first vectorized the predictor variables from text to numerical values using TFIDF vectorization after tokenizing, lemmatizing and removing stop-words and punctuations. Then we splitted the dataset into train(70%) and test(70%) setsto train and evaluate our models. 

<div style='text-align:center'>
<h5>[Model building]</h5>
</div>
<div style="text-align:center;">
<img src="../images/2021-12-23-text-class/picture3.png" alt="picture3.png" style="zoom:70%;" class="center" />
</div><br><br><br>


From the result, SVC model showed the higest accuracy with the score of 88.45%. From the confusion matrix of the SVC model, we can evaluate how model predicted each brand correctly. 

<div style='text-align:center'>
<h5>[Model performance]</h5>
</div>
<div style="text-align:center;">
<img src="../images/2021-12-23-text-class/picture4.png" alt="picture4.png" style="zoom:70%;" class="center" />

<div style='text-align:center'>
<h5>[Confusion matrix]</h5>
</div>
<div style="text-align:center;">
<img src="../images/2021-12-23-text-class/picture5.png" alt="picture5.png" style="zoom:70%;" class="center" />
</div><br><br><br>


Our model generated huge information gain by 34%. The website's search rate is 68% and our model classification rate is 92% (excluding others). It shows that our best model would provide more correct results and minimize information loss on the searches that users performed on the website. Therfore, we would expect that our model would contribute to an increase engagement of users with the webiste, leading to growth in retention rate and potentially generating more revenue.

<div style='text-align:center'>
<h5>[Information gain comparison]</h5>
</div>
<div style="text-align:center;">
<img src="../images/2021-12-23-text-class/picture6.png" alt="picture6.png" style="zoom:70%;" class="center" />
</div><br><br><br>


## Details of Codes and Model Building Process

<div class="notebook-embedded">
<iframe scrolling="yes" src="https://nbviewer.org/gist/jaylee21/e3b230d13eb3c54663f6163558d96c14" width="100%" data-embed="true" height="500" frameborder="0" allowfullscreen></iframe>
</div>

