# Twitter-Sentiment-Analysis
Sentiment analysis and EDA on twitter (tweets) dataset 


In this code I'll be using Twitter dataset (uploaded in the reposistory) for sentiment analysis. Few modules like, wordcloud, count vectorizaton whose working will be briefly explained later in the text. 
Sentiment analysis, in general, is used to analyze and classify a certain text (or tweet in our case) as either offensive or non-offensive. This saves corporations a lot of time and effort that it would otherwise have taken to read and classify each comment/tweet. Let's dive into the steps of the code. 

1 . Firstly, even before the cleaning process, one should get familiar with the kind of data they'll be dealing with (also called as exploratory data analysis). This just helps in providing more context and background information to the data scientist. So After reading the csv file, I've run a few functions on the data just to familiarize with it. We get to know the size of the data, the data types of each column/feature, number of null entries, the distribution of different classes, average number of words in a tweet etc. It depends from question to question. We then realize that we wont be needing the id column in further analysis so we drop it. 

2. Another part of EDA in text/sentiment analysis could be to use the WordCloud, to get a big picture idea of the overall class distribution based on text. For it's implementation, we first join all to tweets to a single huge sentence. This sentence does not have to mean anything to us, but it does to WordCloud. It will take this gigantic sentence as its input and produce an output image (WordCLoud) that'll show the distribution of certain 'words' that have been used most frequently. The number of usages of a word or it's importance is directly proportional to it's size as seen on the WordCloud. From the wordcloud we infer that most of the words used in most of th tweets are generally "positive", which was expected as our dataset is imbalanced towards "positive" tweets. 

3. Next we move onto data cleaning. In sentiment analysis Data cleaning generally refers to removing the unnecessary punctuations as they hinder the proper working of the algorithm and also removing "Stopwords", which is a collection of words that are "neutral" and very common/ everyday use words, just so we can trim out the unnecessary characters the make our dataset too long to compute. 

4. After cleaning, We move onto a process called CountVectorization. Count Vectorization involves counting the number of occurrences each words that appears in a document/text (i.e distinct text such as an tweet,article, book, even a paragraph). Python’s Sci-kit learn library has a tool called CountVectorizer to accomplish this. This process helps in converting the text data as we understand it, to numerical data, that is easier for the computer to understand. For eg. we see that in the all the tweets combined we have 47385 distinct words. 

5. Now that we have our data in numerical form, it's time to implement algorithms on it. Here any powrful binary classification algorithm could be applied like logistic regression,SVM etc. I've applied Naive Bayes because it works well with large data as we have here. After fitting the model on our training data, and assessing it we see that our model gave an accuracy of 94% which is pretty good. But as we have already seen that our dataset was highly imbalanced, we cannot conclude that our model is effiecient. For that we look at the Precision and Recall (also tp and fp rates, although numerically tp rate is same as recall). For the 0 class (positive tweets class) we have pretty good precision, recall and F1score but for class 1 (negative tweets class) whose data samples are considerably less than Class 0 samples, our model didnt perform well. After all, our target is to corectly detect negative tweetsand report them not the positive tweets. To improve Precision and recall of class 1 we can try different classification algorithm, which I havn't shown in this code. Or we can also use PyCaret to implement multiple algorithms together and compare them. However all that is a topic for a different code
