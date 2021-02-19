# Pump it up: Data Mining the Tanzanian Water Crisis

## Overview

This project aims to identify waterpoints (sources of clean water) that need repair in the developing country of Tanzania. With a population of 57 million, Tanzania only provides clean water to a little less than half of its population. Many of their waterpoints are in need of repair or have failed altogether. Access to clean water is essential to well-being and is a basic right for all individuals. Using data from Tarrifa and the Tanzanian Ministry of water, we will try to predict which water pumps are functional and which are in need of repair.

## Business Problem

Communities across Tanzania need a way to understand which pumps are operating and which pumps are in need of repair. In order to do so, we have built a model which will aim to identify functional and non-functional waterpoints. Understanding which pumps will fail and which will not may help improve maintenance operations and ensure that clean water is available to people residing in Tanzania.

## Data

The Tanzanian Ministry of Water and Tarrifa have provided us with data of waterpoints across tanzania. Every waterpoint has a unique ID, data on that given waterpoint (type of extraction, quality of water, region it is in, etc.), and a status level (functional, functional in need of repair, and non-functional). The data consists of over 59,000 records and each record has roughly 38 features. 

### Cleaning and Feature Engineering

This project uses data cleaning and feature engineering  To make our model a bit simpler, we categorized non functional pumps and pumps that need repair into the same group, as each of those pumps will need to be serviced. This also addressed the class imbalance between each variable. We also cleaned up our data, as there were missing values in multiple columns. For example, if "construction year" of the waterpoint was missing a value, we filled that value with the mean construction year of all waterpoints within that given region. We also engineered one column "age" to equal the age of the waterpoint when the data was collected. Cleaning our data and building these features helped make our model more interpretable and significant.

## Methods

Classification analysis was used in order to predict the status level of a pump. The baseline was set at 54% accuracy based off of our majority score. We trained five separate classifier models: Logistic Regression, K-Nearest Neighbor, Random Forest, AdaBoost and Gradient Boosting.
