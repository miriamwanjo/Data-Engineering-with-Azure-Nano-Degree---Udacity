# Data Modelling with Apache Cassandra

## Introduction

Sparkify which is a startup business wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.

## Project Description

Build an ETL pipeline using Python and transfer data to tables created in Apache Cassandra

### Project Requirements

1. Create Apache Cassandra keyspace ```CREATE KEYSPACE```
2. Create tables, INSERT data and query them for validation
3. Query the tables to answer 3 questions:
  -
      1. Give me the artist, song title and song's length in the music app history that was heard during sessionId = 338, and itemInSession = 4

      2. Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182

      3. Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'
### Datasets

1. event_data Dataset - contains logs from a music app history including information on users, songs, artist names, song title and duration.

### Prerequisites

- Python 3.7
- Apache Cassandra


##### Project files
1. **event_datafile_new.csv** contains the denormalized data used for modelling

2. **Project_1B_ Project_Template.ipynb** jupyter notebook to build the etl pipeline


##### Project Steps

1. Run **Project_1B_ Project_Template.ipynb** file to denomalize raw data, create a Cassandra keyspace, tables and insert data into the tables
2. Validate data by running select queries to get answers for the questions outlined in the project Prerequisites section. 
