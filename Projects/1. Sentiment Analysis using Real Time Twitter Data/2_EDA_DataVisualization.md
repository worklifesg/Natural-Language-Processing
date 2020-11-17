### EDA & Data Visualization

Here we will analyze tweets as per certain criteria:

    Average Length of last 200 tweets
    Most liked and maximum times retweet
    Time Series Analysis of Likes and RT

* ***Average Length of last 200 tweets***

  ```javascript
      print('The average length of Barack Obama tweets among last 200 tweets are: {}'.format(np.mean(data1['len'])))
      print('-----------------------------------------------------------------------------------------')

      print('The average length of Justin Bieber tweets among last 200 tweets are: {}'.format(np.mean(data2['len'])))
      print('-----------------------------------------------------------------------------------------')

      print('The average length of Cristiano Ronaldo tweets among last 200 tweets are: {}'.format(np.mean(data3['len'])))
      print('-----------------------------------------------------------------------------------------')

      print('The average length of Donald Trump tweets among last 200 tweets are: {}'.format(np.mean(data4['len'])))
      print('-----------------------------------------------------------------------------------------')

      print('The average length of Narendra Modi tweets among last 200 tweets are: {}'.format(np.mean(data5['len'])))
      print('-----------------------------------------------------------------------------------------')

      print('The average length of CNN Breaking News tweets among last 200 tweets are: {}'.format(np.mean(data6['len'])))
      print('-----------------------------------------------------------------------------------------')

      print('The average length of Twitter tweets among last 200 tweets are: {}'.format(np.mean(data7['len'])))
      print('-----------------------------------------------------------------------------------------')

      plt.figure(figsize=(10,5))
      accounts=['Barack Obama','Justin Bieber','Cristiano Ronaldo','Donald Trump','Narendra Modi','CNN Breaking News','Twitter']
      lengths=[np.mean(data1['len']),np.mean(data2['len']),np.mean(data3['len']),np.mean(data4['len']),np.mean(data5['len']),
              np.mean(data6['len']),np.mean(data7['len'])]

      plt.bar(accounts,lengths,color=['black', 'red', 'green', 'blue', 'orange','purple','magenta']);
      plt.xticks(rotation=45);
      plt.xlabel('Twitter Most Followed Accounts')
      plt.ylabel('Average Length of Tweets (last 200 tweets)')
      plt.grid()
  ```
  
<p align="center">
  <img width="600" alt="java 8 and prio java 8  array review example" img align="center" src ="https://github.com/worklifesg/Natural-Language-Processing/blob/main/images/EDA1.png">
</p>

| So it is seen that top most followed person on Twitter (Barack Obama) use long Tweets (around 135 length) while others such as Narendra Modi and CNN using near to Barack Obama and are placed at 15 and 16 position respectively. However it is interesting that Justin Bieber (musician) doesn't need to tweet long length messages to gain his popularity (he is no. 2 on top followed list) |
| --- |

* ***Most liked tweets***

  ```javascript
      fav_max1 = np.max(data1['Likes'])
      fav_max2 = np.max(data2['Likes'])
      fav_max3 = np.max(data3['Likes'])
      fav_max4 = np.max(data4['Likes'])
      fav_max5 = np.max(data5['Likes'])
      fav_max6 = np.max(data6['Likes'])
      fav_max7 = np.max(data7['Likes'])

      print('The most Liked Tweet of Barack Obama among last 200 tweets are: {} with {} of likes '.format(data1['Tweets'][data1[data1.Likes == fav_max1].index[0]],fav_max1))
      print('-----------------------------------------------------------------------------------------')

      print('The most Liked Tweet of Justin Bieber among last 200 tweets are: {} with {} of likes '.format(data2['Tweets'][data2[data2.Likes == fav_max2].index[0]],fav_max2))
      print('-----------------------------------------------------------------------------------------')

      print('The most Liked Tweet of Cristiano Ronaldo among last 200 tweets are: {} with {} of likes '.format(data3['Tweets'][data3[data3.Likes == fav_max3].index[0]],fav_max3))
      print('-----------------------------------------------------------------------------------------')

      print('The most Liked Tweet of Donald Trump among last 200 tweets are: {} with {} of likes '.format(data1['Tweets'][data4[data4.Likes == fav_max4].index[0]],fav_max4))
      print('-----------------------------------------------------------------------------------------')

      print('The most Liked Tweet of Narendra Modi among last 200 tweets are: {} with {} of likes '.format(data1['Tweets'][data5[data5.Likes == fav_max5].index[0]],fav_max5))
      print('-----------------------------------------------------------------------------------------')

      print('The most Liked Tweet of CNN Breaking News among last 200 tweets are: {} with {} of likes '.format(data1['Tweets'][data6[data6.Likes == fav_max6].index[0]],fav_max6))
      print('-----------------------------------------------------------------------------------------')

      print('The most Liked Tweet of Twitter among last 200 tweets are: {} with {} of likes '.format(data1['Tweets'][data7[data7.Likes == fav_max7].index[0]],fav_max7))
      print('-----------------------------------------------------------------------------------------')

      plt.figure(figsize=(10,5))
      accounts=['Barack Obama','Justin Bieber','Cristiano Ronaldo','Donald Trump','Narendra Modi','CNN Breaking News','Twitter']
      lengths=[fav_max1,fav_max2,fav_max3,fav_max4,fav_max5,fav_max6,fav_max7]

      plt.bar(accounts,lengths,color=['black', 'red', 'green', 'blue', 'orange','purple','magenta']);
      plt.xticks(rotation=45);
      plt.xlabel('Twitter Most Followed Accounts')
      plt.ylabel('No. of Likes for the most Liked Tweet (last 200 tweets)')
      plt.grid()
  ```
  
