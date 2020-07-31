[Back to main guide](../README.md) | [Next](activity2.md)

____

## 1. Provision a data lake, data lake administrator and data lake analyst

### a. Launch CloudFormation Template

Launch the CloudFormation stack in one of the AWS regions. Other regions are also supported.

We recommend that CloudFormation template be launched from the user having administrator previliges.

Region | Launch
-------|-----
US East (N. Virginia) | [![Launch Solution in us-east-1](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/images/cloudformation-launch-stack-button.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=lf-bleiva&templateURL=https://templates-cf-bleiva-no-borrar.s3.amazonaws.com/lf-ml-devendpoint.template)

Edit **StackName** and **Alias** parameter name, instead bleiva, write your name.

Click **Next**. On the last page, select the checkbox **I acknowledge that AWS CloudFormation might create IAM resources with custom names** and click on on **Create Stack**.
Wait for cloudformation template to **Complete**.

CloudFormation template would create the below resources.
- Data Lake Administrator user (dladmin-${Alias})
- Data Lake Analyst (dlanalyst-${Alias})
- S3 Bucket with Sample Patient Dataset having duplicates. **(Use this S3 bucket throughout the lab. The one shown the in the screenshots is only for the reference.)** 
- Labelling file that would be used in Activity#8
- Glue Development Endpoint 
- SageMaker Notebook instance with Spark ETL code
- IAM Role for AWS Glue and Lake Formation

**NOTE: Password for dladmin and dlanalyst users is set to "welcome".**

### b. Setup Data Lake Administrator
Navigate to Lake Formation Dashboard from AWS Management Console.
![lakeformation-console](images/1-1.png)
First time you navigate to Lake Formation Dashboard page, you would be prompted for creating a Data Lake Administrator. Click on **“Add administrators”**.



OR

i) While you are logged in as an IAM Admin user

ii) Go to => Lake Formation Console **→ Admins and database creators → Data lake administrators → Grant**

iii) Click on **Add Administrators**

<img alt="add admin" src="images/1-2.png" width="60%" height="60%" >

iv) Select the Data Lake Administrator as **“dladmin”** user and click on **Save**.

<img alt="dladmin" src="images/1-3.png" width="60%" height="60%" >

v) Another recommended change that you would need to do is to go to Lake Formation Console **→ Data Catalog → Settings** and **uncheck** both the boxes as shown below and click on **Save** button.

<img alt="datacatalog" src="images/1-4.png" width="60%" height="60%" >


After this step you, would not be using this IAM user again. Instead you will use **dladmin** user as a Data Lake Administrator and **dlanalyst** user as a data lake analyst/developer.

___

[Back to main guide](../README.md) | [Next](activity2.md)
