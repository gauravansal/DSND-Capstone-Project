# Capstone Project: Create a Customer Segmentation Report for Arvato Financial Solutions

### Table of Contents

1. [Project Overview](#overview)
2. [Project Components](#components)
3. [Installation](#installation)
4. [File Descriptions](#files)
5. [Instructions](#instructions)
6. [Results](#results)
7. [Notes on Class Imbalance](#class_imbalance)
8. [Licensing, Authors, and Acknowledgements](#licensing)

## Project Overview<a name="overview"></a>

In this project, I had analyzed demographics data for customers of a mail-order sales company in Germany, compared it against demographics information for the general population. I had used unsupervised learning techniques to perform customer segmentation, identifying the parts of the population that best describe the core customer base of the company. Then, I had applied what I've learned on a third dataset with demographics information for targets of a marketing campaign for the company, and used a trained model to predict which individuals are most likely to convert into becoming customers for the company. The data used has been provided by our partners at Bertelsmann Arvato Analytics, and represents a real-life data science task.

## Project Components<a name="components"></a>

The project has three major parts: the customer segmentation report, the supervised learning model, and the Kaggle Competition.
1. Customer Segmentation Report: This part used the unsupervised learning techniques to perform customer segmentation, identifying the parts of the population that best describe the core customer base of the company.

2. Supervised Learning Model: This part would use the third dataset with attributes from targets of a mail order campaign and use the previous analysis to build a machine learning model that predicts whether or not each individual will respond to the campaign.

3. Kaggle Competition: Once best performing model would be identified, it would be used to make predictions on the campaign data as part of a Kaggle Competition. We would rank the individuals by how likely they are to convert to being a customer, and see how our modeling skills measure up against the fellow students.

## Installation<a name="installation"></a>

 - The code should run with no issues using Python versions 3.*.
 - No extra besides the built-in libraries from Anaconda needed to run this project
 * numpy
 * pandas
 * seaborn

## File Descriptions<a name="files"></a>

There are four data files associated with this project:
* `Udacity_AZDIAS_052018.csv`: Demographics data for the general population of Germany; 891 211 persons (rows) x 366 features (columns).
* `Udacity_CUSTOMERS_052018.csv`: Demographics data for customers of a mail-order company; 191 652 persons (rows) x 369 features (columns).
* `Udacity_MAILOUT_052018_TRAIN.csv`: Demographics data for individuals who were targets of a marketing campaign; 42 982 persons (rows) x 367 (columns).
* `Udacity_MAILOUT_052018_TEST.csv`: Demographics data for individuals who were targets of a marketing campaign; 42 833 persons (rows) x 366 (columns).

Each row of the demographics files represents a single person, but also includes information outside of individuals, including information about their household, building, and neighborhood. Use the information from the first two files to figure out how customers ("CUSTOMERS") are similar to or differ from the general population at large ("AZDIAS"), then use your analysis to make predictions on the other two files ("MAILOUT"), predicting which recipients are most likely to become a customer for the mail-order company.
The "CUSTOMERS" file contains three extra columns ('CUSTOMER_GROUP', 'ONLINE_PURCHASE', and 'PRODUCT_GROUP'), which provide broad information about the customers depicted in the file. The original "MAILOUT" file included one additional column, "RESPONSE", which indicated whether or not each recipient became a customer of the company. For the "TRAIN" subset, this column has been retained, but in the "TEST" subset it has been removed; it is against that withheld column that your final predictions will be assessed in the Kaggle competition. Otherwise, all of the remaining columns are the same between the three data files.

For more information about the columns depicted in the files above, one can refer to two additional meta-data files(.xlsx) provided and one manually created file(.csv).

* `DIAS Information Levels - Attributes 2017.xlsx`: is a top-level list of attributes and descriptions, organized by informational category.
* `DIAS Attributes - Values 2017.xlsx`: is a detailed mapping of data values for each feature in alphabetical order.
* `feature_summary_complete.csv`: is a feature summary file and is created manually using the above 2 files mapping all the attributes with information level, type & missing_or_unknown information to assist in our analysis.

## Instructions<a name="instructions"></a>
1. Since the data files are not available publicly as dataset are highly proprietary, the Jupyter notebook is just for exploration. An HTML file has been provided as another means to check the notebook.

2. `feature_summary_complete.csv` should be used for data pre-processing.

3. The Jupyter notebook produced a file called `kaggle_submission_file.csv` which was submitted to Kaggle for the in-class competition.


## Results<a name="results"></a>
* It was necessary to apply the majority of CRISP-DM (CRoss-Industry Standard Process for Data Mining) to both parts of the project. Business Understanding was slipped in as  part of the problem description, but Data Understanding, Data Preparation, Modelling and Evaluation had to be developed from scratch. The general rule that Data Preparation is the most time consuming part in the process could be verified once again.

* Part 1 presented how unsupervised learning techniques — namely PCA and Clustering with KMeans — were applied to distinguish groups of individuals that best describe the core customer base of the mail-order company. A supervised learning model, in form of LogisticRegression, then helped to identify the main characteristics of these individuals.

* Part 2 presented the straightforward way of building a supervised learning model. The base performance of various classifiers was determined. With the help of GridSearchCV the most promising one — GradientBoostingClassifier — was fitted respectively tuned to the training dataset (considering stratified cross-validation) and its performance was evaluated via ROC AUC. A short analysis of the most important features completed the model creation before using it for predicting on the testing dataset which individuals of a marketing campaign are most likely to convert into becoming customers.

* Part 3 presented the [Kaggle in-class competition](https://www.kaggle.com/c/udacity-arvato-identify-customers/overview) and `kaggle_submission_file.csv` was submitted to obtain a kaggle score which is roc_auc score on the testing data. Through Kaggle score, position of the participant in the leaderboard was determined.

* [Project Notebook: Create a Customer Segmentation Report for Arvato Financial Solutions](https://nbviewer.jupyter.org/github/gauravansal/DSND-Capstone-Project/blob/master/Arvato%20Project%20Workbook.html)
* [Blog Post: Identify potential new Customers more efficiently using Machine Learning](https://medium.com/@ansal.gaurav/identify-new-customers-more-efficiently-using-machine-learning-15a10255baf8)

## Notes on Class Imbalance<a name="class_imbalance"></a>

 - Since there is a large output class imbalance, predicting individual classes and using accuracy does not seem to be an appropriate performance evaluation method. Instead, the model will be using ROC-AUC to evaluate performance.

 - Aside from the Kaggle competition (see section below) using ROC-AUC as the score, the metric is suitable for binary classification problems such as this. ROC curves give us the ability to assess the performance of the classifier over its entire operating range. The most widely-used measure is the area under the curve (AUC). The AUC can be used to compare the performance of two or more classifiers. A single threshold can be selected and the classifiers' performance at that point compared, or the overall performance can be compared by considering the AUC". Compared to the F1 score, the ROC does not require optimizing a threshold for each label.

## Licensing, Authors, and Acknowledgements<a name="licensing"></a>

<a name="license"></a>
### License
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

<a name="acknowledgement"></a>
### Acknowledgements

This app was completed as part of the [Udacity Data Scientist Nanodegree](https://www.udacity.com/course/data-scientist-nanodegree--nd025). The data was originally sourced by Udacity from [Arvato Financial Solutions](https://medium.com/r/?url=https%3A%2F%2Fwww.arvato.com%2Fus-en%2Fsolutions%2Ffinancial-solutions.html), a [Bertelsmann](https://medium.com/r/?url=https%3A%2F%2Fwww.bertelsmann.com%2F) subsidiary.