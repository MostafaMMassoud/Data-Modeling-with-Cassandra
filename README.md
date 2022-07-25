# Data Modeling with Cassandra

### Introduction

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analysis team is particularly interested in understanding what songs users are listening to. Currently, there is no easy way to query the data to generate the results, since the data reside in a directory of CSV files on user activity on the app.

They'd like a data engineer to create an Apache Cassandra database which can create queries on song play data to answer the questions, and wish to bring you on the project. Your role is to create a database for this analysis. You'll be able to test your database by running queries given to you by the analytics team from Sparkify to create the results.

### Project Description

In this project, I'll apply what I've learned on data modeling with Apache Cassandra and compleete an ETL pipeline using python. I will start to map the project 3 specific queries in order to create 3 tables (Sessions, Users, Songs).

The code  starts by accumelating event_data CSV files into all_event_data.csv which included all the data of the month of Novembre year 2018. Then I will be creating each table separetly then Inserting the data from the all_event_data.csv file into the appropriate table. Finally I will test the insertion of data by running the 3 queries provided.

## Prerequisites

This project makes the folowing assumptions:

-   Python 3 is available
-   `cassandra` are available
- 
## Running the Python Jupyter notebook

Open the data_modeling.ipynb and running each code block


##  Data Modeling

###  all_event_data.csv

<img src="images/image_all_event_data.jpg" alt="denormalize data in all_event_data.csv"  width="800"/>

 ### Table1
##### Query1:
- Give me the `artist`, `song title` and `song's length` in the music app history that was heard during  `sessionId = 338`, and `itemInSession  = 4`
```
Table Name: sessions
	column 1: sessionId
	column 2: itemInSession
	column 3: artist
	Column 4: song_title
	Column 5: song_length
	PRIMARY KEY(SessionId,itemInSession)
```
### Table2
##### Query2:
- Give me only the following: `name of artist`, `song` (`sorted by itemInSession`) and `user` (`first` and `last` name) for `userid` = 10, `sessionid` = 182


```
Table Name: users
	column 1: userId
	column 2: sessionId
	column 3: itemInSession
	Column 4: artist
	Column 5: song
	Column 6: userName
	PRIMARY KEY(userId,sessionId,itemInSession)
```
### Table3
##### Query3:

- Give me every `user name` (first and last) in my music app history who listened to the `song` 'All Hands Against His Own'



```
Table Name: songs
	column 1: song
	column 2: userId
	column 3: sessionId
	Column 4: user_name
	PRIMARY KEY(song, userId, sessionId)
```

##  Description of Files

###  Directory: event_data

The directory of CSV files partitioned by date. 

###  Directory: images

Contain `image_all_event_data.jpg` which is a screenshot of what the denormalized data should appear like in the all_event_data.csv.

##  all_event_data.csv

a smaller event data csv file that will be used to insert data into the Apache Cassandra tables.

##  data_modeling.ipynb

This Python jupyter notebook for the data extraction, creating database table, and inserting data from CSV. into the database

##  requirements.txt

A list of Python modules used by this project.