<p align="center">
  <img width="600" alt="java 8 and prio java 8  array review example" img align="center" src ="https://github.com/worklifesg/Natural-Language-Processing/blob/main/images/EDA2.png">
</p>

|  Again Barack Obama has maximum likes due to maximum number of followers. It is coincidence that his tweet from today (7 November 2020) has the highest number of likes based on his commnets on US Elections Results. Due to his popularity on Twitter, Donald Trump was not able to win 2020 US Elections though his likes are second highest here. |
| --- |

* ***Time series analysis for most likes upto now***

  ```javascript
      likes1=pd.Series(data=data1['Likes'].values, index=data1['Date'])
      likes2=pd.Series(data=data2['Likes'].values, index=data2['Date'])
      likes3=pd.Series(data=data3['Likes'].values, index=data3['Date'])
      likes4=pd.Series(data=data4['Likes'].values, index=data4['Date'])
      likes5=pd.Series(data=data5['Likes'].values, index=data5['Date'])
      likes6=pd.Series(data=data6['Likes'].values, index=data6['Date'])
      likes7=pd.Series(data=data7['Likes'].values, index=data7['Date'])

      plt.figure(figsize=(20,5))

      plt.plot(likes1,color='black',label='Barack Obama');
      plt.plot(likes4,color='blue',label='Donald Trump');
      plt.xticks(rotation=45);
      plt.xlabel('Date (period of last 200 tweets)')
      plt.ylabel('No.of Likes (last 200 tweets)')
      plt.legend()
      plt.grid()

      plt.figure(figsize=(20,5))

      plt.plot(likes2,color='red',label='Justin Bieber');
      plt.plot(likes3,color='green',label='Cristiano Ronaldo');
      plt.plot(likes5,color='orange',label='Narendra Modi');
      plt.plot(likes6,color='purple',label='CNN Breaking News');
      plt.plot(likes7,color='magenta',label='Twitter');

      plt.xticks(rotation=45);
      plt.xlabel('Date (period of last 200 tweets)')
      plt.ylabel('No.of Likes (last 200 tweets)')
      plt.legend()
      plt.grid()
  ```
  
<p align="center">
  <img width="900" alt="java 8 and prio java 8  array review example" img align="center" src ="https://github.com/worklifesg/Natural-Language-Processing/blob/main/images/EDA3.png">
  <img width="900" alt="java 8 and prio java 8  array review example" img align="center" src ="https://github.com/worklifesg/Natural-Language-Processing/blob/main/images/EDA4.png">
</p>

* ***Time series analysis for most retweets upto now***

  ```javascript
      retweet1=pd.Series(data=data1['RTs'].values, index=data1['Date'])
      retweet2=pd.Series(data=data2['RTs'].values, index=data2['Date'])
      retweet3=pd.Series(data=data3['RTs'].values, index=data3['Date'])
      retweet4=pd.Series(data=data4['RTs'].values, index=data4['Date'])
      retweet5=pd.Series(data=data5['RTs'].values, index=data5['Date'])
      retweet6=pd.Series(data=data6['RTs'].values, index=data6['Date'])
      retweet7=pd.Series(data=data7['RTs'].values, index=data7['Date'])

      plt.figure(figsize=(20,5))

      plt.plot(retweet1,color='black',label='Barack Obama');
      plt.plot(retweet4,color='blue',label='Donald Trump');
      plt.xticks(rotation=45);
      plt.xlabel('Date (period of last 200 tweets)')
      plt.ylabel('No.of Retweets (last 200 tweets)')
      plt.legend()
      plt.grid()

      plt.figure(figsize=(20,5))

      plt.plot(retweet2,color='red',label='Justin Bieber');
      plt.plot(retweet3,color='green',label='Cristiano Ronaldo');
      plt.plot(retweet5,color='orange',label='Narendra Modi');
      plt.plot(retweet6,color='purple',label='CNN Breaking News');
      plt.plot(retweet7,color='magenta',label='Twitter');

      plt.xticks(rotation=45);
      plt.xlabel('Date (period of last 200 tweets)')
      plt.ylabel('No.of Retweets (last 200 tweets)')
      plt.legend()
      plt.grid()
  ```
  
<p align="center">
  <img width="900" alt="java 8 and prio java 8  array review example" img align="center" src ="https://github.com/worklifesg/Natural-Language-Processing/blob/main/images/EDA5.png">
  <img width="900" alt="java 8 and prio java 8  array review example" img align="center" src ="https://github.com/worklifesg/Natural-Language-Processing/blob/main/images/EDA6.png">
</p>

This is an interesting observation as their daily tweet acitivity on Twitter (based on today 7 Nov 2020):

    Barack Obama - His last 200 Tweets came in last 5 months and yet he had highest number of likes on one tweet due to his top followed twitter personality.
    Justin Bieber - very active among his followers with low likes but still covering 200 tweets in last 5 months
    Cristiano Ronaldo - Not much active on Twitter , last 200 tweets in last 1 year 5 months but has better liked tweets besides Obama
    Donald Trump - Due to US Elections Trump has done 200 tweets in last 6 days and has gained very high number of likes but couldn't make it impactful in the elections unfortunately.
    Narendra Modi - Very much active on Twitter with 200 tweets in last 3-4 weeks with lower number of liked tweets as compared to his contemporary candidates.
    CNN Breaking News - News Channel covered its 200 tweets in last 2-3 weeks but however was not much impactful as compared to its followers.
    Twitter - Social Media Platform - going with its normal pace speed and covered 200 tweets in last 3.5 months with good amouint of liked tweets

Similar trend for retweets as well
