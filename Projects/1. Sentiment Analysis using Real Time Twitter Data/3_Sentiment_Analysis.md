### Sentiment Analysis

 a) Clean tweets - using regular expressions (Regex): any symbol distinct to alphanumeric value will be remapped into new onw that satisfy the condition

 b) Analyze sentiment - create a classifier to check the polarity of tweet (-1,0,1) 
 
* ***Defining functions to clean tweet and analyze sentiment***

  ```javascript
      def clean_tweet(tweet):
          return ' '.join(re.sub("(@[A-Za-z0-9]+)|([^0-9A-Za-z \t])|(\w+:\/\/\S+)", " ", tweet).split())

      def analize_sentiment(tweet):
          analysis = TextBlob(clean_tweet(tweet))
          if analysis.sentiment.polarity > 0:
              return 1
          elif analysis.sentiment.polarity == 0:
              return 0
          else:
              return -1
  ```

* ***Adding new column to dataframe for sentiment analysis***

  ```javascript
      data1['SA'] = np.array([ analize_sentiment(tweet) for tweet in data1['Tweets'] ])
      data2['SA'] = np.array([ analize_sentiment(tweet) for tweet in data2['Tweets'] ])
      data3['SA'] = np.array([ analize_sentiment(tweet) for tweet in data3['Tweets'] ])
      data4['SA'] = np.array([ analize_sentiment(tweet) for tweet in data4['Tweets'] ])
      data5['SA'] = np.array([ analize_sentiment(tweet) for tweet in data5['Tweets'] ])
      data6['SA'] = np.array([ analize_sentiment(tweet) for tweet in data6['Tweets'] ])
      data7['SA'] = np.array([ analize_sentiment(tweet) for tweet in data7['Tweets'] ])
  ```
  
  # Let us check for Barack Obama
  ```javascript
      print('------------------------Tweet Data with Sentiment Analysis for Barack Obama-------------------------')
      display(data1.head(10))
  ```
  
  ```
  ------------------------Tweet Data with Sentiment Analysis for Barack Obama-------------------------
  
                             Tweets 	                        len 	            ID 	             Date                  	Source         Likes 	  RTs   SA
      0 	Congratulations to my friends, @JoeBiden and @... 	140 	1325136780396437507 	2020-11-07 18:03:22 	Twitter Web App 	1360501 169542 	0
      1 	Thank you Chiney, Nneka, and all of the athlet... 	140 	1323781320678531077 	2020-11-04 00:17:16 	Twitter Web App 	74702 	3807 	0
      2 	Rahul, you're helping make democracy work toda... 	83 	1323777143566934020 	2020-11-04 00:00:40 	Twitter Web App 	151106 	4595 	0
      3 	There's a reason some folks are trying to make... 	140 	1323770228191465472 	2020-11-03 23:33:11 	Twitter Web App 	72169 	7816 	-1
      4 	If you are in line to vote before polls close,... 	140 	1323770226555703296 	2020-11-03 23:33:11 	Twitter Web App 	83505 	16175 	1
      5 	This Election Day, everything is on the line. ... 	139 	1323726205993033728 	2020-11-03 20:38:15 	Twitter Media Studio 	206826 	24708 	0
      6 	RT @JoeBiden: Voting is your right. If you hav... 	140 	1323717453046796289 	2020-11-03 20:03:28 	Twitter for iPhone 	0 	8374 	1
      7 	This is it –– today is the last day to vote. I... 	120 	1323703138529009669 	2020-11-03 19:06:36 	Twitter Web App 	272518 	20846 	0
      8 	For eight years, Joe was the last one in the r... 	140 	1323687618526269442 	2020-11-03 18:04:55 	Twitter Web App 	257651 	31446 	1
      9 	More than 100 million Americans have already c... 	139 	1323626668842459136 	2020-11-03 14:02:44 	Twitter Media Studio 	102052 	12261 	1
  ```
  
* ***Assigning positive, neutral and negative tweets***

  ```javascript
      pos_tweets1 = [tweet for index, tweet in enumerate(data1['Tweets']) if data1['SA'][index] > 0]
      neu_tweets1 = [tweet for index, tweet in enumerate(data1['Tweets']) if data1['SA'][index] == 0]
      neg_tweets1 = [tweet for index, tweet in enumerate(data1['Tweets']) if data1['SA'][index] < 0]

      pos_tweets2 = [tweet for index, tweet in enumerate(data2['Tweets']) if data2['SA'][index] > 0]
      neu_tweets2 = [tweet for index, tweet in enumerate(data2['Tweets']) if data2['SA'][index] == 0]
      neg_tweets2 = [tweet for index, tweet in enumerate(data2['Tweets']) if data2['SA'][index] < 0]

      pos_tweets3 = [tweet for index, tweet in enumerate(data3['Tweets']) if data3['SA'][index] > 0]
      neu_tweets3 = [tweet for index, tweet in enumerate(data3['Tweets']) if data3['SA'][index] == 0]
      neg_tweets3 = [tweet for index, tweet in enumerate(data3['Tweets']) if data3['SA'][index] < 0]

      pos_tweets4 = [tweet for index, tweet in enumerate(data4['Tweets']) if data4['SA'][index] > 0]
      neu_tweets4 = [tweet for index, tweet in enumerate(data4['Tweets']) if data4['SA'][index] == 0]
      neg_tweets4 = [tweet for index, tweet in enumerate(data4['Tweets']) if data4['SA'][index] < 0]

      pos_tweets5 = [tweet for index, tweet in enumerate(data5['Tweets']) if data5['SA'][index] > 0]
      neu_tweets5 = [tweet for index, tweet in enumerate(data5['Tweets']) if data5['SA'][index] == 0]
      neg_tweets5 = [tweet for index, tweet in enumerate(data5['Tweets']) if data5['SA'][index] < 0]

      pos_tweets6 = [tweet for index, tweet in enumerate(data6['Tweets']) if data6['SA'][index] > 0]
      neu_tweets6 = [tweet for index, tweet in enumerate(data6['Tweets']) if data6['SA'][index] == 0]
      neg_tweets6 = [tweet for index, tweet in enumerate(data6['Tweets']) if data6['SA'][index] < 0]

      pos_tweets7 = [tweet for index, tweet in enumerate(data7['Tweets']) if data7['SA'][index] > 0]
      neu_tweets7 = [tweet for index, tweet in enumerate(data7['Tweets']) if data7['SA'][index] == 0]
      neg_tweets7 = [tweet for index, tweet in enumerate(data7['Tweets']) if data7['SA'][index] < 0]
  ```
  
