# Data Modelling with Postgres

## Introduction

Sparkify which is a startup business wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.

## Project Description

Build an ETL pipeline using Python and SQL that transfers data from log files into tables in Postgres 

### Project Requirements

1. Define fact and dimension tables for a star schema
2. Write an ETL pipeline to transfer data from log and songs files

### Datasets

1. Song Dataset - contains metadata about a song and the artist of the song

2. Log Dataset - activity log fils from a music streaming app in json format partitioned by year and month. Contains attributes such as song, userid, firstname, lastname 

To view the json files, create a pandas dataframe first to read the data
ie. **df = pd.read_json('data/log_data/2018/11/2018-11-01-events.json', lines=True)**

### Data modelling

For this project, a star schema is needed because there is one fact table in the middle (songplays) surrounded by dimension tables - as seen in the ERD diagram

![ERD](Flowcharts - DBMS ER diagram (UML notation).jpeg)

##### Tables

###### Fact table

1. **songplays** - records in log data associated with song plays i.e. records with page NextSong
       - songplay_id SERIAL PRIMARY KEY
       - start_time bigint NOT NULL 
       - user_id int NOT NULL 
       - level varchar
       - song_id varchar
       - artist_id varchar
       - session_id int
       - location text
       - user_agent text

###### Dimension Tables

2. **users** - users in the app
        - user_id int PRIMARY KEY 
        - first_name varchar
        - last_name varchar
        - gender char(1)
        - level varchar

3. **songs** - songs in music database
        - song_id varchar PRIMARY KEY 
        - title varchar
        - artist_id varchar
        - year int
        - duration float

4. **artists** - artists in music database
        - artist_id varchar PRIMARY KEY
        - name varchar
        - location TEXT
        - latitude float
        - longitude float

5. **time** - timestamps of records in songplays broken down into specific units
        - start_time timestamp PRIMARY KEY
        - hour int
        - day int
        - week int
        - month int
        - year int
        - weekday varchar

##### Project files
1. **test.ipynb** displays the first few rows of each table to let you check your database.

2. **create_tables.py** drops and creates your tables. Run this file to reset your tables before each time you run your ETL scripts.

3. **etl.ipynb** reads and processes a single file from song_data and log_data and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.

4. **etl.py** reads and processes files from song_data and log_data and loads them into your tables. 

5. **sql_queries.py** contains all the sql queries, and is imported into the last three files above.

6. **README.md** contails the project details.


##### Project Steps

1. first run **create_tables.py** file to create the sparkifydb database, connect to it and create the other tables ```root@73544cf8f56d:/home/workspace# python create_tables.py 

2. Run all the cells in the **etl.ipynb** file to read the json data, convert it to a pandas dataframe and insert the data into all the tables. 

3. Run the **test.ipynb** file to make sure that the data has been inserted correctly in the tables. 
   - Example from songplays table: 
   ![songplays table](songplays_results.PNG)
   
4. Once satisfied that it all works, run the **etl.py** file to process all the files and insert into the respective tables. ```root@73544cf8f56d:/home/workspace# python etl.py 