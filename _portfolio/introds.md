---
title: "Predicting the Outcome of Professional Basketball Game"
excerpt: "Web scraping box scores and building Machine Learning pipelines"
header:
  teaser: /images/introds/basketball.jpg
sidebar:
  - title: "Course"
    image: /images/myphoto.jpg
    image_alt: "image"
    text: "NYU DS-GA 1001: <br> Introduction to Data Science"
  - title: "Skill Sets"
    text: "Python 
          <br> Machine Learning 
          <br> &emsp;- Scikit-learn 
          <br> Web Scraping
          <br>&emsp;- Pyppeteer
          <br>&emsp;- Selenium
          <br>&emsp;- BeautifulSoup
          <br> Visualization
          <br>&emsp;- Matplotlib
          <br>&emsp;- Seaborn"
gallery:
  - url: /images/introds/heatmap.jpg
    image_path: /images/introds/heatmap.jpg
    alt: "placeholder image 1"
  - url: /images/introds/mutualinformation.jpg
    image_path: /images/introds/mutualinformation.jpg
    alt: "placeholder image 2"
  - url: /images/introds/timeseriescv.jpg
    image_path: /images/introds/timeseriescv.jpg
    alt: "placeholder image 3"
toc: true
toc_label: "Content"
---



<p></p>
<button type="button" class="btn btn-secondary btn-sm" onclick=" relocate_home()" style="width:120px;height:40px;border:2px blue none;background-color:lightgrey;">Paper Link</button>

<script>
function relocate_home()
{
     location.href = "https://garylkl.github.io/pdf_files/introds_final.pdf";
} 
</script>

## Introduction

The sports of basketball fascinates us for its unpredictability, but whenever we look retrospectively, the result almost always makes sense. We can explain a victory by many factors: better star players, better team chemistry, better coaching, better momentum, and the list goes on and on. With the belief that the result of a basketball game is not entirely random, we landed this project to predict the result of the game based on the previous records of the participating opponents.

{% include gallery caption="" %}

## Web Scraping

There was no comprehensive dataset that includes all the information we need for this project, so we made the best efforts to scrape data from the internet and then merged these datasets to create our dataset. The three data sources are basketball-reference, stats.nba.com and ESPN’s NBA website.

## Potential Selection Bias

NBA rules have changed significantly since the start of league, leading to a great change in playing styles in the NBA. Since the data we collected are from 2008 to 2019, our model may achieve much worse results when trying to predict the outcomes of games a long time ago, like in the 20th century.

## Feature Selection

Since feature selection is crucial in determining the result, we chose to design two methods to conduct feature selection: one is first to drop highly correlated features and then use the random forest to select the most 15 important features; the other is to use mutual information. By making feature selection in such two ways, we ended up in 16 sets of features for eight train-test splits. Now, we will call the first method using correlation and random forest as the feature selection strategy one and mutual information as the feature selection strategy two.

## Blocking Time Series Split

To avoid potential problems of data leakage, traditional Cross Validation does not apply here due to its ran- domness. Instead, we used Blocking Time Series Split[8] written by staff in Packt as a strategy to tune the hyperparameters. Different from k-fold Cross Validation, Blocking Time Series Split uses a smaller set of data as test data and a fixed size of data before testing data as training data.