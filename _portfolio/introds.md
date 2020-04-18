---
title: "Predicting the Outcome of Professional Basketball Game"
excerpt: " "
header:
  teaser: /images/introds/basketball.jpg
sidebar:
  - title: "Course"
    image: /images/myphoto.jpg
    image_alt: "image"
    text: "DS-GA 1001: <br> Introduction to Data Science"
  - title: "Skill Sets"
    text: "Python <br>  <br> Web Scraping (Pyppeteer, Selenium, BeautifulSoup) <br> Matplotlib, Seaborn"
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


## Introduction

<button type="button" class="btn btn-secondary btn-sm" onclick=" relocate_home()">Paper Link</button>

<script>
function relocate_home()
{
     location.href = "https://garylkl.github.io/pdf_files/introds_final.pdf";
} 
</script>


The sports of basketball fascinates us for its unpredictability, but whenever we look retrospectively, the result almost always makes sense. We can explain a victory by many factors: better star players, better team chemistry, better coaching, better momentum, and the list goes on and on. With the belief that the result of a basketball game is not entirely random, we landed this project to predict the result of the game based on the previous records of the participating opponents.

{% include gallery caption="" %}

## Web Scraping

There was no comprehensive dataset that includes all the information we need for this project, so we made the best efforts to scrape data from the internet and then merged these datasets to create our dataset. The three data sources are basketball-reference, stats.nba.com and ESPN’s NBA website.

## Potential Selection Bias

NBA rules have changed significantly since the start of league, leading to a great change in playing styles in the NBA. Since the data we collected are from 2008 to 2019, our model may achieve much worse results when trying to predict the outcomes of games a long time ago, like in the 20th century.

## Blocking Time Series Split

To avoid potential problems of data leakage, traditional Cross Validation does not apply here due to its ran- domness. Instead, we used Blocking Time Series Split[8] written by staff in Packt as a strategy to tune the hyperparameters. Different from k-fold Cross Validation, Blocking Time Series Split uses a smaller set of data as test data and a fixed size of data before testing data as training data.