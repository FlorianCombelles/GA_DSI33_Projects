# General Assembly - DSI 33
## Project 3 Web APIs & NLP
### DogAdvice and CatAdvice subreddits
 
 In week four we've learned about a few different classifiers. In week five we'll learn about webscraping, APIs, and Natural Language Processing (NLP). This project will put those skills to the test.

For project 3, your goal is two-fold:
1. Using [Pushshift's](https://github.com/pushshift/api) API, you'll collect posts from two subreddits of your choosing.
2. You'll then use NLP to train a classifier on which subreddit a given post came from. This is a binary classification problem.

###### Requirements

- Gather and prepare your data using the `requests` library.
- **Create and compare two models**. One of these must be a Naive Bayes classifier, however the other can be a classifier of your choosing: logistic regression, KNN, SVM, etc.
- A Jupyter Notebook with your analysis for a peer audience of data scientists.
- An executive summary of your results.
- A short presentation outlining your process and findings for a semi-technical audience.

**Pro Tip:** You can find a good example executive summary [here](https://www.proposify.biz/blog/executive-summary).


### Problem Statement and background

###### Problem Statement

During Covid 19, we have seen an increase in the number of new pet owners in Singapore.
These new inexperienced pet owners are facing a lack of ressources on how to care for their new pets.

This leads to them having to overrely on veterinarians and pet stores to provides information and respond to their queries.

This influx of inexperienced pets owners overly reliant on vets and pet store reduces their work efficiency and distract them from their main responsibilites


##### Background

We are working for a company called Pet Smart.

We are releasing a new mobile app that includes two features:
* A chat box where you can ask your cat or dog related question and get an answer from a team of experts.
* Articles that provides informations and tips on how to care for your pets.


### Data Acquisition

For this analysis, we will use the following datasets.

For this project, we will be scrapping [Reddit](https://www.reddit.com) and particularly two similar subreddits:
* [DogAdvice](https://www.reddit.com/r/DogAdvice/)
* [CatAdvice](https://www.reddit.com/r/CatAdvice/)

###### These two subreddits are a place where people can post and look for information/advice regarding their dogs and cats.

In order to acquire information from these two subreddits, we will be using the [Pushshift's](https://github.com/pushshift/api) API.

This API was designed to help provide enhanced functionality and search capabilities for searching Reddit comments and submissions.

It provides full functionality for searching Reddit data and also includes the capability of creating powerful data aggregations

### NLP 

We will use the following NLP techniques to transform our text:
* Remove Punctuations
* Tokenize text
* Remove stop words
* Stem / Lemmatize

### Modeling Process

We will be focusing mainly on three types of Naive Bayes models:
* Bernoulli Naive Bayes
* Multinomial Naive Bayes
* Gaussian Naive Bayes

We will also model Logistic Regressions, K-Nearest Neighbors and Random Forests.

In order to optimise the results of our models we will also make use of:
* Pipelines
* Hyperparameters Tuning

#### Conclusions of our modeling and recommendations

 After our extensive round of modelling and testing 3 different types of Count Vectorizers and 4 types of models, our best model is the Multinomial Naive Bayes using Count Vectorizer.

| Min ocurence 	| Max occurence 	| Max number of features 	| N-Gram Range       	|
|--------------	|---------------	|------------------------	|--------------------	|
|       2      	| 50% of corpus 	|          9000          	| Unigram and Bigram 	|


      Model        	| Data Vectorization 	| Cross Val Score 	| Train Score 	| Test Accuracy 	|    Recall    	|  Precision  	|     F1     	|     AUC     	|
|:-------------------:	|:------------------:	|:---------------:	|:-----------:	|:-------------:	|:------------:	|:-----------:	|:----------:	|-------------	|
| Multinomial NB      	| Count Vectorizer   	|      87.86%     	|    96.84%   	|     88.79%    	|    85.23%    	|    91.69%   	|   88.34%   	|     0.95    	|
