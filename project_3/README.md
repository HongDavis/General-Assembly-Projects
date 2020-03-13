# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) 

# Project 3: Web APIs & Classification


## Executive Summary

Obtain postings from 2 reddit threads ('The Truth is Here' (truth) and 'No Sleep' (nosleep)) using web scraping technique. The 2 groups are very different as in;
The truth thread is a collections of personal encounters with the unknown eg, non-fiction stories dealing with spirits, paranormal, strange happenings, and unexplained sightings while the nosleep thread is for authors to share their original horror stories.

The objective is to find out more about the attributes of the 2 threads so as to focus more on the group that are more active in the thread. Business can target the active group with specific advertisements. A simple measurement is to determine the length of posts as it is safe to assume longer posts mean that users stayed longer at Reddit to type. Generally, the longer a person exposed to an advertisement, the high the chance the user may want to check out the ad that may convert to a sale subsequently.

Predictor is the 'selftext' and target is the 'subreddit'. Naive Bayes will be used for the initial model to have a better feel of the data collected. Either K-Nearest Neighbor or Logistic Regression will be used with the aim to improve the initial model.

Data Source:
https://www.reddit.com/r/nosleep.json
https://www.reddit.com/r/Thetruthishere.json

---


### Contents:

- [Obtain Data](Obtain-Data)
- [Exploratory Data Analysis](EDA)
- [Data Cleaning](#Data-Cleaning)
- [Pre-processing](#Pre-processing)
- [Modeling](#Modeling)
- [Interpretation of Results](#Interpretation-of-Results)
- [Business Recommendations](#Business-Recommendations)
- [Sources](#Sources)

---

### Obtain Data
Scrap about 3k posts from (120 pages x 25 posts per page) of 'The Truth is Here' and 'No Sleep' threads from Reddit. Scraping takes a long time. On average, to scrap 120 pages takes around 45 mins with a random time gap set between 2 to 25 seconds. The random time gap is required to avoid being barred from scraping from the website.
url = 'https://www.reddit.com/r/nosleep.json'
url = 'https://www.reddit.com/r/Thetruthishere.json'



### Exploratory Data Analysis
Perform initial EDA of the data to have a better understanding of the features and its correlations eg, attributes of each thread for eg, general length of posts.

1. During initial EDA, there are a lot of duplicates especially the No Sleep thread which is about 40%.
2. There are more advertisements in the No Sleep thread than the Truth thread. There are also more adult promotions in the No Sleep thread. 
3. Plot charts to have a visual on the length of posts.

### Data Cleaning
Removes duplicates and adult advertisements (NSFW) post.
Removes irrelevant features.

---

### Data Visualization
- Chart the length of post for each thread to see which thread spend more time at Reddit website.
- Chart the most frequently used words.

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
- Compute the ratio of a thread against the other. Take the higher ratio as the baseline score.
- Use Naive Bayes Multinomial model to see whether it is better than the baseline.
- Use Logistic Regression model to see whether it is even better.

---

### Interpretation of Results
Although Naive Bayes Multinomial classifer is suitable for this type of task ie, classifying binary output but other models with hyperparameters tuning capabilities such as Logistic Regression, KNN, Tf/ Idf can build more accurate models. In this particular case, Logistic Regression's model produces a more accurate results in classifying posts in their respective thread.

With more time and data, other modeling techniques such as sentiment analysis and topic modeling may provide better insights to the Nosleep group's behaviour as well as the Truth group. But with the analysis done above, the length of posts does provide some form of indication that No Sleep group spend more time at Reddit than the Truth group.

---

### Business Recommendations:
Durng the EDA phase, the fact that there are more NSFW in the No Sleep thread than the Truth thread shows that either the Truth thread is actively blocking ads or other companies is getting results from the No Sleep thread. Therefore, placing ads in the No Sleep thread makes more sense and more bang for the buck too. 

It will be good if more data can be obtained to do topic modeling to segment No sleep group users by topics. This way, specific advertisements can be targeted to the respective topical group. Business can approach Reddit for posting pop-up advertisements based on the contents posted by the users. For eg, business can place advertisements such as computer games, online games to users posting fantasy related stories. For user group posting horror stories, business can advertise on-demand movies subscription or novel that are horror genre.

If reddit's system has adaptive capabiliy, business can consider using the feature for eg, analytics can be perfomed and pop-up advertisement promoting products and services that are related to the contents can be activated while the user is still typing. 

As for the Truth group, business may want to offer products and services such as councelling service, yoga lessons, supplements with calming effects, etc. to help users that may be trying to get over their traumatic experience. 

Besides working with Reddit on advertisement placements, business must get Reddit to provide analytics such as ‘click-rate’ for ad performance evaluation.

---
