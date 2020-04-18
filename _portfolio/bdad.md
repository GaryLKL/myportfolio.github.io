---
title: "A Crowdfunding Campaign You Can’t Refuse"
excerpt: " "
header:
  teaser: /images/bdad/wordcloud.jpg
sidebar:
  - title: "Course"
    image: /images/myphoto.jpg
    image_alt: "image"
    text: "CSCI-GA.3033: <br> Big Data Application Development"
  - title: "Skill Sets"
    text: "Scala Programming <br> Tableau Visualization <br> ML Pipelines (MLlib) <br> Data Cleaning"
gallery:
  - url: /images/bdad/workflow.jpg
    image_path: /images/bdad/workflow.jpg
    alt: "placeholder image 1"
  - url: /images/bdad/tableau.png
    image_path: /images/bdad/tableau.png
    alt: "placeholder image 2"
  - url: /images/bdad/workflow2.png
    image_path: /images/bdad/workflow2.png
    alt: "placeholder image 3"
toc: true
toc_label: "Content"
---


## Introduction

<button type="button" class="btn btn-secondary btn-sm" onclick=" relocate_home()">Paper Link</button>

<script>
function relocate_home()
{
     location.href = "https://garylkl.github.io/pdf_files/bdad_fina.pdf";
} 
</script>


In this work, we aim to increase the chance of success for the Kickstarter project owners. We collect three datasets: product profiles of Kickstarter, tweets on Twitter and product information from Amazon. Analytic and machine learning models are built upon these datasets to provide insights for project owners. Finally, we build a keyword recommendation system to automatically find these keywords for the owners.

To provide better insights, the history data of Kickstarter itself may not be enough. First, its corpus is smaller comparing to other text datasets. Second, other sources may also serve as strong indicators of success, such as reactions on social media. That’s why we choose to include the Amazon and Twitter datasets. We examine the synergies between these dataset carefully with Tableau visualization and conduct thorough experiments to substantiate our claims.

{% include gallery caption="" %}

