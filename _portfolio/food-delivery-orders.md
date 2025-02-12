---
title: "Food delivery orders - data science case study"
excerpt: "A data science project including exploratory data analysis, feature engineering, modeling and testing for a food deliveries dataset"
header:
  image: /assets/images/clustering_user_venue_locations_same_zone_header_resized.png
  teaser: /assets/images/clustering_user_venue_locations_same_zone_header_resized.png
sidebar:
  - title: "Gabriel"
    image: /assets/images/profile-pic.jpeg
    image_alt: "logo"
    text: "Data Scientist"
  - title: "Tech stack"
    text: "Python ()"
  - title: "Skills"
    text: "Data processing, data cleaning, data visualization, machine learning, modeling, feature engineering, evaluation"
---


## Table of Contents
1. [Introduction](#introduction)
2. [Dataset](#dataset)
3. [Data Cleaning](#data-cleaning)
4. [Data Exploration](#data-exploration)
5. [Modeling](#modeling)
6. [Evaluation](#evaluation)
7. [Conclusion](#conclusion)
8. [Requirements](#requirements)

## Introduction
This project was born as a pre-assignment for the Wolt Applied Science Internship 2025.

The goal is to analyze and model the food delivery orders dataset, to gain insightful knowledge about the data and to make a few predictions. The process involves data cleaning, exploration, modeling, and evaluation.


## Dataset
The dataset used in this project is the "orders_autumn_2020" which contains information about customer orders. The dataset includes features such as time of order, delivery times, amount of items, user location, venue location, weather information.


## Data Cleaning
Dataset cleaning is performed in [`orders_cleaning.ipynb`](./orders_cleaning.ipynb)

Data cleaning involves handling missing values, and correcting data types. The steps include:
- Checking for missing values: missing weather information on 10 September 2020.
- Interpolated missing records.
- Converting data types to appropriate formats: TIMESTAMP to datetime.


## Data Exploration
Data exploration is performed in [`orders_exploration.ipynb`](./orders_exploration.ipynb)

Data exploration involves visualizing and summarizing the dataset to understand its structure and relationships. Key steps include:
- Descriptive statistics (mean, median, mode, etc.).
- Correlation relationship between all features (no unexpected strong correlations found)
- Exploration on Wolt KPI's : customer satisfaction, average order value (or quantity here), delivery times (impact by weather, day of the week, rush hour)
- Customer satisfaction:
    - no ratings in the data, but can compute a satisfaction rating based on the time "saved" on each delivery
    - found 14534 deliveries in an acceptable time range (5 minutes late - 10 minutes early)
    - CSAT score of 77.7% (in-line with industry benchmarks)
- Average order quantity (AOQ), with a focus on daily AOQ:
    - no strong correlations with weather
    - good correlation with day of the week (weekends see bigger orders)
    - autocorrelation function for daily AOQ shows a 7-day seasonality
    - avg daily AOQ: 2.7 items/order
- Delivery time impact:
    - some time lost when precipitation is high
    - no time lost when comparing weekday and weekend
    - no time lost during rush hours
    - the ESTIMATED_DELIVERY_MINUTES seems to properly increase when there are inconveniences (weekday, rush hour traffic, bad weather)
    - the users do not get low initial time estimates, impacting the ON_TIME_DELIVERY performance


## Modeling
Data modeling tasks are performed in [`orders_modeling.ipynb`](./orders_modeling.ipynb)

Modeling involves selecting and training machine learning models to make predictions based on the dataset.

### Clustering
A clustering based on K-means is implemented to separate the users into distinct groups based on features
- multiple clustering features and correlations were tested, the only significant impact was the user geographical location
- the dataset was split by user location into 5 clusters, or zones
- the venues were then added based on these zones
- the orders were classified then into two major categories: same-zone orders, and cross-boundary orders
- thus hinting efficient courier distribution


### Classification
Classification based on Random Forest
- trying to predict wether an order will remain in the same-zone, or if the courier needs to cross the zone boundaries to get the order
- splitting the data into training and testing sets.
- training the models on the training data.
- tuning hyperparameters for optimal performance.
Two predictions were selected:

#### Same-zone orders
Predicting if the order stays in the same zone

#### Venue cluster
Predicting if we can determine a venue's cluster, based on the user's information (user clusters go to preferred clusters, or they order all over the place)


## Evaluation
Evaluation involves assessing the performance of the trained models using metrics such as accuracy, precision, recall, and F1-score. Steps include:
- making predictions on the test data.
- calculating evaluation metrics.
    - same-zone orders predicted with 83% accuracy
    - venue clusters predicted with 64% accuracy
- comparing model performance
    - KNN was used to better predict the venue clusters


---
## Conclusions
- EDA showed interesting metrics on customer satisfaction and delivery times
- no extreme correlations with weather, day of the week, hour
- used clustering methods to categorize the dataset into optimal "user zones"
- try to predict if orders remain inside the zones, or cross the zone boundary
- try to predict venue clusters, based on order information
- evaluate performance of modeling

Further developments:
- hyper-parameter search to optimize prediction
- test other classifiers
- time series analysis on AOQ, or daily/weekly orders
    - use SARIMA (because data has seasonality)
    - forecast number of orders on a particular day (focus on weekday vs weekend)
- try other clustering methods (e.g. DBSCAN)
