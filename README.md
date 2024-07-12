# Spotify Data Engineering End To End Project
## Overview
The architecture of the project is shown here the data will be present in our staging layer then we'll be using
AWS glue to build our ETL pipeline that will take a data from staging layer and
transfer into our data warehouse once our data warehouse is in
place we'll be running a glue crawler that will create a database and populate
a table for our database then we'll be using AWS athena to
query a data present in a table once everything is set up we can
use AWS quick site to to do a visualization and to gain a business
Insight out of our data.

the data set that will be using in this project is Spotify data set
Insight out of our data.Tthe data set consist of five CSV files albums artist Spotify data Spotify
features and Spotify tracks Spotify albums consist of details
of all the albums tracks artist and the release date of the
album Spotify artist consist of details of the artist name number of followers
in the genre they sing in Spotify data consist of album ID album name album
popularity artist Spotify features consist of
danceability energy loudness mode
speech liveliness and Valance of the music the tracks consist of track ID
track popularity. the data is in raw format so lots of pre-processing will be
required for this playlist I've already pre-processed the data and I'll be providing the data
I preprocessed the five CSV files and built three CSV file out of it which is albums, artist,s and tracks. 

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
