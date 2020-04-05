# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) 

# Capstone Project: Recommender System


## Executive Summary

Problem Statement:
A Recommender System refers to a system that is capable of predicting the future preference of a set of items for a user, and recommend somthing s/he likes (content based) or something preferred by other users with similar tastes (collaborative). In the past where brick and mortar is the norm, recommendations are usually made through word of mouth. However, with the internet, availability of large amount of data and fast computing power, recommendations not only can be done quickly but also fairly accurate. Recommendations are very common nowadays. Businesses especially those relying heavily or solely on online sales, recommender systems is a must and will greatly boost business growth or even the very survival of the business.

There are many type of recommender systems but in this movie recommender system project, the following 2 models will be used;

[Collaborative Recommendation Engine]
The user's ratings is the backbone for the basis for further suggestions in this type of recommendation engine.
The collaborative recommendation is based on the history of user interactions with the platform and ratings users have given. For instance, if user A likes the same 5 movies as user B, user A will most likely also enjoy movies user B likes. In short, find users who are similar and recommend what they like (user-based).

[Content-based Recommender System (similar items)]
The content-based recommendation goes in a different direction from collaborative systems. Instead of focusing on the users' behavior, the content-based recommendation is built around items, ie. movies. In this case, if the user is looking for action movies, the system will likely suggest the same genre. For example, if a user enjoys certain characteristics of movies (e.g. certain actors, genre, etc.), the user probably also enjoy other movies with those characteristics. Note this can easily be done using machine learning methods! Each movie can be decomposed into features. Then, for each user we compute a model -- the target can be a binary classifier (e.g. "LIKE"/"DISLIKE") or regression (e.g. star rating). The initial model is based on a simple non-machine learning model and the results will be compared with a machine learning based model. The machine learning model will be expected to produce better results. Although there are many users and movie titles but in reality, not all users give their ratings which in a way is good. This means, we can recommend movies to users. Instead of storing all users and movies in matrix which can be very huge and take up a lot of memory, we can store the ratings in a sparse matrix which requires far less memory.


## Objective
Build a model recommending movies to the user according to user's ratings using content-based or collaborative model. We will start off with a simple non-machine learning model to set a baseline score. We will then use ML model to compare results. 


# Optional:
#### If time permits try to incorporate the followings;
(i) Store data in a database and if possible place the database in a bigdata environment.
(ii) Retrieve datasets from database using SQL and feed the data into the model.
(iii) Design a front end user interface using Flask for user to interact with the model eg, input ratings and request the recommender system for movie recommendations.

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
Datasets with different sizes eg, small, 1M, 20M, etc. are available at Grouplens. This project will be using the 1M datasets downloaded from Grouplens. Refer to links provided in the Data Source section below.


### Exploratory Data Analysis
Movies and ratings are stored separately in movies and ratings file. About a million users ratings of movies can be found in the ratings dataset while close to 4,000 movies information is in the movies dataset. Modeling technique such as Cosine Similarity will be used to make recommendation. 


### Data Cleaning
Datasets are cleaned, no missing values, no outliers and data integrity seems to be okay. Hence, data cleaning is not required except that some of the irrelevant features will be removed eg, timestamp.

---

### Data Visualization
- Find out movie titles and genres users generally like using wordcloud.
- Find out movie ratings distribution.

---

### Pre-processing
Remove irrelevant features from datasets eg, time stamp.

---

### Modeling
**Establish baseline score.**


---

### Interpretation of Results


---

### Business Recommendations:


---

### Data Source:
Due to GitHub fize size limitation (file size must not > 100mb), the 1 million ratings dataset will be used.

1M datasets from Grouplens: https://grouplens.org/datasets/movielens/1m/

Full details on all available datasets: https://grouplens.org/datasets/movielens/

Data dictionary: http://files.grouplens.org/datasets/movielens/ml-latest-README.html

---