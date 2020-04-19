---
title: "A Crowdfunding Campaign You Can’t Refuse"
excerpt: " "
header:
  teaser: /images/bdad/money.jpg
sidebar:
  - title: "Course"
    image: /images/myphoto.jpg
    image_alt: "image"
    text: "NYU CSCI-GA 3033: <br> Big Data Application Development"
  - title: "Skill Sets"
    text: "Spark
    		<br>&emsp;- Scala
    		<br>&emsp;- SparkSQL
    		<br>&emsp;- Spark's MLlib
    		<br> Tableau Visualization
    		<br> Machine Learning Pipelines
    		<br> Text Data Cleaning"
gallery:
  - url: /images/bdad/workflow.jpg
    image_path: /images/bdad/workflow.jpg
    alt: "placeholder image 1"
  - url: /images/bdad/tableau.jpg
    image_path: /images/bdad/tableau.jpg
    alt: "placeholder image 2"
  - url: /images/bdad/wordcloud.jpg
    image_path: /images/bdad/wordcloud.jpg
    alt: "placeholder image 3"
toc: true
toc_label: "Content"
---
<p></p>
<button type="button" class="btn btn-secondary btn-sm" onclick=" relocate_home()" style="width:120px;height:40px;border:2px blue none;background-color:lightgrey;">Paper Link</button>

<script>
function relocate_home()
{
     location.href = "https://garylkl.github.io/pdf_files/bdad_final.pdf";
} 
</script>

## Introduction




In this work, we aim to increase the chance of success for the Kickstarter project owners. We collect three datasets: product profiles of Kickstarter, tweets on Twitter and product information from Amazon. Analytic and machine learning models are built upon these datasets to provide insights for project owners. Finally, we build a keyword recommendation system to automatically find these keywords for the owners.

To provide better insights, the history data of Kickstarter itself may not be enough. First, its corpus is smaller comparing to other text datasets. Second, other sources may also serve as strong indicators of success, such as reactions on social media. That’s why we choose to include the Amazon and Twitter datasets. We examine the synergies between these dataset carefully with Tableau visualization and conduct thorough experiments to substantiate our claims.

{% include gallery caption="" %}

## Feature-based Prediction

In order to make prediction, we randomly split the whole dataset into a training set and a testing set. 10-fold cross validation has been executed on the training set to tune the parameters. MLlib provides several traditional machine learning API. Among all, we used logistic regression with a L2 regularizer as the baseline model. Besides, two tree- based model, decision tree and random forest, are built with a combination of hyperparameters. However, MLlib only has the option of linear support vector machine without the choice of a common kernel technique, radial basis function.

## NLP-based Prediction

We remove all special characters and white spaces, lower each character, remove stopwords and lemmatize. Afterwards, we choose pretrained [GloVe embedding](https://nlp.stanford.edu/projects/glove/) on Twitter to encode each product description as a 200d vector. Then, we feed a batch with 512 vectors into a multilayer perceptron (MLP). The final layer could be either a sigmoid or softmax layer. In the former case, the output is score within the range of [0,1]. We should scale it back to [1,5] as the original Amazon ratings. In the latter case, the output is the probability for each of the 5 rating classes.

## Keyword Recommendation

Given the description of a Kickstarter campaign as a query document, we would like to the retrieve the most similar documents from the Amazon dataset. The most straightforward idea is to compare its cosine similarity to each document one by one. However, this is compute-intensive. Therefore, we adopt locality sensitive hashing (LSH) to map each 200d GloVe embedding to a lower dimensional binary vector. The close documents in the original vector space will very likely be close in the new space. And we can reduce a great amount of search time.

Finally, we select the high-rated documents within top-k similar documents and compute the mean of their TF-IDF vector. If a word is more important, it will have a higher value in the resulting mean vector.