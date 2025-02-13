# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) 

# Capstone Project: Recommender System


## Objective
Build and evaluate model's performance in recommending movies to user using content-based or collaborative model. We will start off with a simple non-machine learning model and see how it performs. We will then gradually build more advance models using ML and compare results to use the best model for our prediction.


## Executive Summary

Problem Statement:
A Recommender System (RS) refers to a system capable of predicting future preferences of a set of items for a user, and recommend something s/he likes (content based) or something preferred by other users with similar tastes (collaborative). In the past where brick and mortar is the norm, recommendations are usually made through word of mouth. However, with the internet, availability of large amount of data and fast computing power, recommendations not only can be done quickly but also fairly accurately. Recommendations are very common nowadays. Businesses especially those relying heavily or solely on online sales, RS is a must and will greatly boost business growth or threathen the very survival of the business if it chosed not to implement one.

There are many type of RSs but in this project, the following 2 models will be used;

[Collaborative Filtering]
The user's ratings is the backbone for the basis for further suggestions in this type of recommendation engine.
The collaborative recommendation is based on the history of user interactions with the platform and ratings users have given. For instance, if user A likes the same 5 movies as user B, user A will most likely also enjoy movies user B likes. In short, find users who are similar and recommend what they like (user-based). It is very resource taxing for user-to-user recommandations and slightly better for item-to-item recommendation.

[Content-based Filtering]
The content-based recommendation goes in a different direction from collaborative systems. Instead of focusing on the users' behavior, the content-based recommendation is built around the user's past behavior and likings. For example, if a user enjoys certain characteristics of movies (e.g. certain actors, genre, etc.), the user probably also enjoy other movies with those characteristics. Note this can easily be done using machine learning methods! Each movie can be decomposed into features. Then, for each user we compute a model -- the target can be a binary classifier (e.g. "LIKE"/"DISLIKE") or regression (e.g. star rating). The initial model is based on a simple non-machine learning model and the results will be compared with a machine learning based model. The machine learning model will be expected to produce better results. Although there are many users and movie titles but in reality, not all users give their ratings which in a way is good. This means, we can recommend movies to users. Instead of storing all users and movies in matrix which can be very huge and take up a lot of memory, we can store the ratings in a sparse matrix which requires far less memory.


---


### Contents

