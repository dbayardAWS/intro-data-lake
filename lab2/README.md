# Part 3- Extend the lake with Data Warehousing (provision Redshift)
In this lab you will integrate Amazon Redshift to your data lake.

Amazon Redshift is a fully managed, petabyte-scale data warehouse service in the cloud. You can start with just a few dozen gigabytes of data and scale to a petabyte or more. The Amazon Redshift service manages all of the work of setting up, operating, and scaling a data warehouse. These tasks include provisioning capacity, monitoring and backing up the cluster, and applying patches and upgrades to the Amazon Redshift engine.

Learn more about Amazon Redshift [here](https://aws.amazon.com/redshift/).


## Before You Begin
* Complete the previous parts as this lab will use objects created by the other sections of the lab.

## Provision a new Redshift Cluster

* In the AWS Console, use the Services menu and navigate to the Redshift console.  One way to do so, is to expand the Services menu and type "Redshift" in the service search field.

* In the Redshift console, scroll down to the "Find the best cluster configuration" section.

![screenshot](images/RS1.png)

* In the cluster configuration section, you can experiment with the cluster size settings. When you are done, restore the settings to their defaults (20 GB) and click the "Launch this cluster" button
* In the cluster identifier field, change the field to be "redshift-cluster-[initials]".
* Enter a value for the master user password that you will remember.  If you want a suggestion, you can use "AWSuser1!"
* In the Available IAM roles drop-down, choose "Lab-IntroDataLake-Redshift" role.

![screenshot](images/RS2.png)

* Click the Launch cluster button, which will start creating your new Redshift cluster.
* Click the "View all clusters" button and wait for your cluster to be created (the Cluster Status will change to "available").  This can take 15 minutes or so.

![screenshot](images/RS3.png)

## Connect to your Redshift Cluster
There are multiple ways to connect to your new Redshift cluster, including via JDBC and ODBC.  For this lab, we will use the Query editor that is part of the Redshift console.

* Once your Redshift cluster is created, click on "Query editor" on the left-hand column.
* In the Credentials pop-up, choose "redshift-cluster-[initials]" as the Cluster.
* Enter "dev" as the Database.
* Enter "awsuser" as the Database user.
* Enter the password you used earlier.  If you followed the lab's suggestion, that password would be "AWSuser1!".

![screenshot](images/RS4.png)

* Click Connect

## Congratulations- you have provisioned a Redshift cloud data warehouse to use with your data lake

Click [here](NewLab2b.md) to advance to the next section




