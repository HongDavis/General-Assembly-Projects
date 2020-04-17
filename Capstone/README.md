# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) 

# Capstone Project: Recommender System


## Executive Summary

Problem Statement:
A Recommender System refers to a system capable of predicting future preferences of a set of items for a user, and recommend something s/he likes (content based) or something preferred by other users with similar tastes (collaborative). In the past where brick and mortar is the norm, recommendations are usually made through word of mouth. However, with the internet, availability of large amount of data and fast computing power, recommendations not only can be done quickly but also fairly accurately. Recommendations are very common nowadays. Businesses especially those relying heavily or solely on online sales, recommender systems is a must and will greatly boost business growth or threathen the very survival of the business if it chosed not to implement one.

There are many type of recommender systems but in this movie recommender system project, the following 2 models will be used;

[Collaborative Recommendation Engine]
The user's ratings is the backbone for the basis for further suggestions in this type of recommendation engine.
The collaborative recommendation is based on the history of user interactions with the platform and ratings users have given. For instance, if user A likes the same 5 movies as user B, user A will most likely also enjoy movies user B likes. In short, find users who are similar and recommend what they like (user-based). It is very resource taxing for user-to-user recommandations and slightly better for item-to-item recommendation.

[Content-based Recommender System (similar items)]
The content-based recommendation goes in a different direction from collaborative systems. Instead of focusing on the users' behavior, the content-based recommendation is built around the user's past behavior and likings. For example, if a user enjoys certain characteristics of movies (e.g. certain actors, genre, etc.), the user probably also enjoy other movies with those characteristics. Note this can easily be done using machine learning methods! Each movie can be decomposed into features. Then, for each user we compute a model -- the target can be a binary classifier (e.g. "LIKE"/"DISLIKE") or regression (e.g. star rating). The initial model is based on a simple non-machine learning model and the results will be compared with a machine learning based model. The machine learning model will be expected to produce better results. Although there are many users and movie titles but in reality, not all users give their ratings which in a way is good. This means, we can recommend movies to users. Instead of storing all users and movies in matrix which can be very huge and take up a lot of memory, we can store the ratings in a sparse matrix which requires far less memory.


## Objective
Build and evaluate model's performance in recommending movies to user using content-based or collaborative model. We will start off with a simple non-machine learning model and see how it performs. We will then gradually build more advance models using ML and compare results to use the best model for our prediction.

---


### Contents:

