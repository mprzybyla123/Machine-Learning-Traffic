# Machine-Learning-Traffic

## Classification of Single or Multi fatality accidents

**We will attempt to classify accidents as single-fatality or multiple-fatality accidents**

Using logistic regression, K-nearest neighbor, and Gaussian and Bernoulli Naive Bayes models we will attempt to classify the accidents in our dataset as to whether they result in single or multiple fatalities.  For each of these models, a grid search will be used to assist in determining the most useful combination of parameters.  Model parameters are adjusted during the grid search using the **accuracy** measurement.

The intended metrics which we will use to compare models are **accuracy, precision, and recall**. Accuracy gives us a good measure of True Positives (i.e. a prediction of a single-fatality accident is indeed a single-fatality accident) and True Negatives (i.e. prediction of a multi-fatality accident is indeed a multi-fatality accident). However, accuracy ignores misclassification and as such is somewhat misleading in that it predicts single fatalities because our data is skewed that way. 

Precision penalizes the models for prediction of False Positives (i.e. prediction of a single-fatality accident when it is actually a multi-fatality accident) and good precision will lower the False Positive rate. Recall penalizes for predicting False Negatives (i.e. prediction of a multi-fatality accident when it is actually a single-fatality accident) and good recall will lower the false negatives.

Since the data is extremely skewed toward single-fatality accidents (29,816 single-fatality accidents as opposed to 2,350 multi-fatality accidents), a stratified shuffle split and 10-fold cross validation. is used with these models. The stratified split will help to ensure that all of our CV folds include a suficient number of multi-fatality accidents.
The best model appears to be the Gaussian NB model. While this model does not have quite as high accuracy (90.4% as compared to approximately 92.6% for KNN and logistic regression), the accuracy is still fairly close and, more importantly, Gaussian NB has the highest recall of any model. Due to the fact that our classification task is centered around the goal of saving human life, the ability to correctly identify relevant cases is a priority. Although the recall is only 0.11, it is still much higher than logistic regression's recall of 0.01 and KNN's of 0.005.

From a computational standpoint, the Logistic Regression model takes a while to run, and the KNN model is extremely computational intensive and time consuming. Even with a limited neighbor list, it required over 8 minutes to run. Another advantage to the GaussianNB is the speed at which it performs, and gives us another reason for choosing this model.

## Classification of Collision/No-collision accidents

**We will classify accidents into those that result in collisions or no collision**



The dataset includes information for several types of motor vehicle collisions, including head-on, sideswipe, rear-end and other types of collision. This information is listed for those accidents in the dataset for which "first harmful event" is listed as a collision between two or more motor vehicles. Those that do not have this event listed have a "0" for the MAN_COLL (manner of collision) variable. To reduce this information to a binary classifier, we retained all non-collision accidents as a "0" and combined each type of collision into a "1" in a new variable named *collision*.
 
Once again using logistic regression, K-nearest neighbor, and Gaussian and Bernoulli Naive Bayes models we will attempt to classify the accidents in our dataset as to whether each accident involved a collision with another vehicle.    
For each of these models, a grid search will be used to assist in determining the most useful combination of parameters.

When compared to the number of fatalities, this variable is not nearly as highly skewed: 19,881 (62%) accidents did not involve a collision with another motor vehicle while 12,285 (38%) did.

The logistic regression, KNN, and Bernoulli NB models have very similar accuracies at approximately 73, 74, and 72%, respectively. The Gaussian NB model has the poorest accuracy at only 69%. The KNN model has the highest precision although each model has very similar precision values.

The Bernoulli NB model has the highest recall by a long shot: 0.715 vs the next highest recall of 0.576. We will select the Bernoulli NB model as our best model because of the good accuracy and recall. Again, the ability to correctly identify relevant cases is a priority and gives more credibility to the Bernoulli NB model in this instance.

Again, from a computational standpoint, the Logistic Regression model takes awhile to run, and the KNN model is once again extremely computational intensive, again taking over 8 minutes to run. Both GaussianNB and BernoullNB are computationally friendly and make the BernoulliNB a good pick for our top model.
