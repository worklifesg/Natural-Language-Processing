## Projects (NLP)
In this section, we will perform certain projects pertaining to NLP.

### 1. Sentiment Analysis using Real Time Twitter Data

This project is a simple program where we will fetch current real time data from Twitter using Twitter API (credentials won't be shared here, but are used in execution for this program at my backend).

For our analysis we will be using last 200 recent tweets from Twitter Accounts that are most followed on Twitter. We choose different profession based personalities and companies from top 20.

    Barack Obama (Former US President) - @BarackObama
    Justin Bieber (Musician) - @justinbieber
    Cristiano Ronaldo (Sports) - @Cristiano
    Donald Trump (Former US President) - @realDonaldTrump
    Narendra Modi (Prime Minister of India) - @narendramodi
    CNN Breaking News (News Channel) - @cnnbrk
    Twitter (Social Media Platform) - @twitter 

Then in next step, we will simply visualize times series visualization for their tweets and their activity analysis as per different dates.

Final step is to analyze sentiment analysis on this tweets first by cleaning and understanding the tweets using Regex and later applying Textblob for sentiment analysis nature of their tweets. These are the following coding steps that are implemented to complete this sentiment analysis

As we can request 200 tweets per time alloted, so we need to analyze these seven accounts separately and then compare their sentiment together in a different visualization charts
Code Steps:

***[Data Engineering](https://github.com/worklifesg/Natural-Language-Processing/blob/main/Projects/1.%20Sentiment%20Analysis%20using%20Real%20Time%20Twitter%20Data/0_Data_Engineering.md)***

    Import libraries (tweepy, pandas, numpy, matplotlib, textblob, re)
    Creating Twitter App (using Twitter Developer API Account)
    Importing Tweets (cuurent real time last 200 tweets)
    Creating a tweet combined DataFrame with details for each data

***[Data Cleaning & Structuring](https://github.com/worklifesg/Natural-Language-Processing/blob/main/Projects/1.%20Sentiment%20Analysis%20using%20Real%20Time%20Twitter%20Data/1_Data_Cleaning_Structuring.md), [EDA & Data Visualization](https://github.com/worklifesg/Natural-Language-Processing/blob/main/Projects/1.%20Sentiment%20Analysis%20using%20Real%20Time%20Twitter%20Data/2_EDA_DataVisualization.md)***

    Tweets Time Series Analysis

***[Sentiment Analysis](https://github.com/worklifesg/Natural-Language-Processing/blob/main/Projects/1.%20Sentiment%20Analysis%20using%20Real%20Time%20Twitter%20Data/3_Sentiment_Analysis.md)***

    Clean Tweet (using Regex function)
    Analyze Sentiment (TextBlob) - Positive, Negative, Neutral Tweets

***Final Result and Conclusion***
<p align="center">
  <img width="600" alt="java 8 and prio java 8  array review example" img align="center" src ="https://github.com/worklifesg/Natural-Language-Processing/blob/main/images/EDA7.png">
</p>

****Conclusion****

 * It is observed that Barack Obama has highest number of followers on Twitter even though he is not current US President but due to his positive tweets towards everyone on different issues (60%).
 * On other side, musician and sports people are always in controversy and have split tweets between positive and neutral tweets.
 * Politician like Narendra Modi plays safe as by giving neutral tweets and is very cautious about his image in public and has negative tweets even less than twitter itself.
 * While comparing Donald Trump with other political leaders, he seems to be open about various issues and tends to be on negative side and playing bit safe with 50% neutral tweets.
 * As predicted news channel tend to give negative news a lot, CNN breaking News leads at the top of having 20% negative tweets.
 

### 2. Spam Ham Detection and Patterns
In this program, spam filter for text messages using NLP is performed.

 * Before applying machine learning algorithms to predict whether the text message is spam or not, data pre-processing and exploring data analysis is perfomed using NLP pre-processing techniques.
 * Data Pre-processing includes Normalization, removing specific strings such as email addresses, URLs, money symbols, phone numbers and numbers. Also removing puntuations, stop words, and stemming is performed.
 * Next feature engineering is done through Tokenization using Ngrams and TF-IDF statistics.
 * A robust classifier is built with splitting the data into train and test with 70/30 split ratio . The training model is tested to built with different ensemble methods such as Random Forest, XGBoost, AdaBoost, CatBoost and LightGBM classifiers. Also, Naives Bayes has achieved better results before, so ensemble methods will be tested out with NB.

***Data Engineering***

    Import libraries
    Reading, Preprocessing and Exploring dataset

<p align="center">
  <img width="300" alt="java 8 and prio java 8  array review example" img align="center" src ="https://github.com/worklifesg/Natural-Language-Processing/blob/main/images/Spam1.png">
  <img width="300" alt="java 8 and prio java 8  array review example" img align="center" src ="https://github.com/worklifesg/Natural-Language-Processing/blob/main/images/Spam2.png">
  <img width="900" alt="java 8 and prio java 8  array review example" img align="center" src ="https://github.com/worklifesg/Natural-Language-Processing/blob/main/images/Spam3.png">
</p>

***Text Pre-processing and Feature Engineering***

    Normalization, removing specific strings 
    Removing puntuations, stop words, and stemming 
    Tokenization using Ngrams and TF-IDF statistics

***Building classifier, training and prediction models***

    Splitting the data 70/30
    RandomForestClassifier
    AdaBoostClassifier
    CatBoostClassifier
    XGBoost
    LightGBM
    Naives Bayes

<p align="center">
  <img width="400" alt="java 8 and prio java 8  array review example" img align="center" src ="https://github.com/worklifesg/Natural-Language-Processing/blob/main/images/Spam4.png">
  <img width="400" alt="java 8 and prio java 8  array review example" img align="center" src ="https://github.com/worklifesg/Natural-Language-Processing/blob/main/images/Spam5.png">
</p>

***Final Result and Conclusion***

All above ensemble methods are compared with Naives Bayes technique which is quite popular in solving spam.ham detection problem in NLP.

First three classifiers, we calculated confusion matrix as well where type I (FP) and type II (FN). Mainly Type II error, which is False Negative is quite dangerous situation and we would like to minimize or eliminate it in our predictive model

| Classifier  | Type (II) error | Type (I) error | ROC-AUC Score |
| ------------- | ------------- | -------------- | ------------- |
| RandomForestClassifier  | 39  | 0 | 91.29% |
| AdaBoostClassifier | 18  | 10 | 95.63% |
| CatBoostClassifier  | 30  | 1 | 93.26% |
| XGBoost  |   |  | 98.03% |
| LighGBM  |   |  | 97.57% |
| Naives Bayes  | 14  | 6 | 96.67% |

It is seen from above table that both type II error (most concerned) is minized using Naives Bayes technique as compared to RandomForest and CatBoost classifiers. AdaBoost classifier has false negative near to NB (i.e. 18) but has lower ROC score than NB.

In terms of ROC-AUC score, XGBoost and NB can be chosen as appropiate classifier that can be used with the highest prediction and separating two classes very well with 98.03% and 96.67% respectively. NB is chosen over LightGBM because for low rate of false positive and false negative. Therefore ,we will use NB as final classifier for modeling spam/ham detection problem and will evaluate in the end to see whether it is a better fit.


***Conclusion***

It is seen that NB works good while evaluating different messages. Here is the summary of evaluation regarding the prediction of different messages.

| Text 	| Original Class 	| Predicted Class 	| Evaluation
| ------------- | ------------- | -------------- | ------------- |
| Limited Time: Claim Your Exclusive Reward (Details Inside) |	SPAM |	HAM |	Predicted Incorrect|
| Get your welcome bonus 1000 EUR or 1 BTC + 150 FREE SPINS |	SPAM |	SPAM |	Predicted Correct|
| Congrats! You have unlocked a Discount of upto 60% |	SPAM |	SPAM |	Predicted Correct|
| Pizza Pizza Order Confirmation |	HAM |	HAM |	Predicted Correct|
| Reminder: Your electricity bill |	HAM |	HAM |	Predicted Correct|
| Review your upcoming delivery |	HAM |	SPAM |	Predicted Incorrect|

The first text is originally SPAM but was detected as HAM. Also last text which is basically from Amazon is HAM but it is detected as SPAM as program didn't had sufficient training to detect such small texts.

If I modified Amazon message to 'Amazon.ca Review forthcoming purchase', it will be detected corrected as HAM
 
