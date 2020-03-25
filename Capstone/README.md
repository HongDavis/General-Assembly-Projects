# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) 

# Capstone Project: Recommender System


## Executive Summary

To build a model recommending certain genres of movies to the user using content-based or collaborative approach. Here is a short summary of the 2 approach.

[Collaborative Recommendation Engine]
The user's feedback is the backbone for the basis for further suggestions in this type of recommendation engine.
The collaborative recommendation is based on the history of user interactions with the platform.

Here's how it works:
First, the system aggregates the user output - various kinds of search history, ratings, comments, and recommendations of products or pieces of content in a big dataset.
Then, it compares the output of different users for specific products, finds common elements, and calculates matches between different pieces of content. Based on the information, the algorithm will make relevant suggestions to users. It is also a good way of understanding which products are preferred by the users and to what degree in comparison with the other products.


[Content-based Recommender System]
The content-based recommendation goes in the opposite direction from collaborative systems. Instead of focusing on the users' behavior, the content-based recommendation is built around the item inventory (products, contents) and attribution comparison. In this case, if the user is looking for action movies, the system will likely suggest laptops of similar size and tech specifications.

Keywords that describe items lay the foundation for the suggestions, and each product usually has more than one keyword to make the matching easier and more precise. These keywords, coupled with the user activity, form the scope of the movie recommendation.

---


### Contents:

- [Obtain Data](Obtain-Data)
- [Exploratory Data Analysis](EDA)
- [Data Cleaning](#Data-Cleaning)
- [Pre-processing](#Pre-processing)
- [Modeling](#Modeling)
- [Interpretation of Results](#Interpretation-of-Results)
- [Business Recommendations](#Business-Recommendations)
- [Data Source](#Data-Source)

---

### Obtain Data
Data sets can be downloaded from Kaggle. There are couple of datasets with different sizes eg, small, 100K and 20M. This project will be using the Full: 27,000,000 ratings and 1,100,000 tag applications applied to 58,000 movies by 280,000 users. Includes tag genome data with 14 million relevance scores across 1,100 tags. Last updated 9/2018.

Data dictionary: http://files.grouplens.org/datasets/movielens/ml-latest-README.html


### Exploratory Data Analysis
Perform initial EDA of the data to have a better understanding of the features and its correlations.


### Data Cleaning
Removed nul values

---

### Data Visualization


---

### Pre-processing
Perform the followings before performing NLP modeling.
- Remove HTML tags.
- Remove puntuations.
- Convert all words to lower case.
- Remove stop words.
- Tokenize and Lemmetize words.

---

### Modeling
**Establish baseline score.**


---

### Interpretation of Results


---

### Business Recommendations:


---

### Data Source:
Due to GitHub fize size limitation (file size must not > 100mb), the 1 million ratings dataset will be used. MovieLens 10M movie ratings. Stable benchmark dataset. 10 million ratings and 100,000 tag applications applied to 10,000 movies by 72,000 users. Released 1/2009. Zipped file size: 63MB

Datasets from Grouplens: https://grouplens.org/datasets/movielens/1m/

Full details about the datasets: https://grouplens.org/datasets/movielens/

Data dictionary: http://files.grouplens.org/datasets/movielens/ml-latest-README.html

---