# Spotify Data Pipeline using Snowflake, AWS, Python, Tableau

## Overview

### This project demonstrates an end-to-end data pipeline using the Spotify API, AWS services (S3, Lambda, EventBridge, IAM, CloudWatch), Snowflake as a data warehouse, and Tableau for data visualization and analytics. The pipeline is orchestrated using AWS Lambda and EventBridge, with logs and monitoring handled by CloudWatch.

## Project Architecture
![End-To-End Project Architecture](https://github.com/Adwait0043/spotify-end-to-end-data-engineering-project-using-aws-snowflake/blob/main/End-to-End-Architecture.png)



## Technologies Used
1. Programming Language - Python
2. Scripting Language - SQL
3. AWS
   - IAM( Identity and Access Management)
   - S3 ( Simple Storage Service)
   - Lambda
   - CloudWatch
   - Eventbridge
4. Snowflake : Cloud data warehouse for data storage and querying.
5. Tableau : Data visualization and analytics tool for reporting on Spotify data.
6. Spotify API: API used to retrieve music data such as tracks, artists, and albums.

## Data Flow
1. Data Ingestion: Extract song metadata from the Spotify API using AWS Lambda
2. Data Storage: Store raw data in AWS S3.
3. Event-Driven Orchestration: Use AWS EventBridge to trigger data processing workflows.
4. Data Transformation: Use AWS Lambda to clean and transform data.
5. Data Loading: Load the transformed data into Snowflake.
6. Analytics: Use Tableau to visualize and analyze the data stored in Snowflake.
7. Monitoring: Monitor pipeline execution with AWS CloudWatch.

## Scripts for project 
1. [Data Extraction ](Data_Extraction_From_Spotify_API_Using_Python.ipynb)
2. [Data Extraction in AWS Lambda](Data_Extraction_Source_Code_AWS_Lambda.ipynb)
3. [Data Transforamtion in AWS Lambda](Data_Transformation_Source_Code_AWS_Lambda.ipynb)

## Transformed Data (Format : csv)
1. [Album.csv](https://github.com/Adwait0043/spotify-end-to-end-data-engineering-project-using-aws-snowflake/blob/main/album_transformed_2024-10-03%2019_34_07.292656.csv)
2. [Artist.csv](https://github.com/Adwait0043/spotify-end-to-end-data-engineering-project-using-aws-snowflake/blob/main/artist_transformed_2024-10-03%2019_34_07.392659.csv)
3. [Songs.csv](https://github.com/Adwait0043/spotify-end-to-end-data-engineering-project-using-aws-snowflake/blob/main/song_transformed_2024-10-03%2019_34_07.014263.csv)

## Motivation
Why Spotify?
Spotify is one of the most popular music streaming platforms globally, boasting a vast repository of music data, including tracks, artists, albums, and user listening habits. Analyzing Spotify data can provide valuable insights into music trends, artist popularity, and listener preferences, making it an ideal choice for a data engineering project focused on real-world applications.

Real-World Use Case
The ability to efficiently extract, transform, and analyze large volumes of music data is crucial for various stakeholders in the music industry, including:

Music Streaming Services: To personalize user experiences and recommend new music.
Artists and Record Labels: To understand audience demographics and track performance metrics.
Market Analysts: To identify emerging trends and inform strategic decisions.

## Challenges Faced
**1. Handling API Rate Limits**
Issue: The Spotify API imposes rate limits on the number of requests that can be made within a specific timeframe, which can hinder data extraction efforts.
Solution:
    -- Rate Limiting Logic: Implemented exponential backoff strategies within AWS Lambda functions to gracefully handle rate limit responses and retry requests as necessary.
    -- Batch Requests: Optimized data extraction by batching requests where possible, reducing the overall number of API calls and adhering to rate limits more effectively.

**2. ETL Process Optimization**
Issue: Processing large volumes of data efficiently to ensure timely transformation and loading into Snowflake without incurring excessive costs or delays.
Solution:
    -- Lambda Function Optimization: Fine-tuned memory and timeout settings for AWS Lambda functions to balance performance and cost, ensuring rapid data processing without over-provisioning resources.
    -- Parallel Processing: Leveraged concurrent executions within Lambda to handle multiple data segments simultaneously, speeding up the ETL process.

**3. Data Quality Issues**
Issue: Ensuring the accuracy, consistency, and cleanliness of the data extracted from Spotify to maintain high-quality analytics and reporting.
Solution:
    -- Data Validation: Implemented validation checks within transformation scripts to identify and rectify inconsistencies, missing values, or anomalies in the data.
    -- Error Handling: Added robust error handling mechanisms to capture and log data quality issues, facilitating timely resolution and maintaining data integrity.
