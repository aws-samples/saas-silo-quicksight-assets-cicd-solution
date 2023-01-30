# CI/CD of QuickSight Assets in SaaS Silo deployment model- Reference Solution

## Steps for creating CI/CD of QUickSight assets in your own organization
Files in this folder are for review only. CloudFormation script that is run in Toolchain account, automatically downloads these files from a public S3 bucket and checks them into the CodeCommit Repository. You can edit these files and check them again in CodeCommit repository to test CI/CD of QuickSight assets.

In this document we will share with you the steps we took to create these files. You can also create CI/CD of your organization's QuickSight assets i.e. DataSource, DataSet, Analysis and Dashboard.

First step in the process is creating QuickSight DataSource, DataSet, Analysis, Dashboard in a development environment. If you want to learn about creating QuickSight assets, please follow the instructions in this workshop: https://catalog.workshops.aws/quicksight/en-US/author-workshop/1-build-your-first-dashboard/exercises

Second step in the process is to download the QuickSight assets as JSON documents using the new API Capabilities added during re:invent 2022. You can refer to the following blog in order to learn about downloading the JSON documents: https://aws.amazon.com/blogs/aws/new-amazon-quicksight-api-capabilities-to-accelerate-your-bi-transformation/

## Data Source & Data Set
DataSource and DataSet have native support in CloudFormation. You can use the json output of  **DescribeDatasourceDefinition** and **DescribeDatasetDefinition** API calls to create CloudFormation template. We have provided sample CloudFormation scriptin this tutorial: **QuickSight_Assets_CI_CD\SAASQSAssetsViaCF.yaml**. 



## Analysis & Dashboard
Analysis and Dashboard do not have native CloudFormation support. In this tutorial, we have provided two Custom Lambda functions to create these assets using QuickSight SDK. In order to use the code, you need to provide the JSON response of **DescribeAnalysisDefinition** and **DescribeDashboardDefinition** calls to the generic custom lambda functionality in the CloudFormation script that we have provided in this tutorial: **QuickSight_Assets_CI_CD\SAASQSAssetsViaCF.yaml**. 

## License
This library is licensed under the MIT-0 License. See the LICENSE file.

## Security
See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.
