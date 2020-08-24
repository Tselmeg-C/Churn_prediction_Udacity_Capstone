# Churn_prediction_Udacity_Capstone
Solved churn prediction problem on an event data set and exemplified big data handling skills with Spark on AWS

Churn prediction, namely predicting clients who might want to turn down the service, is one of the most common business applications of machine learning. It is especially important for those companies providing streaming services. In this project, an event data set from a fictionary music streaming company named Sparkify was analyzed. A tiny subset (128MB) of the full dataset (12GB) was first analyzed locally in Jupyter Notebook with a scalable script in Spark and the whole data set was analyzed on the AWS EMR cluster. 

Skills examplified on this project are: 
1. How to manipulate large and realistic datasets with Spark to engineer relevant features for predicting churn. 
2. how to use Spark MLlib to build machine learning models with large datasets

Three jupyter notebook files were uploaded:
Sparkify_visualization: Codes for cleaning small data set and exploratory visualization
Sparkify_modeling: Codes for cleaning small data set and modeling
Sparkify_AWS: Codes for analyzing big data set on AWS EMR cluster (not the exactly scaled codes from the other two parts)

AWS EMR setting:
On AWS, the full 12GB dataset was hosted on a public S3 bucket, and expect to use about $30 dollars or more (I spent around 50 :() to run this cluster while you build your project for a week with the following setting. 

