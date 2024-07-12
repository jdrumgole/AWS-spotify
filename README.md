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

## S3 Staging
## Glue ETL
## S3 DataWarehouse
## Crawler
## Quicksight
