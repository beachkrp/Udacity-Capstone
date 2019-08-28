# Udacity-Capstone
Udacity Capstone Project



#Installation

#Motivation
Capstone Project for Udacity Data Science Nano Degree

#Problem Statement

Sparkify is a music streaming service.  The problem is to identify subscribers from the access logs of the service so that subscribers who are likely to churn would be convinced to remain with the service. 

#Metics

An _authorizaion_ field with a valued of "Cancelled" is used when a user cancels the service. When this is present in the logs for that user, that user is considered to have "churned"

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

The Naive Bayes model gives the best model among all the models and that is used for the final deployment
 	





#Limitations

Unable to deploy on an AWS cloud service because in a matter of three days, the maximum allowable s3 requests on the Free Tier had been exhausted for the month of August and the project was due before that date, therefore on the mini-subet was used. 

Due to time constraints, the various Parameter grids were not as extensive as I would have liked to explore. 



