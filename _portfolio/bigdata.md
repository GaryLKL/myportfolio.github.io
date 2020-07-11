---
title: "Book Recommendation System for Goodreads.com"
excerpt: " "
excerpt: "Analyzing 4GB user-item interaction data in PySpark and developed a collaborative filtering recommendation system"
header:
  teaser: /images/bigdata/bookstore.jpg
sidebar:
  - title: "Course"
    image: /images/myphoto.jpg
    image_alt: "image"
    text: "NYU DS-GA 1004: <br> Big Data"
  - title: "Skill Sets"
    text: "Spark
    		<br>&emsp;- PySpark
    		<br>&emsp;- Spark ML
    		<br> Recommendation Systems
    		<br> Dimension Reduction
    		<br> Fast Search Algorithm"
toc: true
toc_label: "Content"
---
<p></p>
<button type="button" class="btn btn-secondary btn-sm" onclick=" relocate_home_article()" style="width:120px;height:40px;border:2px blue none;background-color:lightgrey;">Article Link</button>
<button type="button" class="btn btn-secondary btn-sm" onclick=" relocate_home_code()" style="width:120px;height:40px;border:2px blue none;background-color:lightgrey;">Code Link</button>

<script>
function relocate_home_article()
{
     location.href = "https://garylkl.github.io/pdf_files/bigdata_final.pdf";
} 
</script>

<script>
function relocate_home_code()
{
     location.href = "https://github.com/GaryLKL/Goodreads-Recommendation-Systems";
} 
</script>

## Introduction

In this project, we utilized collaborative filtering to build a recommender system on the Goodreads dataset. In particular, we used Alternating Least Square (ALS) and Spark to train our models, and attained RMSE of 1.6908, PrecisionAt of 0.770 on the test set. Furthermore, we implemented fast searching that increased the speed of the query of 10 users from 86 seconds to 0.33 seconds. We also explored the visualization of the learned space in this paper.

## Architecture

The description of the implementation is divided into two parts: (1) Data Preprocessing; (2) Modeling with Latent Factor Model. All work is done as Spark jobs on on Dumbo, the Hadoop cluster at New York University as the original dataset is large (4.1GB).  Besides, we do fast-queries and build Latent Factor Model in PySpark, which is the Python API for Spark. The whole data science process is generally separated into three stages from data pre-processing to model evaluation. The code for this project is available [here](https://github.com/GaryLKL/Goodreads-Recommendation-Systems).

## Fast Search

Query time is crucial in building a recommender system. Therefore, we compared query time of three methods to associate 500 books with each user. 

- **Naive Approach:** Bring user latent factors and item latent factors into memory of driver machine and use heapq(priority queue) to find the top 500 books for each user.
- **Spark Approach:** Since computing dot product between user latent factor and item latent factor is parallelizable, the second method take advantages of spark to do the computation.
- **Annoy Approach:** For each user, the best books to recommend are the books that are the nearest neighbors of this user. Therefore, we can build a spatial data structure in the space of all book latent factors after which we can easily find the most nearest neighbors of user at query time. The [Annoy library](https://github.com/spotify/annoy) did a good job at implementing it and it reduced the query time a lot.

## Dimension Reduction and Visualization

To visualize and better understand what kind of information item vectors encode, we used T-SNE to project the item factors into 2 dimensions. There can be many kinds information that is encoded, we mainly want to see if we can find some structure of ratings and genre in the item factors.