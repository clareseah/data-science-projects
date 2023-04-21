# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & NLP

# Problem Statement
We are a group of data scientists looking to open a cafe by making data-driven business decisions. 
In order to do this, we will first analyze posts from the 'Coffee' and 'Tea' subreddits to develop a classification model capable of segregating texts into 'Coffee' and 'Tea' categories. And then filter out the most popular flavour profiles and drinks to create a data driven menu.

# Executive Summary
### Notebook 01 - Data Collection
We used pushshift API to scrap reddit submissions from <a href="https://www.reddit.com/r/Coffee/" target="_blank">Coffee</a> and <a href="https://www.reddit.com/r/tea/" target="_blank">Tea</a> subreddits. 15000 submissions from each subreddit were scrapped, with timeframe set to 1<sup>st</sup> October 2022 0000hr and earlier.<br> 
14979 out of 15000 submissions from Coffee subreddit were collected. These submissions were posted between 3<sup>rd</sup> Jan 2022 and 1<sup>st</sup> October 2022.<br>
out of 15000 submissions from Tea subreddit were collected. These submissions were posted between 22<sup>nd</sup> August 2021 and 1<sup>st</sup> October 2022.
<br>
### Notebook 02 - Data Cleaning, Preprocessing and EDA
<b>2.1 Data Cleaning</b><br>
We start by removing redundant reddit submissions. First we will drop any duplicated submissions as well as submissions that were already removed by moderators, likely due to irrelevance to the subreddit. Next, repetive submissions by moderators were also dropped as these submissions do not add any value to our dataset. 
<br>
Finally, we will extract 'created_utc', 'subreddit', 'title',  'selftext' for our analysis. And create a new column 'post', that represents the concatenation of title and selftext. 
<br><br>
<b>2.2 Preprocessing</b><br>
In this section, we run an initial preprocssing on our dataset without dropping key labels (coffee & tea), in order to retain the context of the words and aid in the identification of words of interest. For example, green tea and black tea rank highly when we vectorize them. If we removed 'tea', these words of interest would lose their meaning. 
<br>Lemmitization is chosen over stemming so as to retain the context of the words as well. 
<br><br>
<b>2.3 EDA</b><br>
Words of interest found in unigram plots seem to be too general and not helpful compared to the words in bigram and trigram plots
It can also be observed that the words of interest can be split into a few categories:
   - Types of coffee/tea
   - Types of coffee/tea brewing techniques
   - Types of equiments used for coffee/tea brewing
   - List of coffee/tea brands and equipment brands
   
<br>
<b>2.4 Data Cleaning for Modeling</b><br>
Now that we have filtered out words of interest via CountVectorizationa nd TF-IDF Vectorization, we will run the dataset through preprocessing again, this time with coffee and tea related words within the stopwords list. 
<br>

### Notebook 03 - Modeling

In this notebook, we will look into modeling to find the best model, using the data that has been preprocessing in notebook 2.
Here are the steps we will follow to find the best model: 1. Setup a Baseline Model 2. Setup pyCaret to compare and identify models for further evaluation 3. Create and tune hyperparameters for the selected models in Step 2 4. Evaluate and select the best model
<br><br>
<b>Model Evaluation</b>

| Model       | Multinomial Naive Bayes (Baseline) | Logistic Regression | SVM - Linear kernel | Light Gradient Boosting Machine | Random Forest Classifier |
|-------------|------------------------------------|---------------------|---------------------|---------------------------------|--------------------------|
| Train score | 0.8956                             | 0.9207              | 0.9166              | 0.9067                          | 0.9880                   |
| Test score  | 0.8715                             | 0.8835              | 0.8803              | 0.8741                          | 0.8735                   |

We can observe that the 4 models evaluated have higher train and test scores compared to the baseline model.
Given that the train score is slightly higher than the test score for Logistic Regression, SVM - Linear kernel and Light Gradient Boosting Machine, it may indicate a slight overfitting of the model. Random Forest Classifier shows more severe signs of overfitting as the train score is significantly higher than the test score.

Overall, Logistic Regression is the best model as it has the highest accuracy score of 0.8835. This means that 88.4% of future posts are likely to be classified correctly by this model.


# Conclusion
Through modeling and hyperparameter tuning above, we can conclude that Logistic regression is the best model with 88% accuracy. However, it is important to note that logistic regression makes the assumption that observations in the dataset are independent of each other. This assumption may not hold true in the real world scenario as words may be dependent on each other due to the nature of languages.

Most Reddit users are from USA. In a study done between Dec'21 - May'22, almost 50% of desktop traffic originates from USA, followed by ~7% from UK as well as Canada.[<sup>2</sup>](#References) This shows that Reddit is not very popular among Singaporeans. Hence we can take the results from this analysis as a baseline, but we should also gather localised data for more accurate analysis on local preferences.

# Recommendation
Since we now have a classification model capable of segregating texts into 'Coffee' and 'Tea', we can work towards broaden the dataset and improving accuracy of the model by collecting more data. This can be done by increasing the number of reddit submissions scrapped and expanding the coverage to more platforms, especially ones that are highly used by Singaporeans such as quora, facebook, instagram, twitter etc.<br><br>

With the trained model, we can also explore other subreddits and categories such as Coffeebean, Starbucks etc. Posts from these categories can be run through our model to classify them before conducting further analysis to filter our most popular flavour profiles and drinks.<br><br>

We also recommend:
- Adding more stopwords to the list of stopwords, to filter out the noise in the dataset
- Explore Gensim package to gather more topics for analysis
- Expand the model to other relevant topics related to setting up a cafe (eg. interior design of cafe, food menu, equipment for brewing drinks etc)
- Run sentiment analysis on top words verified in ngrams to gather human emotion towards our planned cafe setup 

# References
<sup>1</sup> https://scikit-learn.org/stable/modules/generated/sklearn.naive_bayes.MultinomialNB.html#sklearn.naive_bayes.MultinomialNB<br>
<sup>2</sup> https://www.google.com/url?q=https://www.statista.com/statistics/325144/reddit-global-active-user-distribution/&sa=D&source=editors&ust=1665561748586934&usg=AOvVaw016E0b4h4Z6XkgRD4_ROvu
