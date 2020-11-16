### Data Engineering Analysis

* ***Import Libraries***

  In the first segment of the code, we will first import necessary libraries to implement this NLP program
  ```javascript
      import tweepy
      import pandas as pd
      import numpy as np

      import matplotlib.pyplot as plt
      import seaborn as sns

      from textblob import TextBlob
      import re

      from credentials import *
  ```

* ***Creating Twitter API and fetching live data*** 

  * Next step is connect to Twitter Real Time data through its API. First and foremost step is to create [Twitter developer account](https://developer.twitter.com/apps) by sending them request to use data for learning purpose as instructed in the [youtube video](https://www.youtube.com/watch?v=vlvtqp44xoQ)
  * Once Twitter developer account is created and approved, we can generate Authentication Tokens and we need four keys to access the data. Currently there are two versions of Twiiter API [v 1.1](https://developer.twitter.com/en/docs/twitter-api/v1) and [v2: Early Access](https://developer.twitter.com/en/docs/twitter-api/early-access)
    * API key
    * API key secret
    * Access Token
    * Access Token secret
  * For privacy issue, I have not shown my credentials here in the code
  
    ```javascript
      def tweet_api():
    
      auth = tweepy.OAuthHandler(CONSUMER_KEY,CONSUMER_SECRET)
      auth.set_access_token(ACCESS_TOKEN, ACCESS_SECRET)
    
      api = tweepy.API(auth)
      return api
      
      # To Consume:
      CONSUMER_KEY    = 'YOUR API KEY'
      CONSUMER_SECRET = 'YOUR API KEY SECRET'

      # To Access:
      ACCESS_TOKEN  = 'YOUR ACCESS TOKEN'
      ACCESS_SECRET = 'YOUR ACCESS TOKEN SECRET'
      
      # use twitter api
      result = tweet_api()
    ```

* ***Tweet Extraction for all 7 personalities*** 

    ```javascript
    tweets_obama = result.user_timeline(screen_name="@BarackObama", count=200)
    tweets_bieber = result.user_timeline(screen_name="@justinbieber", count=200)
    tweets_ronaldo = result.user_timeline(screen_name="@Cristiano", count=200)
    tweets_Trump = result.user_timeline(screen_name="@realDonaldTrump", count=200)
    tweets_modi = result.user_timeline(screen_name="@narendramodi", count=200)
    tweets_cnn = result.user_timeline(screen_name="@cnnbrk", count=200)
    tweets_twitter = result.user_timeline(screen_name="@twitter ", count=200)
    
    print("Number of tweets for Barak Obama extracted are: {}.\n".format(len(tweets_obama)))
    print("Number of tweets for Justin Bieber extracted are: {}.\n".format(len(tweets_bieber)))
    print("Number of tweets for Cristiano Ronaldo extracted are: {}.\n".format(len(tweets_ronaldo)))
    print("Number of tweets for Donald Trump extracted are: {}.\n".format(len(tweets_Trump)))
    print("Number of tweets for Narendra Modi extracted are: {}.\n".format(len(tweets_modi)))
    print("Number of tweets for CNN Breaking News extracted are: {}.\n".format(len(tweets_cnn)))
    print("Number of tweets for Twitter extracted are: {}.\n".format(len(tweets_twitter)))
    ```
        
    ```
        Number of tweets for Barak Obama extracted are: 200.
        Number of tweets for Justin Bieber extracted are: 199.
        Number of tweets for Cristiano Ronaldo extracted are: 200.
        Number of tweets for Donald Trump extracted are: 200.
        Number of tweets for Narendra Modi extracted are: 200.
        Number of tweets for CNN Breaking News extracted are: 200.
        Number of tweets for Twitter extracted are: 200
    ```
    
* ***Tweet Read (Last 3 recent) for all 7 personalities*** 

    ```javascript
        print("3 recent tweets for Barack Obama:\n")
        for tweet in tweets_obama[:3]:
            print(tweet.text)
            print()
        print('------------------------------------------------------------------------------------------------------')

        print("3 recent tweets for Justin Bieber:\n")
        for tweet in tweets_bieber[:3]:
            print(tweet.text)
            print()
        print('------------------------------------------------------------------------------------------------------')

        print("3 recent tweets for Cristiano Ronaldo:\n")
        for tweet in tweets_ronaldo[:3]:
            print(tweet.text)
            print()
        print('------------------------------------------------------------------------------------------------------')

        print("3 recent tweets for Donald Trump:\n")
        for tweet in tweets_Trump[:3]:
            print(tweet.text)
            print()
        print('------------------------------------------------------------------------------------------------------')

        print("3 recent tweets for Narendra Modi:\n")
        for tweet in tweets_modi[:3]:
            print(tweet.text)
            print()
        print('------------------------------------------------------------------------------------------------------')

        print("3 recent tweets for CNN Breaking news:\n")
        for tweet in tweets_cnn[:3]:
            print(tweet.text)
            print()
        print('------------------------------------------------------------------------------------------------------')

        print("3 recent tweets for Twitter:\n")
        for tweet in tweets_twitter[:3]:
            print(tweet.text)
            print()
        print('------------------------------------------------------------------------------------------------------')
     ```
     
     ```
        3 recent tweets for Barack Obama:

        Congratulations to my friends, @JoeBiden and @KamalaHarris — our next President and Vice President of the United St… https://t.co/ln4G2r6804

        Thank you Chiney, Nneka, and all of the athletes who are using their platforms and helping people vote in this elec… https://t.co/f7QvXIqVK9

        Rahul, you're helping make democracy work today. Thank you. https://t.co/wOtcgc8zHh

        ------------------------------------------------------------------------------------------------------
        3 recent tweets for Justin Bieber:

        RT @Vevo: A laid-back version of "Holy" from @justinbieber and @chancetherapper to ease you into the weekend. 🙏
        ⠀⠀⠀⠀⠀⠀⠀⠀⠀
        ▶️ https://t.co/X…

        Mood remix @24kGoldn @JBALVIN @ianndior https://t.co/siedNLfJmk https://t.co/aBq59HTQc3

        Holy acoustic @chancetherapper https://t.co/nwMMrTbdZ5 https://t.co/iP0xaiXCSN

        ------------------------------------------------------------------------------------------------------
        3 recent tweets for Cristiano Ronaldo:

        Excited about this collaboration with @clear . A legend has been made. Can’t wait to share with all of you here 😎… https://t.co/AOGMHe8wh1

        Grande vittoria! Avanti cosi, tutti insieme!💪🏽👊🏽 #finoallafine https://t.co/JnliJkqCCu

        ❤️❤️❤️❤️❤️ https://t.co/wiByaOgL8Y

        ------------------------------------------------------------------------------------------------------
        3 recent tweets for Donald Trump:

        71,000,000 Legal Votes. The most EVER for a sitting President!

        THE OBSERVERS WERE NOT ALLOWED INTO THE COUNTING ROOMS. I WON THE ELECTION, GOT 71,000,000 LEGAL VOTES. BAD THINGS… https://t.co/qGn3DXgDbb

        I WON THIS ELECTION, BY A LOT!

        ------------------------------------------------------------------------------------------------------
        3 recent tweets for Narendra Modi:

        भाजपा को जन-जन तक पहुंचाने के साथ देश के विकास में अहम भूमिका निभाने वाले श्रद्धेय श्री लालकृष्ण आडवाणी जी को जन्म… https://t.co/saXZtTeQlU

        Heartiest congratulations @KamalaHarris! Your success is pathbreaking, and a matter of immense pride not just for y… https://t.co/M8XOUNBmpk

        Congratulations @JoeBiden on your spectacular victory! As the VP, your contribution to strengthening Indo-US relati… https://t.co/TGfktQ3kuH

        ------------------------------------------------------------------------------------------------------
        3 recent tweets for CNN Breaking news:

        RT @CNNPolitics: President-elect Joe Biden delivers remarks to the nation: "I pledge to be a president who seeks not to divide but unify. W…

        Vice President-elect Kamala Harris invoked the late Rep. John Lewis in a speech to the nation, saying "democracy wa… https://t.co/YaRwnYdQSx

        Live: President-elect Joe Biden and Vice President-elect Kamala Harris address Americans for the first time since b… https://t.co/0Ch9KeJuBz

        ------------------------------------------------------------------------------------------------------
        3 recent tweets for Twitter:

        breathe

        @sexyvamplre apology accepted

        @DaReal2ET H2🌑

        ------------------------------------------------------------------------------------------------------
     ```

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

***[<------------- Project Description](https://github.com/worklifesg/Natural-Language-Processing/blob/main/Projects/1.%20Sentiment%20Analysis%20using%20Real%20Time%20Twitter%20Data/Readme.md) ------------------------------------------------------------- [Data Cleaning & Structuring ------------->](https://github.com/worklifesg/Natural-Language-Processing/blob/main/Projects/1.%20Sentiment%20Analysis%20using%20Real%20Time%20Twitter%20Data/0_Data_Engineering.md)***
