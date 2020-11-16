### Data Cleaning & Structuring

* ***Saving tweets in DataFrame for all 7 personalities***

  We will create a pandas dataframe as follows:
  ```javascript
      data1 = pd.DataFrame(data=[tweet.text for tweet in tweets_obama], 
                     columns=['Tweets'])
      data2 = pd.DataFrame(data=[tweet.text for tweet in tweets_bieber], 
                           columns=['Tweets'])
      data3 = pd.DataFrame(data=[tweet.text for tweet in tweets_ronaldo], 
                           columns=['Tweets'])
      data4 = pd.DataFrame(data=[tweet.text for tweet in tweets_Trump], 
                           columns=['Tweets'])
      data5 = pd.DataFrame(data=[tweet.text for tweet in tweets_modi], 
                           columns=['Tweets'])
      data6 = pd.DataFrame(data=[tweet.text for tweet in tweets_cnn], 
                           columns=['Tweets'])
      data7 = pd.DataFrame(data=[tweet.text for tweet in tweets_twitter], 
                           columns=['Tweets'])
  ```
  
  To check one of the dataframe, let us check Barack Obama dataframe and its internal methods.
  
  ```javascript
      display(data1.head(10))
      print(dir(tweets_obama[0]))
  ```
  
  ```
                      Tweets
            0 	Congratulations to my friends, @JoeBiden and @...
            1 	Thank you Chiney, Nneka, and all of the athlet...
            2 	Rahul, you're helping make democracy work toda...
            3 	There's a reason some folks are trying to make...
            4 	If you are in line to vote before polls close,...
            5 	This Election Day, everything is on the line. ...
            6 	RT @JoeBiden: Voting is your right. If you hav...
            7 	This is it –– today is the last day to vote. I...
            8 	For eight years, Joe was the last one in the r...
            9 	More than 100 million Americans have already c...

            ['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', '_api', '_json', 'author', 'contributors', 'coordinates', 'created_at', 'destroy', 'entities', 'favorite', 'favorite_count', 'favorited', 'geo', 'id', 'id_str', 'in_reply_to_screen_name', 'in_reply_to_status_id', 'in_reply_to_status_id_str', 'in_reply_to_user_id', 'in_reply_to_user_id_str', 'is_quote_status', 'lang', 'parse', 'parse_list', 'place', 'possibly_sensitive', 'retweet', 'retweet_count', 'retweeted', 'retweets', 'source', 'source_url', 'text', 'truncated', 'user']

  ```
  
* ***What other information can we fetch from our API ?***

  Checking for Obama only here (same can be applied for other 6 personalities)
  ```javascript
      print(tweets_obama[0].id) #ID number
      print(tweets_obama[0].created_at) #Tweet Creation
      print(tweets_obama[0].source) #Source from where tweet was created
      print(tweets_obama[0].favorite_count) # Likes
      print(tweets_obama[0].retweet_count) #RT
      print(tweets_obama[0].geo) #Geolocation
      print(tweets_obama[0].coordinates) #Cordinates of geolocation
      print(tweets_obama[0].entities) #internal methods
  ```  
  
  ```
        1325136780396437507
        2020-11-07 18:03:22
        Twitter Web App
        1360501
        169542
        None
        None
        {'hashtags': [], 'symbols': [], 'user_mentions': [{'screen_name': 'JoeBiden', 'name': 'Joe Biden', 'id': 939091, 'id_str': '939091', 'indices': [31, 40]}, {'screen_name': 'KamalaHarris', 'name': 'Kamala Harris', 'id': 30354991, 'id_str': '30354991', 'indices': [45, 58]}], 'urls': [{'url': 'https://t.co/ln4G2r6804', 'expanded_url': 'https://twitter.com/i/web/status/1325136780396437507', 'display_url': 'twitter.com/i/web/status/1…', 'indices': [117, 140]}]}
  ```
  
* ***Adding relevant data from data extraction into our dataframe***

  Adding for Barack Obama only here (for others please check the whole code) 
  ```javascript
      data1['len']  = np.array([len(tweet.text) for tweet in tweets_obama])
      data1['ID']   = np.array([tweet.id for tweet in tweets_obama])
      data1['Date'] = np.array([tweet.created_at for tweet in tweets_obama])
      data1['Source'] = np.array([tweet.source for tweet in tweets_obama])
      data1['Likes']  = np.array([tweet.favorite_count for tweet in tweets_obama])
      data1['RTs']    = np.array([tweet.retweet_count for tweet in tweets_obama])
      
      print('-----------------------------------------Tweet Data for Barack Obama-------------------------------------------')
      display(data1.head(10))
  ```  
  
  ```
        -----------------------------------------Tweet Data for Barack Obama-------------------------------------------

                                Tweets 	                                len 	        ID 	                  Date 	            Source 	        Likes 	    RTs
          0 	Congratulations to my friends, @JoeBiden and @... 	140 	1325136780396437507 	2020-11-07 18:03:22 	Twitter Web App 	1360501 169542
          1 	Thank you Chiney, Nneka, and all of the athlet... 	140 	1323781320678531077 	2020-11-04 00:17:16 	Twitter Web App 	74702 	3807
          2 	Rahul, you're helping make democracy work toda... 	83 	1323777143566934020 	2020-11-04 00:00:40 	Twitter Web App 	151106 	4595
          3 	There's a reason some folks are trying to make... 	140 	1323770228191465472 	2020-11-03 23:33:11 	Twitter Web App 	72169 	7816
          4 	If you are in line to vote before polls close,... 	140 	1323770226555703296 	2020-11-03 23:33:11 	Twitter Web App 	83505 	16175
          5 	This Election Day, everything is on the line. ... 	139 	1323726205993033728 	2020-11-03 20:38:15 	Twitter Media Studio 	206826 	24708
          6 	RT @JoeBiden: Voting is your right. If you hav... 	140 	1323717453046796289 	2020-11-03 20:03:28 	Twitter for iPhone 	0 	8374
          7 	This is it –– today is the last day to vote. I... 	120 	1323703138529009669 	2020-11-03 19:06:36 	Twitter Web App 	272518 	20846
          8 	For eight years, Joe was the last one in the r... 	140 	1323687618526269442 	2020-11-03 18:04:55 	Twitter Web App 	257651 	31446
          9 	More than 100 million Americans have already c... 	139 	1323626668842459136 	2020-11-03 14:02:44 	Twitter Media Studio 	102052 	12261
  ```