- [Obtain Data](#Obtain-Data)
- [Exploratory Data Analysis](#EDA)
- [Data Cleaning](#Data-Cleaning)
- [Modeling](#Modeling)
- [Evaluation](#Evaluation)
- [Risk/ Limitations/ Assumptions Affecting Findings](#Risks/-Limitations/-Assumptions-Affecting-Findings)
- [Business Recommendation](#Business-Recommendation)
- [Data Source](#Data-Source)
- [Capstone Project Blog](#Capstone-Project-Blog)

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

### Evaluation
Evaluation is important for machine learning projects, because it allows to compare objectively different algorithms and hyperparameter choices for models. We were able to evaluate the 4 models used in this project.

A more robust evaluation approach could be to split train and test sets by a reference date, where the train set is composed by all interactions before that date, and the test set are interactions after that date. For the sake of simplicity, we chose the random approach for this project.

In Recommender Systems, there are a set metrics commonly used for evaluation. We chose to work with Top-N accuracy metrics, which evaluates the accuracy of the top recommendations provided to a user, comparing to the items the user has actually interacted in test set. This evaluation method works as follows:

- For each item the user has interacted in test set.
- Sample 100 other items the user has never interacted.
- Note: Here we naively assume those non interacted items are not relevant to the user, which might not be true, as the user may simply not be aware of those not interacted items. But let's keep this assumption.
- Ask the recommender model to produce a ranked list of recommended items, from a set composed one interacted item and the 100 non-interacted ("non-relevant!) items.
- Compute the Top-N accuracy metrics for this user and interacted item from the recommendations ranked list.
- Aggregate the global Top-N accuracy metrics.

The Top-N accuracy metric choosen was Recall@N which evaluates whether the interacted item is among the top N items (hit) in the ranked list of 101 recommendations for a user. Other popular ranking metrics are NDCG@N and MAP@N, whose score calculation takes into account the position of the relevant item in the ranked list (max. value if relevant item is in the first position). Check out http://fastml.com/evaluating-recommender-systems/ for more details.

The below is a summary of the Top-N accuracy metric for the 4 models;
| Model Name | recall@5 | recall@10 |
| --- | --- | --- |
| Popularity | 0.384924 | 0.547870 |
| Collaborative Filtering | 0.590706 | 0.739545 |
| Content-Based | 0.169519 | 0.277652 |
| Hybrid | 0.408239 | 0.460618 |

Collaborative Filtering (CF) turned out to be better than the Hybrid model. This is obvious because hybrid is the combination of collaborative and content-based. The extremely low score of content-based dampened the performance of the hybrid model.

Generally, Matrix Factorization (MF) is quite efficient and accurate in predictions which explains why it is used by some of the common algorithms eg, ALS, SVD, etc and our CF model is using MF. In addition, the ratings datasets capture all ratings which is not the case in real live. Nonetheless, we can infer that movielens users are statisfied with the recommendations. 

---

## Risk/ Limitations/ Assumptions Affecting Findings
First and fore most before jumping into the band wagon to implement a RS blindly, we need to understand our products and what do want want to offer our users for eg, good shopping experience or just an In-Your-Face approach. There are plenty of RSs out there and different algorithm can be used each comes with pros and cons. Therefore, it is imperative to understand which algorithm is suitable for the product in question. Here are a few algorithms commonly used in a RS;
**ALS (Alternating Least Square)** which is easy to implement, easy to understand, and not resource taxing.
**KNN (K-Nearest Neigbor)** which is fast in the learning phase but slow in recall phase (the model is applied to new data). KNN is also called **Lazy Learners**.
**Rule-Based algorithm** on the other hand is the opposite of KNN. It is expensive to update and train.
**Matrix Factorization** is a matured field of ML. It is one of the commonly used algorithms. It is memory efficient and versatile eg, minimizing error using stichastic gradient descent or ALS technique, apply SVD (Singular Value Decompose) approach.
**CCO (Correlated Cross Occurrence)** kinds of products are more likely to benefit from recommendations? Specifically, are mainstream products or niche projects more likely to benefit from recommendations?

When choosing an algorithm, we have to be mindful how expensive to train and whether the model produces results that meet busines needs. Obviously, various algorithms can be combined or chained to together to get the desired results.

Other question to ask is, what is it about a product that makes it more likely to elicit a response from a consumer when it’s recommended? For example, the ratings of the products or the price of the product or the type of the product — do they influence whether recommendations are effective for that product?

There was a marketing research done by Kownledge @ Wharton highlighting the importance of; 
https://knowledge.wharton.upenn.edu/article/recommended-for-you-how-well-does-personalized-marketing-work/
“Today, producers are used to thinking about, how does our product get discovered by consumers? They need to also ask, how does our product get discovered by algorithms?” 

The article also mentioned some surprised findings "Now, another result that surprised us was that recommendations and ratings are substitutes for each other. Again, prior to the study, we expected that people would respond to recommendations for things when they are highly rated, and we did find that. But what surprised us was that their response is even greater when the products have a lower rating. That suggests that there’s this effect of recommendations as substitutes for ratings, and we hadn’t predicted that beforehand."

Therefore, simply recommending users based on their browsing or purchasing history/ habits, how similar their behavior to other users, etc, will risk losing the users because of boredom (always recommend the same stuff) and also losing potential sales eg, niche products that weren't shown to the user before. For eg, Amazon has thousands of products and only a small fractions of the products were exposed/ recommended to the users. Imagine a recommender systems capable of recommending products users has never seen before which the users may like. 
<br><br>

## Business Recommendation
### All things being equal and based on the metrics, business should consider using the Collaborative Filtering as the RS. 

#### One particular problem busines must be aware of is, cold-start issue. That is, a RS not being able to make recommendations to new users as there are no historical activities in the system. To overcome this, business can consider asking the user to provide information about their preferences on movies and genres during registration. This way, at least some information about the user's preference is captured for the RS to work with.

#### After implementation, business can evaluate the effectiveness of the newly implemented RS by using;
- A/B-testing or Multivariate testing.
- Click-Through-Rate (CTR), Conversion Rate (CR) to measure KPIs. 
- the good old Return On Investment (ROI) to measure performance but ROI calculations can be very fuzzy and depends on large number of unknowns.

Last but not least, it is always a good idea to keep an eye on the churn rate and customer retention rate.

---

### Data Source
Due to GitHub fize size limitation (file size must not > 100mb), the 1 million ratings dataset will be used.

1M datasets from Grouplens: https://grouplens.org/datasets/movielens/1m/

Full details on all available datasets: https://grouplens.org/datasets/movielens/

Data dictionary: http://files.grouplens.org/datasets/movielens/ml-latest-README.html

---

### Capstone Project Blog
Head over to https://donutmypet.wordpress.com/2020/04/21/my-capstone-project-journey-at-dsi-13/ for a glimpse of my capstone journey.