                                     #**SPARKIFY -- DATA MODEL FOR STREAMING APP**

Sparkify, a start-up entrepreneur is working on their new music streaming app. They aspire to build up an insight on collected data of songs and user activity, mainly focusing on user interest pattern listening to music.   But it is not easy way to query on the data, data sets are residing in directory of JSON logs on the user the activity on the app , as well as  a directory with JSON metadata on the songs in their app.

Sparkify had a data engineer for creating a repository on Postgres database with tables designed to optimize queries for song play analysis.  The repository will have a ETL pipe line to Postgres table from JSON data file and this analytical database will serve the business queries and analysis.

##**Prerequisites**

Python 3
Pandas and psycopg2 
PosgreSQL


##**Data sets**

Song Data SETs is  a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are filepaths to two files in this dataset.

***song_data/A/B/C/TRABCEI128F424C983.json***
***song_data/A/A/B/TRAABJL12903CDCF1A.json***


TRAABJL12903CDCF1A.json  looks like 

{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}

Log Data Sets is log file generated this event simulator based on the songs in the dataset above. These simulate activity logs from a music streaming app based on specified configurations. As example,   filepaths of two log files in this dataset.

log_data/2018/11/2018-11-12-events.json
log_data/2018/11/2018-11-13-events.json

As example data looks in log file as , 2018-11-12-events.json, looks like.

![Alt text](/data/log.png?raw=true "Optional Title")

Data Modeling 

For project implementation Star schema method followed , which is good for queries 
On song play analysis.

Fact Table
•	songplays - records in log data associated with song plays  
songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

Dimension Tables

•	users - users in the app
             user_id, first_name, last_name, gender, level

•	songs - songs in music database
             song_id, title, artist_id, year, duration

•	artists - artists in music database
             artist_id, name, location, latitude, longitude 

•	time - timestamps of records in songplays broken down into specific units
             start_time, hour, day, week, month, year, weekday


File structure 

Following files has been used in various steps of  etl , etl_pipeline 

1.	create_tables.py: drops and creates your tables. You run this file to reset   tables before each time you run your ETL scripts.
2.	etl.ipynb: reads and processes a single file from song_data and log_data and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.
3.	etl.py: reads and processes files from song_data and log_data and loads them into your tables. You can fill this out based on your work in the ETL notebook.
4.	README.md: provides discussion on this project.
5.	StarSchema.jpg: ERD for star schema of this project
6.	sql_queries.py: contains all your sql queries, and is imported into the last three files above.
7.	test.ipynb: displays the first few rows of each table to let us check on the database.
8.	Data sets : mentioned above 


Run process
1.	Run create_tables.py to create the database and tables.
2.	Run etl.py to process for loading, extracting and inserting the data.
3.	Run test.ipynb to confirm the creation of database and columns.

Conclusion 
This demo initial project  can give answer few business queries “ which are the top popular songs users are listening” , “ top favourite artist”  etc  
