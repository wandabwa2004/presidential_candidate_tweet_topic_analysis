###Objective: 
Determine and assess the top prevalent issues regarding presidential candidates, by discovering topics and related words concerning the candidates given relevant tweets. 
###Solution: 
Perform Natural Language Processing (NLP) and Text Clustering on tweets about presidential candidates in Python.
###Methodology: 
LDA Topic Modeling, K-Means Clustering, and Google's Word2Vec
I extracted themes out of tweets concerning candidates: 
* Generated the 10 topics associated with tweets. These topics were generated by training topic models with Latent Dirichlet allocation (LDA) provided by the GraphLab Create library. 
* Generated 15 clusters of frequently occurring words embedded within tweets. These clusters were generated using the K-Means Clustering technique provided by the SciKit-Learn library. 

I assessed public opinions of presidential candidates by finding words associations embedded within tweets: 
* Generated word relationships within the context of tweets using Google's Word2Vec algorithms. 

####Source: 
I archicted a cloud-hosted database of tweets mentioning Hillary Clinton and Donald Trump.

##Natural Language Processing: Topic Modeling with Latent Dirichlet allocation 
I decided to take the NLP approach of Topic Modeling the tweets using LDA. My goal was to extract themes out of tweets about candidates by clustering words within tweets that frequently occur together and have similar meaning. I decide to use the GraphLab python module for LDA. 

###Step 1: Non-Relational Database Hosting  
* Hosted a NoSQL Database on a cloud machine to avoid storing large amounts of tweets on my local machine. 
* Installed a MongoDB on my Amazon Web Service's (AWS) EC2 server. 

###Step 2: Data Extraction 
* Wrote a python script that retrieves tweets using the Twitter API and creates database collections of tweets on my hosted MongoDB. 
* Utilized a python wrapper for the Twitter API called TwitterSearch, and inserted custom BSON objects of tweets into my database. 
* Connected to my MongoDB database containing tables of tweets concerning Hillary Clinton & Donald Trump
#### Database - MongoDB on AWS: election2016
    * hillary_tweets: 10001 tweets
    * trump_twees: 10001 tweets

###Step 3: Data Pre-Processing
* Converted collections of tweets to unigram, bigram, & trigram bag of words / document vector  
* Tokenized words in tweets, and stemmed similar words in tweets 
* Removed Stop/Irrelevant words

###Step 4: Data Modeling 
* Train/Test split documents for each collection 
* Trained all N_Grams Models for Hillary & Trump fitted with respective training sets

###Step 5: Results & Evaluation 
* Generated 10 topics for unigram fitted models. 
* Chose unigram fitted models because they were the most interpretable.
* Evaluated models using the perplexity metric. Perplexity is a measurement of how well a probability distribution or probability model predicts a sample (https://en.wikipedia.org/wiki/Perplexity).
* Result: My perplexities were higher than I would like them to be. I plan on lowering it before deployment.

###Step 6: Deployment: 
* Visualized results in D3.js via the [pyLDAvis](https://github.com/bmabey/pyLDAvis) Python wrapper

##Text Clustering: Topic Modeling with K-Mean Clustering

###Step 7: Clustered words from tweets with K-Means clustering 

##Word2Vec

###Step 8: Discovered word relations with Google's Word2Vec 

###Appendix:
####Topic Model
A topic model is a type of statistical model for discovering abstract "topics" occurring in a collection of text documents [[1]](https://en.wikipedia.org/wiki/Topic_model). A "topic" consists of a cluster of words that frequently occur together [[2]](http://mallet.cs.umass.edu/topics.php). These "topics" represent embedded thematic structures within unlabeled text documents [[2]](http://mallet.cs.umass.edu/topics.php) [[3]](https://www.cs.princeton.edu/~blei/topicmodeling.html). Using contextual clues, topic models can connect words with similar meaning, and distinguish between uses of words with multiple meanings [[3]](https://www.cs.princeton.edu/~blei/topicmodeling.html). Topic Modeling helps us develop new ways to search, browse, and summarize large archives of texts [[3]](https://www.cs.princeton.edu/~blei/topicmodeling.html).
####Latent Dirichlet allocation (LDA)
Latent Dirichlet allocation (LDA) is a generative model that allows sets of observations to be explained by unobservedgroups that explain why some parts of the data are similar [[4]](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation).
####Word2Vec
Word2vec is a group of algorithms that are shallow, two-layer neural networks that encode the context of words in a vector. Word2vec models map each word to a vector of hundreds of elements, which represent that word's relation to other words. (https://en.wikipedia.org/wiki/Word2vec#cite_note-mikolov-1)
