# SETUP - Preparing for the Intro to Data Lake Labs
In this document, you will setup your AWS account to run the Intro to Data Lake labs.



## Contents
* [Before You Begin](#before-you-begin)
* [Creating Users](#creating-users)
* [Account Service Limits](#account-service-limits)
* [Craete a S3 bucket](#create-a-s3-bucket)
* [Create an IAM role for Redshift](#create-an-iam-role-for-redshift)
* [Create an IAM role for Glue](#create-an-iam-role-for-glue)
* [Before You Leave](#before-you-leave)

## Before You Begin
* These labs were built so that multiple users in the same AWS account can run them at the same time.
* These setup instructions describe the steps that should be done once per account (as compared to once per user).
* The labs should be able to run in any AWS region, but the public dataset we will use resides in us-east-1, so using us-east-1 will be slightly faster at times.
* The labs assume that the VPC and subnets to be used already exist.

## Creating Users
* The users will be using S3, Glue, Athena, Redshift, and Cloudwatch and should have at least admin privileges for those services.
* XXXXXXXXX - test with specific privileges and document

## Account Service Limits
* Each user will create a couple of Glue Crawlers and ETL jobs.  Depending on the number of users and the number of existing glue resources already provisioned, you may likely need to request a service limit for Glue.  As a best practice, you should do this a few days PRIOR to the labs.
* XXXXXXXXXXXXX - call out specific limits to request and document how to request the increase


## Create a S3 bucket
* The suggested name is lab-introdatalake-[customer], where [customer] is replaced with the customer name.

![screenshot](images/S3.png)


## Create an IAM role for Redshift
In this section we will create an IAM role for Redshift that can access S3 and Glue.  For reference, you can learn more in the [documentation](https://docs.aws.amazon.com/redshift/latest/mgmt/authorizing-redshift-service.html)

* Navigate to the IAM console, click on Roles on the left column, then click on Create role.
* Select "AWS service" as the type of trusted entity.
* Choose "Redshift" as the service that will use this role.
* Choose "Redshift - Customizable" as the use case.
* Click "Next: Permissions"
* In the Filter policies search field, type "s3"
* Click the checkbox in front of AmazonS3ReadOnlyAccess

![screenshot](images/RSIAM1.png)

* Go back to the Filter policies search field and type "glue"
* Click the checkbox in front of AWSGlueConsoleFullAccess

![screenshot](images/RSIAM2.png)

* Click "Next: Tags"
* Click "Next: Review"
* Type "Lab-IntroDataLake-Redshift" for the Role name.
* Click "Create role"

![screenshot](images/RSIAM3.png)


## Create an IAM role for Glue
In this section we will create an IAM role for Glue that can access S3.  For reference, you can learn more in the [documentation](https://docs.aws.amazon.com/glue/latest/dg/create-an-iam-role.html)

* Navigate to the IAM console, click on Roles on the left column, then click on Create role.
* Select "AWS service" as the type of trusted entity.
* Choose "Glue" as the service that will use this role.
* Click "Next: Permissions"
* In the Filter policies search field, type "s3"
* Click the checkbox in front of AmazonS3FullAccess

![screenshot](images/GlueIAM1.png)

* Go back to the Filter policies search field and type "glue"
* Click the checkbox in front of AWSGlueServiceRole

![screenshot](images/GlueIAM2.png)

* Click "Next: Tags"
* Click "Next: Review"
* Type "Lab-IntroDataLake-Glue" for the Role name.
* Click "Create role"

![screenshot](images/GlueIAM3.png)







* Determine and capture the following information and login to the [AWS Console](https://console.aws.amazon.com/). If you are new to AWS, you can [create an account](https://portal.aws.amazon.com/billing/signup).
  * [Your-AWS_Account_Id]
  * [Your_AWS_User_Name]
  * [Your_AWS_Password]
* Determine the [AWS Region Name] and [AWS Region Id] which is closest to you and switch your console to that [Region](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html).  

## Configure Security
### VPC
Create or identify a VPC where you will launch your Redshift cluster.  For our purposes we will create a **VPC** to isolate the traffic.
```
https://console.aws.amazon.com/vpc/home?#CreateVpc:
```
![](../images/VPC.png)
### InternetGateway
Create or identify an Internet Gateway.  For our purposes we will create an **Internet Gateway**. Once created, select the Internet Gateway and attach it to the VPC created earlier.  
```
https://console.aws.amazon.com/vpc/home?#Create%20Internet%20Gateway:
```
![](../images/InternetGateway.png)
![](../images/InternetGatewayAttach1.png)
![](../images/InternetGatewayAttach2.png)

## Configure Client Tool
* See [Prerequisites](#prerequisites) for more details on downloading and installing [SQL Workbench/J](http://www.sql-workbench.net) and the [Redshift JDBC Driver](https://docs.aws.amazon.com/redshift/latest/mgmt/connecting-to-cluster.html). 
* Launch SQL Workbench/J and navigate to [File | Manage Drivers].
* Select "Amazon Redshift" and set the driver Library location to where you downloaded the Redshift JDBC Driver. Click Ok.
![](../images/Library.png)
* Navigate to [File | Connect Window] to create a new connection profile and modify the following settings and once complete click on the "Test Connection" button.
  * Name - "LabConnection"
  * Driver - Amazon Redshift (com.amazon.redshift.jdbc.Driver)
  * URL - Find this by navigating to the [Cluster List](https://console.aws.amazon.com/redshift/home?cluster-details:#cluster-list:), selecting your cluster, and copying the JDBC URL.  
  ![](../images/JDBCUrl.png)
  * Username - [Master user name]
  * Password - [Master user password]
  * Autocommit - Enabled
  
![](../images/Connection.png)

## Run Sample Query
* Run the following query to list the users within the redshift cluster.  
```
select * from pg_user
```
* If you receive the following results, you have established connectivity and this lab is complete.  
![](../images/Users.png)

## Before You Leave
If you are done with the lab, please follow the cleanup instructions to avoid having to pay for unused resources.
