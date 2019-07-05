# CLEANUP - Cleaning Up the Intro to Data Lake Labs
In this document, you will find notes to help you de-provision the resources created during the Intro to Data Lake labs.



## Resources to Delete for each user
* Delete the Redshift cluster you created.  The suggested name was redshift-cluster-[INITIALS]
* Delete the Glue ETL Job if created (this was an optional part of Lab1).  The suggested name was ETL_Reviews_to_Parquet_[INITIALS]
* Delete the Glue Crawler.  The suggested name was Crawl_Raw_Reviews_[INITIALS]
* Delete the databases and tables from the Glue catalog. The suggested database name was Reviews_[INITIALS].  The suggested table names were "reviews" and "all_reviews_parquet".
* Delete the files from the S3 bucket you created.  To do so, you can delete files in the Raw_[INITIALS] and Processed_[INITIALS] folders.

## Resources to Delete at the account level
* Delete the entire S3 bucket "lab-introdatalake-[customer]" if every user is done with the labs.
* Delete the IAM roles Lab-IntroDataLake-Glue and Lab-IntroDataLake-Redshift if every user is done with the labs.


