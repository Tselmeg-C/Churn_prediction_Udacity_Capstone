# Churn_prediction_Udacity_Capstone
Solved churn prediction problem on an event data set and exemplified big data handling skills with Spark on AWS

Churn prediction, namely predicting clients who might want to turn down the service, is one of the most common business applications of machine learning. It is especially important for those companies providing streaming services. In this project, an event data set from a fictionary music streaming company named Sparkify was analyzed. A tiny subset (128MB) of the full dataset (12GB) was first analyzed locally in Jupyter Notebook with a scalable script in Spark and the whole data set was analyzed on the AWS EMR cluster. 

Skills examplified on this project are: 
1. How to manipulate large and realistic datasets with Spark to engineer relevant features for predicting churn. 
2. how to use Spark MLlib to build machine learning models with large datasets

Three jupyter notebook files were uploaded:
1. Sparkify_visualization: Codes for cleaning small data set and exploratory visualization
2. Sparkify_modeling: Codes for cleaning small data set and modeling
3. Sparkify_AWS: Codes for analyzing big data set on AWS EMR cluster (not the exactly scaled codes from the other two parts)

AWS EMR setting:

On AWS, the full 12GB dataset was hosted on a public S3 bucket, and expect to use about $30 dollars or more to run this cluster while you build your project for a week with the following setting. 

Launch EMR Cluster and Notebook

Follow the instructions below to launch your EMR cluster and notebook.

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

Now you can run Spark code for your project in this notebook, which EMR will run on your cluster. In the next page, you'll find starter code to create a spark session and read in the full 12GB dataset for the DSND Capstone project.

![empty notebook](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/empty-notebook.png)

For more information on EMR notebooks, click [here](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-managed-notebooks.html).

**Pricing - Be Careful!**

From this point on, AWS will charge you for running your EMR cluster. 

**For those who want to challenge yourselves, you could start with the starter code instead of referring to my code**

**Starter Code**

Below, you'll find starter code to create a spark session and read in the full 12 GB dataset. You can use the following link to access the public dataset:

Full Sparkify Dataset: *s3n://udacity-dsnd/sparkify/sparkify_event_data.json*

You can also use the link below to access the mini 123MB dataset:

Mini Sparkify Dataset: *s3n://udacity-dsnd/sparkify/mini_sparkify_event_data.json*

![start code](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/spark-notebook-1.png)

When you run the last cell, you'll see a box appear that says "Spark Job Progress." Click on the arrow in that box to view your cluster's progress as it reads the full 12GB dataset! (Screenshot of this is shown below.)

![notebook 2](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/spark-notebook-2.png)

![notebook 3](https://github.com/Tselmeg-C/Churn_prediction_Udacity_Capstone/blob/master/images%20in%20Github%20readme/spark-notebook-3.png)

