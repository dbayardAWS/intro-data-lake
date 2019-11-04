# More Glue - Install a Spark History Server
In this section, we are going to launch a Spark History Server on an EC2 instance.  We are doing this as a way to be able to use the "Spark UI" with our Glue Developer Endpoint.  The Spark History Server process running on EC2 will have access to the SparkUI event logs which are being written to the glue-sparkui-history folder in your S3 lf-datalake bucket.  The History Server uses those event logs to be able to run the Spark UI web application.


Then start History Server
https://docs.aws.amazon.com/glue/latest/dg/monitor-spark-ui-history.html

Use the us-east-1 CF
https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?templateURL=https://aws-glue-sparkui-prod-us-east-1.s3.amazonaws.com/public/cfn/sparkui.yaml

Name: SparkUI
IP Address Range: 0.0.0.0/0
EventLogDir: s3a://lf-data-lake-bucket-565578166282/sparkui-history/
KeystorePassword: enter at least 6 character such as welcome1
VPC: choose the one called LF-Workshop-VPC
subnet: choose the one called LF-Workshop-PublicSubneOne


In outputs, grab the SparkUiPublicUrl
In a new browser window, open up that URL




## Congratulations - you have launched a Developer Endpoint
Take 5minutes or so to provision - while it is provisioning, please continue to the [next section](glue3.md).

