---
title: "Extractive-Abstractive of Text Summarization Stacking Model"
excerpt: " "
excerpt: "Designed a graph-based summarization pipeline to reduce word repetition by fine-tuning a pretrained Seq2Seq model"
header:
  teaser: /images/nlu/summary.jpg
sidebar:
  - title: "Course"
    image: /images/myphoto.jpg
    image_alt: "image"
    text: "NYU DS-GA 1012: <br> Natural Language Understanding"
  - title: "Skill Sets"
    text: "Spark
    		<br>&emsp;- Scala
    		<br>&emsp;- SparkSQL
    		<br>&emsp;- Spark's MLlib
    		<br> Tableau Visualization
    		<br> Machine Learning Pipelines
    		<br> Text Data Cleaning"
toc: true
toc_label: "Content"
---
<p></p>
<button type="button" class="btn btn-secondary btn-sm" onclick=" relocate_home()" style="width:120px;height:40px;border:2px blue none;background-color:lightgrey;">Article Link</button>

<script>
function relocate_home()
{
     location.href = "https://garylkl.github.io/pdf_files/nlu_final.pdf";
} 
</script>

## Abstract

Text summarization is a widely used technique in the information explosion world. However, one of the summarization approach, abstractive, encounter the readability issue from long text and the decreasing from repetition rate of the outcome are in the dilemma situation for improvement. In this work, we introduce a two-stage integrating concept, extractive stage, and abstractive stage, utilizing the output of extractive model as the input of the abstractive model, and implement different modern summarization techniques as multiple combinations. Finally, we measure the performance with the CNN/Daily Mail dataset by using the ROUGE score and repetition rate of the sentence.

