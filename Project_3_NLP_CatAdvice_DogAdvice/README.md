# General Assembly - DSI 33
## Project 2 - Machine Learning and Regression Models
### Ames Housing Data and Kaggle Challenge
 
 This second project make use of:
 * Basic statistics and probability
 * Python programming concepts
 * EDA
 * Visualizations
 * Machine Learning and Regression Modeling (Linear Regression, Lasso, Ridge)
 * Working with Jupyter notebooks for development and reporting

For this second project, we are going to work with the Ames Housing dataset.
It is an exceptionally detailed and robust dataset with over 70 columns of different features relating to houses in the town of Ames Iowa.


### Problem Statement

We are part of the data team of a real estate agency based in Ames area. The objective of our company is to provide the most accurate sale price to clients who are looking to sell their houses. We also provide counseling on how to optimise sale price based on different features.


The housing and real estate market is getting more competitive and we're loosing the edge we once had to our competitor. Our current machine learning model is not accurate enough to keep up with the competition.
We need to find a better model to regain the advantage.


### Datasets

For this analysis, we will use the following datasets.


* [`train.csv`]: Dataset used to generate and refine model
* [`test.csv`]: Dataset used to predict the sale price of houses based on the train dataset


### Data Dictionary

Data dictionary is available [here](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)


### Modeling Process

Using the information stored in the [`train.csv`] dataset, we will generate our regression model and make use of:
    - train-test split
    - cross-validation / grid searching for hyperparameters
    - strong exploratory data analysis to question correlation and relationship across predictive variables
    - code that reproducibly and consistently applies feature transformation (such as the preprocessing library)

Once these steps are done we will use the [`test.csv`] dataset we will:
    - predict the values of target SalePrice column
    - transform our data to fit required csv format
    - upload our results to Kaggle challenge to see how model does against unseen data
    
Throughout each steps, we will need to evaluate our models and consider the following:
    - what evaluation metrics to use
    - our baseline score and how our models compare to this model
    - how can our model be used for inference
    - why we believe our model will generalize to new data

#### Conclusions of our modeling and recommendations

Our baseline model had a margin of error of 80897$ when predicting sale price of houses.

Using our first model, we managed to bring down the margin of error to 30334$. 
However, for this first model we used a total 47 variables. This made our model quite complex and it could be hard to justify implementing it to stakeholders.
Also, since a lot of the variables were heavily penalised by our model, it wasn't running optimaly.

With this in mind, we reduced the number of variables making our new model simpler and easier to explain.
We also managed to improve the results of our model both in term of accuracy and margin of error.

Our final R2 value was 83.75% and the margin of error was 29854$.


Using this new model, our company will be able to regain it's edge on the market and be able to deploy the best property value predictor on the market.

Since our model is simple (6 variables), we can also recommend our clients which features to improve in order to maximise the sale price of their properties. 


###### Recommendations: 

We could think of expanding our model not only to Ames properties but also to nearby town in other to increase the reach of our services.
We would only need to get the sales history of neghboring towns and train our model on this new data.


We can also leverage on our sale price improvement feature to gain another edge on the market, not only accuratly predicting sale price but also helping our clients in maximising the value of their properties using our coefficients.

Finally, we can also targets properties in the neighborhoods with an higher average or median sale price and be more agressive on our marketing in these areas, as they would be the properties bringing us the highest commissions.


###### Limitations of our model

As every model, we will need to retrain our model every week to remain accurate and adapt to new trends in the market.

We also need to be mindful of the outliers in our model as the results can be heavily skewed by them

Also, we used a transformation of Nieghborhoods based on SalePrice wich can lead to some issues with real time predictions.
* Instead of using the median house price to rank neighborhood it would be better to be better to rank the neighborhood bu their level of amenities.
This is something we should be focusing to improve our model.
