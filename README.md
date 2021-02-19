<p align="center">
 <img width="650" height="325" src=images/tanzania_flag2.jpg>
 </p>

# Pump it up: Data Mining the Tanzanian Water Crisis

## Overview

This project aims to identify waterpoints (sources of clean water) that need repair in the developing country of Tanzania. With a population of 57 million, Tanzania only provides clean water to a little less than half of its population. Many of their waterpoints are in need of repair or have failed altogether. Access to clean water is essential to well-being and is a basic right for all individuals. Using data from Tarrifa and the Tanzanian Ministry of water, we will try to predict which water pumps are functional and which are in need of repair.

<p align="center">
 <img width="900" height="400" src=images/water_well.jpg>
 </p>

## Business Problem

Communities across Tanzania need a way to understand which pumps are operating and which pumps are in need of repair. In order to do so, we have built a model which will aim to identify functional and non-functional waterpoints. Understanding which pumps will fail and which will not may help improve maintenance operations and ensure that clean water is available to people residing in Tanzania.

## Data

The Tanzanian Ministry of Water and Tarrifa have provided us with data of waterpoints across tanzania. Every waterpoint has a unique ID, data on that given waterpoint (type of extraction, quality of water, region it is in, etc.), and a status level (functional, functional in need of repair, and non-functional). The data consists of over 59,000 records and each record has roughly 38 features. 

## Methods 

### Cleaning and Feature Engineering

This project uses data cleaning and feature engineering  To make our model a bit simpler, we categorized non functional pumps and pumps that need repair into the same group, as each of those pumps will need to be serviced. This also addressed the class imbalance between each variable. We also cleaned up our data, as there were missing values in multiple columns. For example, if "construction year" of the waterpoint had a missing value, we filled that value with the mean construction year of all waterpoints within that given region. We also engineered one column "age" to equal the age of the waterpoint when the data was collected. Cleaning our data and building these features helped make our model more interpretable and significant.

### Models Development

Classification analysis was used in order to predict the status level of a pump. The baseline was set at 54% accuracy based off of our majority score. We trained five separate classifier models: Logistic Regression, K-Nearest Neighbor, Random Forest, AdaBoost and Gradient Boosting. Logistic Regression wass our simplest model, and we derived multiple random forest models with different levels of depth.

## Results

Our simplest model, Logistic Regression, came back with a confusion matrix that produced a 66.2% accuracy score and a 53.3% recall score. For our purposes, we were looking to minimize recall as we want to reduce the amount of False Negatives (predicting the pump is functional when it is not) as possible. Below is and ROC Curve illustrating the tradeoff between Sensitivity and Specificity. 

<p align="center">
 <img width="500" height="300" src=images/roc_curve.png>
 </p>

Through running each model, Random Forest gave us the best result, with an accuracy score. We had three different models, each with their limitations. The model which maximized our total accuracy had no limit on max depth. However, this model was overfitting, so we decided to go with a model that had lower accuracy but would do better on unseen data (max_depth = 20). This resulted in and 82.35% accuracy and a sensitivity score of 75%. Below are the confusion matrix for both our simple model (Logistic Regression) and our final model (Random Forest).

#### Logistic Regression Confusion Matrix

<p align="center">
 <img width="900" height="500" src=images/logistic_reg.png>
 </p>
 
#### Random Forest Confusion Matrix

<p align="center">
 <img width="900" height="500" src=images/random_f_max_depth20.png>
 </p>

## Conclusions

- There is an overwhelming high amount of waterpoints that need to be serviced. Using our model, we can predict which waterpoints need to be serviced relatively accurately, helping communities and the Tanzanian government work quicker to address waterpoints that need repair.
- Older waterpoints are much more likely to be failing or in need of repair. Focusing your energies on those waterpoints could be beneficial.

## Next Steps

- Our current model could be improved dealing with our classification differently. We would not combine the waterpoints that need reapir and the non functional waterpoints. We would also have to implement methods to deal with this class imbalance.
- The population metric within our model had many observations with a population of 0. Although this may be true, we believed that too many observations had 0 population. We would look to reduce this number and see if we can find data on population for each given region.
- We would like to add recursive feature elimination as we believe that we have some variables that may not be impacting our model significantly. We may be able to get a simpler model with a better response by doing this.
- Given the potential of this model to improve well-being and quality of life for the people of Tanzania, we also suggest adding functionality to the usage of this model to prioritize pump replacement/installation in communities with larger populations or where there is not already a functioning well.

## Repository Structure

```
├── data
├── images
├── Final_notebook.ipynb
├── README.md
└── Pump_it_up_Data_Mining_the_Water_Crisis.pdf
```