- [Obtain Data](Obtain-Data)
- [Exploratory Data Analysis](EDA)
- [Data Cleaning](#Data-Cleaning)
- [Modeling](#Modeling)
- [Interpretation of Results](#Interpretation-of-Results)
- [Business Recommendations](#Business-Recommendations)
- [Data Source](#Data-Source)

---

### Obtain Data
Datasets with different sizes eg, small, 1M, 20M, etc. are available at Grouplens. This project uses the 1M datasets. Refer to links provided in the Data Source section at the end of this readme doc.

---

### Exploratory Data Analysis
Movies and ratings are stored separately in movies and ratings file. About a million users ratings of movies can be found in the ratings dataset while close to 4,000 movies information is in the movies dataset. Refer to the Data Visualization section below for more details. 

---

### Data Cleaning
Datasets are cleaned, no missing values, no outliers and data integrity seems to be okay. Hence, data cleaning is not required except that some of the irrelevant features will be removed eg, timestamp.

---

### Data Visualization
Although there is not much to visualize from the datasets but some insights can still be found using WordCloud to see what are the favorite titles and genres. For example Man, Love, Night and Day seems to be hot titles and Drama, Comedy and Action Adventure are the prefered genres. Another interesting fact was that users are very generous in rating movies ie, above average ratings 4 & 5 is way above 1 & 2.

---

### Modeling
We start off with a simple item-based collaborative filtering model using Cosine Similarity to compute pairwise distances between items to see a recommender in action. We then add Term Frequency and Inverse Document Frequency (TF/ IDF) to the model to see if there any difference. It turns out the model performance degraded after using TF/ IDF. As we were unable to quantify the performance of these 2 models, we need to use models that we can evaluate.

- Popularity Model
A common (and usually hard-to-beat) baseline approach is the Popularity model. This model is not actually personalized - it simply recommends to a user the most popular movies that the user has not previously consumed. As the popularity accounts for the "wisdom of the crowds", it usually provides good recommendations, generally interesting for most people.

- Content-Based Filtering Model
Content-based filtering approaches leverage description or attributes from items the user has interacted to recommend similar items. It depends only on the user previous choices, making this method robust to avoid the cold-start problem. For textual items, like articles, news and books, it is simple to use the raw text to build item profiles and user profiles.

- Collaborative Filtering Model
The Collaborative Filtering Recommender is entirely based on the past behavior and not on the context. More specifically, it is based on the similarity in preferences, tastes and choices of two users. It analyses how similar the tastes of one user is to another and makes recommendations on the basis of that. For instance, if user A likes movies 1, 2, 3 and user B likes movies 2,3,4, then they have similar interests and A should like movie 4 and B should like movie 1. This makes it one of the most commonly used algorithm as it is not dependent on any additional information. In general, collaborative filtering is the workhorse of recommender engines. The algorithm has a very interesting property of being able to do feature learning on its own, which means that it can start to learn for itself what features to use.

We will use matrix factorization to discover latent features underlying the interactions between two different kinds of entities and Singular value decomposition (SVD) uses matrix factorization to reduce the number of features while retaining the maximum amount of information. This is called dimensionality reduction. SVD decomposes a matrix $A$ into the best lower rank (i.e. smaller/simpler) approximation of the original matrix $A$, to make predictions.

- Hybrid Recommender Model
Hybrid recommender is a recommender that leverages both content and collaborative data for suggestions. In a system, first the content recommender takes place as no user data is present, then after using the system the user preferences with similar users are established. Theoretically, Hybrid model should be able to generate more accurate predictions since it combines the best of both models (Content and Collaborative).

---

### Interpretation of Results

| Model Name | recall@5 | recall@10 |
| --- | --- | --- |
| Popularity | 0.384924 | 0.547870 |
| Collaborative Filtering | 0.590706 | 0.739545 |
| Content-Based | 0.169519 | 0.277652 |
| Hybrid | 0.408239 | 0.460618 |

A big surprise as the Collaborative Filtering turned out to be better than the Hybrid model.

---

### Business Recommendations:
First and fore most before jumping into the band wagon and implement a recommender system blindly. In today days and age, it is no longer enough to just find out the pros and cons of the filtering approach*, a careful data scientist must also try to find out;

- What kinds of products are more likely to benefit from recommendations? Specifically, are mainstream products or niche projects more likely to benefit from recommendations?

- The other question is: What is it about a product that makes it more likely to elicit a response from a consumer when it’s recommended? For example, the ratings of the products or the price of the product or the type of the product — do they influence whether recommendations are effective for that product?

There was a marketing research done by Kownledge @ Wharton highlighting the importance of; 
https://knowledge.wharton.upenn.edu/article/recommended-for-you-how-well-does-personalized-marketing-work/
“Today, producers are used to thinking about, how does our product get discovered by consumers? They need to also ask, how does our product get discovered by algorithms?” 

The article also mentioned some surprised findings "Now, another result that surprised us was that recommendations and ratings are substitutes for each other. Again, prior to the study, we expected that people would respond to recommendations for things when they are highly rated, and we did find that. But what surprised us was that their response is even greater when the products have a lower rating. That suggests that there’s this effect of recommendations as substitutes for ratings, and we hadn’t predicted that beforehand."

Therefore, simply recommending users based on their browsing or purchasing history/ habits, how similar their behavior to other users, etc, will risk losing the users because of boredom (always recommend the same stuff) and also losing potential sales eg, niche products that weren't shown to the user before. For eg, Amazon has thousands of products and only a small fractions of the products were exposed/ recommended to the users. Imagine a recommender systems capable of recommending products users has never seen before which the users may like. 
<br><br>

## Recommendation: Assuming all of the above cons have been taken care of, risks mitigated and based on the metric, business should implement Collaborative Filtering as the recommender system. 


* Here are some of the pros and cons of some of the recommender systems;
- Item-Based Filtering: We only need to know the products users are viewing even though we don't know much about the user yet.
- User-Based Filtering: Similar concept as item-based but susceptible to cold-start problem as user data is not yet available.
- Content-Based Filtering: Works even when a product had no user reviews. Cons - requires descriptive data of all content to recommend which is time consuming.

---

### Data Source:
Due to GitHub fize size limitation (file size must not > 100mb), the 1 million ratings dataset will be used.

1M datasets from Grouplens: https://grouplens.org/datasets/movielens/1m/

Full details on all available datasets: https://grouplens.org/datasets/movielens/

Data dictionary: http://files.grouplens.org/datasets/movielens/ml-latest-README.html

---