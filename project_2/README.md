# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) 

# Project 2: Estimate Sales Price of Housing at Ames, Iowa


## Executive Summary

The objective of this project is to analyze the Ames Housing data to predict house prices using various regression models. The data contains a host of features about houses in Ames, Iowa. The features consist of floor areas of different levels, bedrooms, garage, location, etc. Data can be downloaded from Kaggle's Housing Prices: Advanced Regression Techniques. It comes with a train set, test set, data dictionary and a sample result file for competition submission. (link below).

Data Source: https://www.kaggle.com/c/dsi-us-6-project-2-regression-challenge/data

---


### Contents:

- [Exploratory Data Analysis](EDA) 
- [Data Cleaning](#Data-Cleaning)
- [Data Visualization](#Data-Visualization)
- [Pre-processing](#Pre-processing)
- [Modeling](#Modeling)
- [Interpretation of Results](#Interpretation-of-Results)
- [Business Recommendations](#Business-Recommendations)
- [Sources](#Sources)

---

### EDA

Standard operating procedures on data cleaning and munching along with initial EDA of the data is a must as it provides a better understanding of the features and its correlations;
- with sales price which aids in features selection
- with other independent features that can help to decide to combine related ones eg, garage cars and garage area and drop features that are multicolinear with one another.

Data science is not a linear process. Take this project as an example; EDA, data cleaning, and exploratory visualizations is an iteration process. Here's an example:

1. During initial EDA, missing values are abundant and spread acprss many features.
2. Data dictionary can provide some insights to help decide whether to drop, impute or replace with suitable values like zeroes but without domain knowledge or familiarity of local settings, it can be a challenge. 
3. Plot charts to detect anomalies such as out'liars' and to have a better feel of the relationship between features instead of relying on eye-balling raw data.
4. Any data modifications at the earlier stage that has negative impact on data quality, will need to recycle back, re-load data, re-think approach, and find a better solution.


### Data Cleaning
- Decide how to impute null values.
- Decide how to handle outliers.
- Is it better to combine some of the features?
- Will interaction terms helps in building a better model?
- Should collinear features be dropped manually?

---

Preprocessing: Use One-hot encode of categorical variables, scale data, train test split data for a more effective model.
Modeling: cross-validation and apply both techniques to score a model.
Evaluate several models: Establish baseline score, fit linear regression, improve model using Lasso/ Ridge/ Elastic Net with default parameters and tune hyperparameters for production model.
Business Recommendations: Interpret results and propose practical recommendations to business for consideration.

---

### Data Visualization
Data Visualization is important as different chart types provide different insights. For eg, histograms of total/ composite scores revealed types of distributions while heatmaps give a better picture about correlationship amongst features.

- Look at distributions of selected features. Normal distribution is good otherwise can use standardization technique.
- Look at correlations amongst features.
- Look at relationships to target (scatter plots for continuous, box plots for categorical).

---

### Pre-processing
- One-hot encode categorical variables.
- Train/test split your data before scaling to avoid introducing biasness into the validation dataset.
- Scale selected numeric data only and should not include dummy columns.

---

### Modeling
- **Establish baseline score.**
- Fit linear regression. Look at coefficients to see if they are reasonable and not wildly overblown.
- Fit lasso/ridge/elastic net with default parameters.
- Tweak or remove features that might be causing issues to model results.
- Tune hyperparameters.
- **Identify a production model.**
- Refine and interpret production model.

---

### Interpretation of Results:
Sale price distribution is not normal. It shows 'peakedness' (kurtosis which mean there are outliers) and positively skewed. Postively skewed means not many people buy highly priced property which explains the long tail on the right. From the plot, majority buys average
priced properties between $100k to $250k range.

The boxplot shows there are a handful of properties sold above the maximum values including a number of outliers.

Scatter plots on the some of the features like ground living area, basement living areas, etc. shows a very strong correlation with sales. A very interesting observation was, newer buildings (newly built or remod/add) can command a higher price than older buildings. Garage is also seems to be an important factor for home buyers perhaps due to almost every family drives and owns a few cars. Another interesting observation on the garage features was, buyers willing to pay very good price for property with 1 to 3 car park lots; price drop drastically for properties with more than 3 car park lots.

Other than missing data, the Ames dataset contain relevant stats to build good models to predict sales price.

---

### Business Recommendations:

Conclusions:
From the analysis, it is no doubt pricing has been on an increasing trend gradually for a about century from 1885 to 1985 and then exponentially thereafter. Majority of the houses are transacted between the inter-quartile range of $129,825 to $214,000. However, the min and max is extremely wide between $13k and $612k; the extremes are mostly outliers. The mean ($181k) and the median ($163k) is not too far apart, about $20k difference which confirms that majority of the housing is priced around the mean.

Recommendation:
The property agency business division should target average home buyers since that is the bulk of the transactions. From securing a sales persepctive, there is a higher chance of concluding a sale with these category of customers.

For the developer division, the business should include features such as up to 3 car park lots, big ground living areas, total living areas, etc when developing properties around the area. New building can fetch better sales price too.

---

### Sources:
Data Source: https://www.kaggle.com/c/dsi-us-6-project-2-regression-challenge/data