# Project: Data Modeling with Postgres

## Overview
This project applied data modeling techniques for a startup called Sparkify to simplify the analysis of the user data. This is done by creating a Postgres Relational database and then forming an ETL pipeline using Python to ingest the user data into the tables.

The project has two datasets which are descibed below- 

## Song Dataset
The first dataset is a subset of real data from the [Million Song Dataset](http://millionsongdataset.com/index.html). Each file is in JSON format and contains metadata about a song and the artist of that song.

A single song file looks as below-
```json
{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}
```

## Log Dataset
The second dataset consists of log files in JSON format generated by this [event simulator](https://github.com/Interana/eventsim) based on the songs in the dataset above. These simulate activity logs from a music streaming app based on specified configurations.

After reading the data into the dataframe, here is how the dataset looks like-
![dataset](log-data.png)

## Schema

 - Fact Table
            - songplays
        ```
        songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
        ```
        
 -  Dimension Tables
            - users
         ```
         user_id, first_name, last_name, gender, level
         ```
            - songs 
         ```
         song_id, title, artist_id, year, duration
         ```
            - artists
         ```
         artist_id, name, location, latitude, longitude
         ```
            - time
         ```
         start_time, hour, day, week, month, year, weekday
         ```

## ETL Pipeline
### create_tables.py
This file creates and drops the tables from the database.

### sql_queries.py
This file contains the SQL queries to perform the following -
Markup : * Create and Drop the tables
         * Insert records into the tables
         * Selecting records from the tables that matches a particular condition
         
### etl.py
This file contains functions to process raw json files and triggers the queries to insert the data into the database


## How to Run

 1. Run create_tables.py
 2. Run etl.py
         

## References

 - [PostgreSQL Documentation](https://www.postgresql.org/docs/9.5/datatype.html)
 - [Pandas Documentation](https://pandas.pydata.org/docs/)

