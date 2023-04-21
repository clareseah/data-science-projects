<img src="./images/blackfin_logo_black.png" style="float: left; margin: 0 20px 0 20px; height: 120px">  

# Project 2 - Ames Housing Data and Kaggle Challenge

### Problem Statement 

Home owners are facing issues valuing their property due to the recent volatility of the housing market in the US.

Blackfin aims to build a model that will assist home owners and buyers with getting the best price based on the latest market situation. 

### Data Dictionary

* Data dictionary can be found on kaggle,<a hred = "https://www.kaggle.com/competitions/dsi-us-11-project-2-regression-challenge/data">here</a>

### Executive Summary: 
<b>Notebook 1 - EDA</b><br>
Preliminary exploratory data analysis was done on the train dataset. Box plots and strip plots were plotted for categorical features and histogram and scatter plots for numerical features to explore their relationship with Saleprice

<b>Notebook 2 - Data Cleaning</b><br>
Train and Test datasets were cleaned in this notebook. 
1. Replacing null values 
    - Understanding the Data Dictionary from Kaggle
    - Most null values corresponded to ‘NA’
2. Decide on how to handle missing values
3. Identifying & Removing outliers
4. Encode dataset
5. Scaling Numerical Features

<b>Notebook 3 - Modeling</b><br>
A baseline model was created in this notebook.
The dataset was fitted into other regression models to find which has the best r<sup>2</sup> and RMSE scores. This helped narrow down on which models to use to help predict saleprices. 

<b>Notebook 4 - Production Model and Insights</b><br>
The scores of Lasso and Ridge Regression was compared in this notebook.
Test scores were predicted and submitted to Kaggle to determine which regression model works best for predicting saleprices. 
Conclusions and recommendations were also covered in this notebook. 

### Conclusion and Recommendations 
<b>Conclusion</b>
After submitting our test predictions to Kaggle, Lasso Regression scores better than Ridge Regression. Hence, <b>Lasso regression</b> will be used to predict saleprices. 

Using Lasso Regression, we got an RMSE of of 22092, which is a huge improvement compared to the baseline RMSE score of 79853. The Lasso model also has a high training R<sup>2</sup> score of 0.9247 which means that it can account for up to 92.5% of variance in saleprice. 


<b>Recommendation</b>
1. We recommend using more recent data as the dataset given was saleprices between 2006 and 2010
2. Can refer to the heatmap below, to make decisions on feature selection and feature engineering
    - Total years lived in = year sold - year built
    - Total Interior square footage = TotalBsmtSF + GrLivArea + GarageArea
3. Identify and remove features with multicollinearity 
4. Take into account macroeconomic factors such as interest rates, inflation rates, GDP, unemployment rates