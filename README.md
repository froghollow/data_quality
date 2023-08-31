# Simple Data Quality
This project demonstrates how to use [PyDeequ](https://github.com/awslabs/python-deequ) and [Glue ETL](https://aws.amazon.com/glue/) to define, execute, and manage data quality processes utlizing AWS Serverless Computing technologies.   PyDeequ is an open-source Python wrapper over Deequ which is an open-source tool developed and used at Amazon. PyDeequ allows us to use its data quality and testing capabilities from Python and PySpark, the language of choice of many data scientists.  Although developed by and for AWS, many of these tools and concepts can be applied to any Spark plaform.

AWS has integrated the DeeQu framework with its [Glue Data Catalog](https://docs.aws.amazon.com/glue/latest/dg/catalog-and-crawler.html) and [Glue ETL](https://aws.amazon.com/glue/) services, both of which are being utilized in our [file ingest pipeline](https://github.com/froghollow/simple-file-processing). 
 Glue Data Quality provides flexible interfaces via the Glue Management Console, APIs, and the [Data Quality Definition Language (DQDL)](https://docs.aws.amazon.com/glue/latest/dg/dqdl.html).   DQDL provides a simple declarative syntax for defining data quality rules, which are then executed by a common Glue ETL job.  This makes data quality more approachable for non-coders, and is easier to maintain than a set of Glue ETL job for every rule set which need to go thru SDLC for adding or modifying rules.  DQDL exposes only a subset of (Py)DeeQu features, and implements some features not available in (Py)DeeQu (see [dqdl-pydeequ-xwalk.csv](dqdl-pydeequ-xwalk.csv)

AWS Glue Data Quality currently available only on Commercial Regions, not yet on GovCloud.   This project provides an Interim Solution to be implemented using PyDeequ within a Glue ETL job
- Build Python Custom Library to support selected Data Quality API functionality
  - Store DQDL rulesets in DynamoDB
  - Glue ETL orchestrated by Step Functions, same as SIMPLE File Processing
  - Data Quality Runs logged in DynamoDB
- Result Sets
  - Store on S3 cataloged as Glue DB
- Rule Set Recommendations
  - Not supported by Interim solution
- Transition Custom Library to Wrapper for standard Boto3 API
  - option to utilize either Glue Data Quality or Glue ETL






