# Lab 8: 

<!-- NOTE: 
You can preview this README.md document by clicking the 'Preview' button in the RStudio toolbar. 
-->

## Preparation

- Read/ annotate: [Recipe \#8](https://lin380.github.io/tadr/articles/recipe_8.html). You can refer back to this document to help you at any point during this lab activity.
- Note: do your best to employ what you've learned and use other existing resources (R documentation, web searches, etc.).

## Objectives

- Gain experience working with coding strategies for transforming datasets using tidyverse functions and regular expressions.
- Practice reading/ writing data from/ to disk
- Implement organizational strategies for organizing and documenting a dataset in reproducible fashion.

## Instructions

In this lab we will be working with a new dataset the [Consumer Reviews of Amazon Products](https://www.kaggle.com/datafiniti/consumer-reviews-of-amazon-products) dataset downloaded from Kaggle. The aim will be to transform the curated version of this dataset such that the product reviews are tokenized by words and that these words are associated with sentiment labels. Feel free to use your knowledge and expand your knowledge to explore these datasets and the resulting transformed dataset to gain insight into the process of transformation.

### Setup

1. Create a new R Markdown document. Title it "Lab 8" and provide add your name as the author. 
2. Edit the front matter to have rendered R Markdown documents as you see fit (table of contents, numbered sections, etc.)
  - We will be using `knitr::kable()` to print out tables to allow for pretty tables in PDFs and with options for captions.
3. Delete all the material below the front matter.
4. Add a code chunk directly below the header named 'setup' and add the code to load the following packages and any others you end up using in this lab report. Add `message=FALSE` to this code chunk to suppress messages. 
  - tidyverse
  - tidytext
  - knitr
  - also include `source()` to source the `functions/functions.R` file

*NOTE* Please pay attention to the formatting of your R Markdown output --particular in terms of the code chunk options (`echo = FALSE`, `message = FALSE`, etc.). Also use `knitr::kable()` for all of your table outputs. Include the following two arguments. 

```r
dataset %>% # dataset
kable(booktabs = TRUE, # bold headers
      caption = "<Your informative caption here>") # caption
```

### Tasks

1. Create two level-1 header sections named: "Overview" and "Tasks". 
2. Under "Tasks" create four level-2 header sections named: "Orientation", "Transform", "Write the dataset", and "Documentation".
3. Follow the instructions that follow adding the relevant prose description and code chunks to the corresponding sections.
  - **Make sure to provide descriptions of your steps between code chunks and code comments within the code chunks!**

#### Orientation

- Read the Amazon Reviews curated dataset data dictionary
  - View the data dictionary 
- Read the Amazon Reviews curated dataset found in the `data/derived/` directory.
  - Preview the structure of the dataset and provide prose description of the dataset.
- Load the sentiments lexicon using the `get_sentiments()` function.
  - Preview the structure of the dataset and provide prose description of the dataset.
- Propose an idealized transformed dataset structure (use `tribble()` function) where the unit of observation is `word`.

#### Transform

- Tokenize the Amazon Reviews by words
  - Use the `unnest_tokens()` function with the relevant arguments
  - Preview the results and describe the results.

#### Join

- Join the reviews and sentiment lexicon by the common column `word` keeping all the observations (words) in the reviews.
 - Preview the results and describe the results.
 

**Optional**

- Explore the joined dataset: 
  - Can you filter the observations for only those words with sentiment labels?
  - Can you group the observations by `id` and then count the number of 'positive' vs. 'negative' words?
    - Do these labels appear to capture the `rating` score --that is if we used these sentiment labels would we arrive at the same rating score?

#### Write the dataset

- Write the transformed dataset to disk as a `.csv` file. Add this file to the `data/derived/` directory.

#### Document

- Use the `data_dic_starter()` function that was sourced from the `functions/functions.R` file to create the starter documentation file. Be sure to name your documentation file so that it is clear that this data dictionary file corresponds to the curated dataset you've just created.
  - Make sure to add `eval=FALSE` to the code chunk that creates the documentation starter file. This will ensure that when you knit this R Markdown document in the future, it will not overwrite the updates to this file that you will perform in the next steps!
- Download the starter documentation `.csv` file from RStudio Cloud to your computer and edit this `.csv` file in a spreadsheet software (such as MS Excel or Apple Numbers) adding the relevant documentation information.
- After updating this `.csv` file in spreadsheet software save it as a `.csv` and upload it to RStudio Cloud, overwriting the original starter documentation.
- Read the updated documentation `.csv` file and print the table structure to your R Markdown output. 

You can add a preview of the structure of the `data/derived/` directory using the following code inside a code chunk. 

```r
fs::dir_tree("data/derived/")
```

#### Overview

Now that you have conducted the steps to curate and document the Amazon Product Reviews dataset, provide a prose overview of what the goals of this script are and resulting data structure and files created.

### Assessment

Add a level-1 section which describes your learning in this lab.

Some questions to consider: 

  - What did you learn?
  - What was most/ least challenging?
  - What resources did you consult? 
  - What more would you like to know about?

## Submission

1. To prepare your lab report for submission on Canvas you will need to Knit your R Markdown document to PDF or Word. 
2. Download this file to your computer.
3. Go to the Canvas submission page for Lab #8 and submit your PDF/Word document as a 'File Upload'. Add any comments you would like to pass on to me about the lab in the 'Comments...' box in Canvas.
