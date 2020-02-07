# Sparkify Data Modeling with Apache Cassandra

Sparkify is a startup company that needs help structuring their data in a way that makes it easy to query; particularly to analyze the songs users are listening to on the music streaming app. The goal here is to create a database to run each query using Cassandra. An ETL pipeline is created to transfer data from a csv file to the tables.

## Files:
* `event_data`: contains csv files.
* `event_datafile_new.csv`: All data into one file with needed columns.
* `Project_1B_ Project_Template.ipynb`: ETL pipeline to transfer data from csv file to Cassandra tables.

## Schema:
`session` Table
columns:  
* sessionId  
* itemInSession  
* artist  
* song  
* length  
* PRIMARY KEY: sessionId, itemInSession
    - The primary key consists of the partition key and clustering column; these are the columns that will be used to filter the data by.

`user_session` Table
columns:  
* userId
* sessionId
* itemInSession
* artist
* song
* firstName
* lastName
* PRIMARY KEY: userId, sessionId, itemInSession
    - The primary key consists of the partition key plus two custering columns; userId and sessionid are used to filter the data and itemInSession is used to sort the data

`song_user` Table
columns:  
* song
* userId
* firstName
* lastName
* PRIMARY KEY: song, userId
    - The primary key consists of the song column and userId column; the userId column is added as a clustering column to ensure that each row is unique.



## How to Run:
* Open the command line and navigate to the directory where Cassandra was unpacked.
* Type in `bin/cassandra -f` to start Cassandra.
* Open a new terminal window.
* Navigate to the downloaded repo via the command line and type `jupyter notebook'.
* Open the ipynb file and run the cells.

