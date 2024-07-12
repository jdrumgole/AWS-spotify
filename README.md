# Spotify Data Engineering End To End Project
## Overview

In this project, we build an end-to-end data engineering pipeline using AWS services to process Spotify data. We start by storing raw CSV data in S3 buckets, then create an ETL pipeline with AWS Glue to transform and load the data into a data warehouse bucket. AWS Glue Crawlers automatically catalog the data, making it queryable with AWS Athena. Finally, we use AWS QuickSight to create visualizations based on Athena queries, providing business insights from the processed data. This project demonstrates a scalable, automated, and secure data processing workflow.

In this project, we use several CSV files containing Spotify data for 2023:

**Spotify Albums:** Contains details about albums, including album ID, album name, artist ID, and release date.  
**Spotify Artists:** Includes information about artists, such as artist ID, name, number of followers, and genre.  
**Spotify Tracks:** Lists track details, including track ID, track name, album ID, and track popularity.  
**Spotify Features:** Provides audio features of tracks like danceability, energy, loudness, mode, speechiness, liveliness, and valence.  
**Spotify Data:** Includes a combination of album and artist popularity data.  

These files are uploaded to the S3 staging bucket and processed using AWS Glue to transform and join them into a structured format in the data warehouse bucket. The data is then cataloged by AWS Glue Crawlers, making it queryable by AWS Athena and visualizable in AWS QuickSight.

## Architecture
![Slide_16_9_1 (2)](https://github.com/user-attachments/assets/8a6e9424-8cce-4f68-9bda-825a0e0551ec)

## S3 Buckets
**Purpose**: Scalable object storage for data.

**Why I am Using It:**

Data Storage: Holds raw and processed data files, allowing scalable and durable storage.
Cost-Effective: Only pay for what you use, which is beneficial for large datasets.
Integration: Easily integrates with other AWS services like Glue and Athena for seamless data processing.

**Detailed Steps:**
Creating Buckets: Separates raw (staging) and processed data (data warehouse) to organize and manage data flow.
Uploading Data: Stores the CSV files needed for the project.
## Glue ETL
**Purpose**: Managed ETL (Extract, Transform, Load) service.
**Why I Use It:**

**ETL Automation:** Automates the extraction, transformation, and loading of data, reducing manual effort.
Scalability: Automatically scales to handle large volumes of data.
Data Catalog: Automatically catalogs data, making it easy to query and manage.
**Detailed Steps:**

ETL Pipeline Creation: Visually designs the data flow and transformation process.
Data Transformation: Joins and processes multiple data sources into a coherent format.
Data Cataloging: Uses Glue crawlers to create a metadata catalog that Athena can query.

**Running the Glue Job**

**Purpose:** Execute the data transformation pipeline.
**Why We Use It:**

**Operationalize ETL:** Runs the defined ETL processes, transforming raw data into a structured format for analysis.
Resource Management: Defines computational resources required for the job, ensuring efficient execution.
Detailed Steps:

**IAM Role Configuration:** Provides Glue with the necessary permissions to access S3 buckets.
Job Execution and Monitoring: Runs the job and monitors its progress to ensure successful data transformation.
## Crawler
**Purpose:** Automatically discover and catalog data in AWS S3.

**Why We Use It:**

**Metadata Generation:** Creates a data catalog with schema details, making it easier to query with Athena.
**Automation:** Eliminates the need for manual schema creation, ensuring that new data is automatically included in the catalog.
**Integration:** Works seamlessly with other AWS services, particularly Glue and Athena.
**Detailed Steps**
Configuration:

Source: Point the crawler to the data warehouse bucket in S3 where the transformed data resides.
Output: Define the target database in AWS Glue Data Catalog where the discovered tables will be stored.
Running the Crawler:

**Data Discovery:** The crawler scans the specified S3 path, infers the schema, and updates the Glue Data Catalog with table definitions.
**Schema Inference:** Automatically identifies data types and structures, handling updates when new data is added.
**Using the Catalog:**

**Querying:** The data catalog created by the crawler is used by Athena to run SQL queries on the data in S3.
**Visualization:** QuickSight uses the same catalog to create visualizations based on the data.
Benefits in the Project
**Efficiency:** Automates schema creation, reducing manual workload.
**Consistency:** Ensures accurate and up-to-date metadata, which is crucial for data analysis.
**Scalability:** Handles large datasets and adjusts to changes in data structure seamlessly.

## Athena
**Purpose:** Serverless interactive query service.
**Why We Use It:**

**Querying Data:** Allows SQL queries directly on data stored in S3 without needing to set up a database.
**Serverless:** No infrastructure to manage, with automatic scaling based on query complexity.
**Cost-Effective:** Pay per query, making it economical for infrequent data analysis tasks.

**Detailed Steps:**

**Configuration:** Sets up Athena to use the Glue data catalog.
**Query Execution:** Runs SQL queries to extract insights from the processed data in S3.
## Quicksight
**Purpose:** Business intelligence (BI) service for data visualization.
**Why We Use It:**

**Data Visualization:** Creates interactive dashboards and visualizations, enabling data-driven decision-making.
**Integration:** Connects seamlessly with Athena to visualize queried data.
**Ease of Use:** Provides a user-friendly interface for creating complex visualizations without deep technical knowledge.
**Detailed Steps:**

**Setup:** Signs up for QuickSight and configures it to connect to Athena.
**Creating Visualizations:** Imports data from Athena and builds visual representations to glean business insights.