* ***Percentage of positive, negative and neutral tweets with the bar plot***

  ```javascript
      pt1=len(pos_tweets1)*100/len(data1['Tweets'])
      net1=len(neu_tweets1)*100/len(data1['Tweets'])
      neg1=len(neg_tweets1)*100/len(data1['Tweets'])

      pt2=len(pos_tweets2)*100/len(data2['Tweets'])
      net2=len(neu_tweets2)*100/len(data2['Tweets'])
      neg2=len(neg_tweets2)*100/len(data2['Tweets'])

      pt3=len(pos_tweets3)*100/len(data3['Tweets'])
      net3=len(neu_tweets3)*100/len(data3['Tweets'])
      neg3=len(neg_tweets3)*100/len(data3['Tweets'])

      pt4=len(pos_tweets4)*100/len(data4['Tweets'])
      net4=len(neu_tweets4)*100/len(data4['Tweets'])
      neg4=len(neg_tweets4)*100/len(data4['Tweets'])

      pt5=len(pos_tweets5)*100/len(data5['Tweets'])
      net5=len(neu_tweets5)*100/len(data5['Tweets'])
      neg5=len(neg_tweets5)*100/len(data5['Tweets'])

      pt6=len(pos_tweets6)*100/len(data6['Tweets'])
      net6=len(neu_tweets6)*100/len(data6['Tweets'])
      neg6=len(neg_tweets6)*100/len(data6['Tweets'])

      pt7=len(pos_tweets7)*100/len(data7['Tweets'])
      net7=len(neu_tweets7)*100/len(data7['Tweets'])
      neg7=len(neg_tweets7)*100/len(data7['Tweets'])

      data_sentiment_analysis=[[pt1,pt2,pt3,pt4,pt5,pt6,pt7],
            [net1,net2,net3,net4,net5,net6,net7],
            [neg1,neg2,neg3,neg4,neg5,neg6,neg7]]


      X = np.arange(7)
      fig = plt.figure(figsize=(15,8))
      rects1= plt.bar(X + 0.00, data_sentiment_analysis[0], color = 'b', width = 0.25,label='Positive')
      rects2= plt.bar(X + 0.25, data_sentiment_analysis[1], color = 'g', width = 0.25,label='Neutral')
      rects3= plt.bar(X + 0.50, data_sentiment_analysis[2], color = 'r', width = 0.25,label='Negative')
      plt.xticks(X,('Barack Obama','Justin Bieber','Cristiano Ronaldo','Donald Trump','Narendra Modi','CNN Breaking News','Twitter'))
      plt.xlabel('Twitter Most Followed Accounts')
      plt.ylabel('Sentiment Analysis of last 200 Tweets (%)')
      plt.grid()

      def autolabel(rects):
          for rect in rects:
              height = rect.get_height()
              plt.annotate('{0:.2f} %'.format(height),
                          xy=(rect.get_x() + rect.get_width() / 2, height),
                          xytext=(0, 3),  # 3 points vertical offset
                          textcoords="offset points",
                          ha='center', va='bottom')

      autolabel(rects1)
      autolabel(rects2)
      autolabel(rects3)

      plt.xticks(rotation=45)
      plt.legend()
  ```
  
<p align="center">
  <img width=800" alt="java 8 and prio java 8  array review example" img align="center" src ="https://github.com/worklifesg/Natural-Language-Processing/blob/main/images/EDA7.png">
</p>

* Conclusion

  * It is observed that Barack Obama has highest number of followers on Twitter even though he is not current US President but due to his positive tweets towards everyone on different issues (60%).
  * On other side, musician and sports people are always in controversy and have split tweets between positive and neutral tweets.
  * Politician like Narendra Modi plays safe as by giving neutral tweets and is very cautious about his image in public and has negative tweets even less than twitter itself.
  * While comparing Donald Trump with other political leaders, he seems to be open about various issues and tends to be on negative side and playing bit safe with 50% neutral tweets.
  * As predicted news channel tend to give negative news a lot, CNN breaking News leads at the top of having 20% negative tweets.
