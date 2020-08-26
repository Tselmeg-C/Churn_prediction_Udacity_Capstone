# Churn_prediction_Udacity_Capstone
Solved churn prediction (classification) problem on an event data set and exemplified big data handling skills with Spark on AWS

## Project Discription

Churn prediction, namely predicting clients who might want to turn down the service, is one of the most common business applications of machine learning. It is especially important for those companies providing streaming services. In this project, an event data set from a fictionary music streaming company named Sparkify was analyzed. A tiny subset (128MB) of the full dataset (12GB) was first analyzed locally in Jupyter Notebook with a scalable script in Spark and the whole data set was analyzed on the AWS EMR cluster. 

## Skills examplified
1. How to manipulate large and realistic datasets with Spark to engineer relevant features for predicting churn. 
2. how to use Spark MLlib to build machine learning models with large datasets

## File Descriptions
1. **_Sparkify_visualization_**: Codes for cleaning small data set and exploratory visualization
2. **_Sparkify_modeling_**: Codes for cleaning small data set and modeling
3. **_Sparkify_AWS_**: Codes for analyzing big data set on AWS EMR cluster (Because of limited time and budget, I only run this version of code once on AWS cluster. This is not the exactly scaled codes from the other two parts. However, the other two notebooks should be completely scalable on big data set) 

## AWS EMR Setting Instruction

On AWS, the full 12GB dataset was hosted on a public S3 bucket, follow the instructions below to launch a EMR cluster and notebook. It was expect to use about $30 dollars or more to run this cluster for a week with the following setting.

* Full Sparkify Dataset: *s3n://udacity-dsnd/sparkify/sparkify_event_data.json*
* Mini Sparkify Dataset: *s3n://udacity-dsnd/sparkify/mini_sparkify_event_data.json*

**Launch EMR Cluster and Notebook

* Open a regular AWS account (if you don't already have one) following the instructions via the [Amazon Web Service Help Center](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/)
* Go to the [Amazon EMR Console](https://signin.aws.amazon.com/signin?redirect_uri=https%3A%2F%2Fconsole.aws.amazon.com%2Felasticmapreduce%2Fhome%3Fstate%3DhashArgs%2523%26isauthcode%3Dtrue&client_id=arn%3Aaws%3Aiam%3A%3A015428540659%3Auser%2Femr&forceMobileApp=0&code_challenge=eP2O9hqlLWWxfs_97cQ_W-0F5Bccl4DFS9PDSR4Rptg&code_challenge_method=SHA-256)
* Select "Clusters" in the menu on the left, and click the "Create cluster" button.

![Image of AWS](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/amazon-emr.png)

**Step 1: Configure your cluster with the following settings:**

* Release: *emr-5.20.0* or later
* Applications: *Spark*: Spark 2.4.0 on Hadoop 2.8.5 YARN with Ganglia 3.7.2 and Zeppelin 0.8.0
* Instance type: *m3.xlarge*
* Number of instance: 3
* EC2 key pair: Proceed without an EC2 key pair or feel free to use one if you'd like
* You can keep the remaining default setting and click "Create cluster" on the bottom right.

![create cluster](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/configure-cluster.png)

**Step 2: Wait for Cluster "Waiting" Status**

Once you create the cluster, you'll see a status next to your cluster name that says Starting. Wait a short time for this status to change to Waiting before moving on to the next step.
![cluster waiting](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/cluster-waiting.png)

**Step 3: Create Notebook**

Now that you launched your cluster successfully, let's create a notebook to run Spark on that cluster.

Select "Notebooks" in the menu on the left, and click the "Create notebook" button.
![create notebook](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/create-notebook-button.png)

**Step 4: Configure your notebook**

* Enter a name for your notebook
* Select "Choose an existing cluster" and choose the cluster you just created
* Use the default setting for "AWS service role" - this should be "EMR_Notebooks_DefaultRole" or "Create default role" if you haven't done this before.

You can keep the remaining default settings and click "Create notebook" on the bottom right.

![configur notebook](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/configure-notebook.png)

**Step 5: Wait for Notebook "Ready" Status, Then Open**

Once you create an EMR notebook, you'll need to wait a short time before the notebook status changes from Starting or Pending to Ready. Once your notebook status is Ready, click the "Open" button to open the notebook.

![open notebook](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/notebook-ready.png)

**Start Coding!**

Now you can run Spark code for your project in this notebook, which EMR will run on your cluster. 

![empty notebook](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/empty-notebook.png)

For more information on EMR notebooks, click [here](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-managed-notebooks.html).

**For those who want to challenge yourselves, you could start with the starter code instead of referring to my code**

![start code](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/spark-notebook-1.png)

When you run the last cell, you'll see a box appear that says "Spark Job Progress." Click on the arrow in that box to view your cluster's progress as it reads the full 12GB dataset! 

![notebook 2](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/spark-notebook-2.png)

![notebook 3](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/spark-notebook-3.png)

## Analysis of Mini Data Set

#### Code Structure
1. Import libraries
2. Instantiate a Spark session
3. Load and Clean Dataset
4. Exploratory Data Analysis (separately done in Sparkify_visualization)
5. Feature Engineering
6. Modeling
7. Conclusion
8. Discussion

#### Libraries
* Pyspark
* Pyspark.sql
* Pyspark.ml 
* Numpy
* Pandas
* Seaborn
* Matplotlib

#### Data Cleaning
* Missing values or empty strings handling
* Simplifying categorical variables *location* and *userAgent*
* Transformation of timestamps to epoch time

#### Exploration of Dataset
* Churn and downgrade definition
* Visualization of behavior for users who stayed VS users who churned

#### Feature Engineering
* Assembling features
* Transforming categorical variables
* Scaling features
* Transforming to vector

#### Modeling
* Models: Logistic regression, random forest, gradient-boosted tree
* Evaluator: Binary, Multiclass
* Metrics: F1 and AUC
* Hyperparameter tuning
* Cross-validation
* Check feature importances

#### Conclusion

In this project, churn prediction was performed based on an event data set for a music streaming provider. This was basically a binary classification problem. After loading and cleaning data, I performed some exploratory analysis and provided insights on the next step of feature engineering. All together 13 explanatory features were selected and logistic regression, random forest, and gradient-boosted tree models were fitted respectively to a training data set.

The model performance was the best for the logistic regression on small data set, with an F1 score of 73.10 on the test set. The other two models were both suffered from overfitting. Hyperparameter tuning and cross-validation was not very helpful in solving overfitting, probably because of a small number of sample size. Due to time and budget limitations, the final models were not tested on the big data set. However, the completely scalable process shed a light on solving the churn prediction problem on big data with Spark on Cloud.


#### Future work

**Finer feature engineering**

Feature engineering was one of the most important steps on this project, due to the trade-off between model performance and calculation capacity, it was impossible and unnecessary to select as many features as I wanted. Fewer features were tested on the full data set, as a result, the model performance was not satisfying, that's why I created more features and tested on the small data set. Although there was an improvement in the model performance, it was probably not the ideal result. There are some techniques that might help in the feature selection process. For example, the ChiSqSelector provided by Spark ML for selecting significant features.

**Build balanced training set**

Imbalanced samples (with more "0" labeled rows than "1") was another factor that holding back our model performance. Introducing weight balance was only possible for the logistic regression algorithm. In future work, we could randomly select the same number of "0" rows to "1" rows to create balanced training data and fit models, which might improve the model performances. 


## Acknowledgment

This is my capstone project on Udacity Data Scientist Nanodegree program. Thanks to Udacity for providing such a wonderful program, making it possible for many with different backgrounds to step into the field of data science. 


