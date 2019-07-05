# CLEANUP - Cleaning Up the Intro to Data Lake Labs
In this document, you will find notes to help you de-provision the resources created during the Intro to Data Lake labs.



## Resources to Delete
* Delete the Redshift cluster you created.  The suggested name was Redshift_[INITIALS]
* Delete the Glue ETL Job.  The suggested name was ETL_Reviews_to_Parquet_[INITIALS]
* Delete the Glue Crawler.  The suggested name was Crawl_Raw_Reviews_[INITIALS]
* Delete the tables from the Glue catalog. The suggested names were Kitchen_Reviews_[INITIALS] and XXXXX
* Delete the files from the S3 bucket you created.  To do so, you can delete files in the Raw_[INITIALS] and Processed_[INITIALS] prefixes.
* Delete the IAM roles Lab-IntroDataLake-Glue and Lab-IntroDataLake-Redshift


