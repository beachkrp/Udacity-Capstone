# Udacity-Capstone
Udacity Capstone Project






#Motivation
Capstone Project for Udacity Data Science Nano Degree

#Included files
This READme file
The Notebook for this project.


#Problem Statement

Sparkify is a music streaming service.  The problem is to identify subscribers from the access logs of the service so that subscribers who are likely to churn would be convinced to remain with the service. 

The access logs provide information on the time and the individual songs that the user has accessed.  

It is expected to be able to use the information from the logs to find patterns in a user's usage of the service 


#Metics

An _authorization_ field with a valued of "Cancelled" is used when a user cancels the service. When this is present in the logs for that user, that user is considered to have "churned"

Because of the small number of churned customers it has been suggested that the F1 score be used.  

**However**,  the MLLIB library for evaluation has a glitch where, while a method for  precision, recall and F1 score exist,  they all return the accuracy of the model.  Therefore is is not possible to print out directly from the library these metrics.This glitch, or bug,  has been in place for at least two years, but has to date not been fixed. 

The MultiClassEvaluator used for a Grid Search uses the F1 score as the default measure for tuning the best model. At this point, the models, which all have the best F1 scores for thier category, can be inspected and compared, even if they cannot be done automatically without addition coding, if a "visual inspection" does not provide clear results.



# Implementation

  Pyspark was used for this implementation, using the Spark ML library and using the Spark MLLIB library for evaluation.


#Approach

 In other for the data to be used in machine learning algorithms, the logs were aggregated to fields to calculate the average usage for each user in terms of average number of songs accessed per day and per month and the average number time per day and per month that music is listened to by each user.

Furthermore, to explore if a geographical region would have any relation to the popularity of the service, the state portion of the users' locations was also used as a feature.


Becuase the TrainEvaluationSplit object of the ML library creates its own validation set, there is no need to split the test set into a test and validation set.   However, the dataset then was tested for tuned model using Logistic Regrssion, Naive Bayes, Random Forest and Gradient Boosted Trees, so the test set was split into two sets to be able to choose with algorithm to be chosen for the final model

#Caveats

As the platform used for this implementation was the Classroom Workspace,  only a small subset of the full data was used. 

The data used only carried three months of user logs.   

As a user could register for the service or cancel the service in the middle of any month,  monthly averages could be prone to data skew.   With a smaller dataset such as the one used here, this could give misleading results. 



#Results
 

Not only did the Naive Bayes model provide the highest accuracy (which is in fact a poor measure to be used), none of the other models were able to identify a higher number of users who had canceled the service, or a higher number of users who had not canceled the service. 
This means that the Naive Bayes model would not only have the highest accuracy, but also have the highest precision, recall and F1 score.

Also, Naive Bayes returned the highest Validation Metric of any of the models. 

Thus this was chosen for the final model.

However, the final deployed model also failed in identifying a single user who cancelled. 



 	
#Improvements

The small size of the dataset, which only represents three months of data,  would obviously skew the results becuase of the same sample size. 

Also, much larger parameter grids could be used, testing a larger number of models would likely give a more trustworthy model as well

Deploying this model on a Cloud service would would allow for the use of a larger dataset which would be expected to give more trustworthy results.

A much more streamilined approach for calculating the aggregated columns for the final model could be found.

No actual music content was used in this implementation. This is because of the large number of expected songs that would be available would make it unwieldy for a machine learning model. 
Unfortunately, the logs do not specify artists or genres, which might have been used as a feature that could support an improved model.

Furthermore, because of the glitch in the MMLIB evaluations library, where all metrics are actually returned as accuracy, the F1, precision

#Refinements

Technically, the intial result was the results from the Logistic Regrssion Model.   Each subsequent model would be considered to be an attempt to refine the original Logistic Regression Model.

The final result was the choice of the Naive Bayes model, which gave, not just an improved accuracy over the test set but also a higher recall and precision, observed just by visual inspection of the confusion matrix.

However, an attempt to further refine the Naive Bayes model was done by retuning the model with an expanced grid.  

The final results of this expanded grid search gave the exact same results as the first attempt.



#Limitations

Unable to deploy on an AWS cloud service because in a matter of three days, the maximum allowable s3 requests on the Free Tier had been exhausted for the month of August and the project was due before that date, therefore on the mini-subet was used. 

Due to time constraints, the various Parameter grids were not as extensive as I would have liked to explore. 

#Other sources

https://medium.com/@kevinpearson_20937/identifying-churn-candidates-541a77d0a56


#Acknowledgements. 

Much code from this Udacity course was referenced in this implementation

Also lectures and assignments from Udemy course on Scala and Pyspark from Pierian Data was used to verify usage of code

Also, Susan Li of Towards Data Science  https://towardsdatascience.com/multi-class-text-classification-with-pyspark-7d78d022ed35
was also used to verify proper usage of code. 