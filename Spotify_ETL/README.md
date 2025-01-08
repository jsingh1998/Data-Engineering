# Spotify_ETL  
A complete pipeline project to extract Spotify data, process it, and load it into Snowflake.  

# Spotify Data Pipeline with AWS and Snowflake  

## Project Overview  

This project involves building a data pipeline to fetch, process, and store Spotify's top 100 Hindi songs data in the Snowflake data warehouse. The pipeline leverages AWS services like Lambda, S3, Glue, and Snowpipe, with Apache Spark handling the data transformations.  

## Prerequisites  

Before proceeding, ensure you have:  

- Access to required AWS services  
- A Snowflake account  
- A Spotify Developer account to get API credentials  
- Basic understanding of AWS Lambda, S3, Glue, Snowflake, and Apache Spark  

## Architecture  

<img width="524" alt="image" src="https://github.com/viraniriaz/SpotifyETL2/assets/82742908/44750134-ee33-4274-a484-b6a0baf5b9ad">  

The pipeline architecture includes the following steps:  

1. **Spotify API Integration**: Acquire API credentials (Client ID and Secret) from Spotify Developer.  
2. **Lambda Extraction**: Use AWS Lambda to extract the top 100 Hindi songs from the Spotify API.  
3. **S3 Storage**: Save extracted data into an Amazon S3 bucket.  
4. **AWS Glue Transformation**: Process and clean data using Apache Spark in Glue.  
5. **Snowflake Loading**: Leverage Snowpipe to load processed data from S3 into Snowflake.  
6. **Automated Notifications**: Set up event notifications for Snowpipe from S3 to ensure continuous data ingestion.  

## Setup Instructions  

1. **Get Spotify API Credentials**:  
   - Visit the Spotify Developer portal and log in or sign up.  
   - Create a new application to generate Client ID and Client Secret.  

2. **AWS Setup**:  
   - Develop a Lambda function for API extraction.  
   - Configure an S3 bucket to store raw and processed data.  
   - Set up an AWS Glue job to transform the data using Apache Spark scripts.  
   - Integrate S3 with Snowflake.  

3. **Deploy Code**:  
   - Upload and deploy the Lambda function for data extraction.  
   - Add Apache Spark scripts for transformation in AWS Glue.  

4. **Configure Snowflake**:  
   - Create a Snowflake stage for S3 integration.  
   - Use Snowpipe to automate loading data into Snowflake tables.  

## Usage Instructions  

1. **Data Extraction**:  
   - The Lambda function periodically fetches data from Spotify's API.  
   - Extracted data is stored in the designated S3 bucket.  

2. **Data Transformation**:  
   - AWS Glue processes the raw data using Spark scripts.  
   - The cleaned and structured data is stored back in S3.  

3. **Data Loading**:  
   - Snowpipe automatically ingests transformed data from S3 into Snowflake for further analysis.  

## Transformation Steps  

The data transformation is handled by Apache Spark in AWS Glue and involves the following:  

1. **Album Details**:  
   - Extract album details such as ID, name, release date, total tracks, and URL.  
   - Remove duplicate records based on album ID.  

2. **Artist Information**:  
   - Extract artist details from the track data.  
   - Create separate rows for each artist and retain attributes like ID, name, and URL.  
   - Remove duplicate artist records based on ID.  

3. **Track Information**:  
   - Extract song details from the API data.  
   - Expand arrays of tracks into separate rows, retaining fields such as ID, name, duration, popularity, and date added.  
   - Convert added date to a date format and remove duplicates.  

4. **Save to S3**:  
   - Transformed data is converted back to a DynamicFrame and saved to S3 in CSV format.  
   - Files are partitioned by date for better organization.  

## Contributor

- Jasvinder Singh  
