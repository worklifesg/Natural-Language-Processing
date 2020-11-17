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

***Data Engineering***

    Import libraries (tweepy, pandas, numpy, matplotlib, textblob, re
    Creating Twitter App (using Twitter Developer API Account)
    Importing Tweets (cuurent real time last 200 tweets)
    Creating a tweet combined DataFrame with details for each data

***Data Analysis/Visulaization***

    Tweets Time Series Analysis

***Sentiment Analysis***

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
