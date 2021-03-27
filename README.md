# README

## Introduction

Introduction
A music streaming startup, Sparkify, has grown their user base and song database even more and want to move their data warehouse to a data lake. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

As their data engineer, you are tasked with building an ETL pipeline that extracts their data from S3, processes them using Spark, and loads the data back into S3 as a set of dimensional tables. This will allow their analytics team to continue finding insights in what songs their users are listening to.

This project build an ETL pipeline for a data lake hosted on S3. Data is loaded from S3, processing the data into analytics tables using Spark, and loaded back into S3. The Spark process is deployed on a cluster using AWS.

## Prject Dataset

For this project we use two datasets that reside in S3. Here are the S3 links for each:

- Song data: s3://udacity-dend/song_data
- Log data: s3://udacity-dend/log_data

## Schema

Below the structure of the Strar Schema database used for this project:

### Fact Table

| songplays   |               |             |
| ----------- | ------------- | ----------- |
| songplay_id | IntegerType   | PRIMARY KEY |
| start_time  | TimestampType | FOREIGN KEY |
| user_id     | StringType    | FOREIGN KEY |
| level       | StringType    |
| song_id     | StringType    | FOREIGN KEY |
| artist_id   | StringType    | FOREIGN KEY |
| session_id  | StringType    |
| location    | StringType    |
| user_agent  | StringType    |

### Dimension Tables

| users      |            |             |
| ---------- | ---------- | ----------- |
| user_id    | StringType | PRIMARY KEY |
| first_name | StringType |
| last_name  | StringType |
| gender     | StringType |
| level      | StringType |

| songs     |               |             |
| --------- | ------------- | ----------- |
| song_id   | StringType    | PRIMARY KEY |
| title     | StringType    |
| artist_id | StringType    |
| year      | TimestampType |
| duration  | DoubleType    |

| artists          |             |             |
| ---------------- | ----------- | ----------- |
| artist_id        | StringType  | PRIMARY KEY |
| artist_name      | StringType  |
| artist_location  | StringType  |
| artist_latitude  | DecimalType |
| artist_longitude | DecimalType |

| time       |               |             |
| ---------- | ------------- | ----------- |
| start_time | TimestampType | PRIMARY KEY |
| hour       | IntegerType   |
| day        | IntegerType   |
| week       | IntegerType   |
| month      | IntegerType   |
| year       | IntegerType   |
| weekday    | IntegerType   |

## Usage

### Configuration

Edit the config file `dl.cfg` setting the information of your IAM-Role that can read and write S3 buckets.

```cfg
[S3]
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
```

### ETL pipeline

This program has been executed on AWS EMR cluster.
To launch the script, run the following command:

```bash
spark-submit --master yarn ./etl.py
```
