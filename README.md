# Data-Migration Project With S3-Documentdb(NoSQL)

## Problem Statement:

An URL that points to a zip file is provided.The zip file contains multiple JSON files. The JSON files contain multiple documents with various data structures.Goal is to download the zip file from the URL, extract the data from the zip file, process the JSON files, store it in Amazon S3, and load it into Amazon Database (NoSQL).

## Getting the Data

Using Boto3 API, I've created an s3 bucket to store the zipfile. Using Requests module I got the zipfile from the url through get method in a variable. I didn't write it into my local. Using s3 put_object method I put it in the bucket directly.

## Unzipping

Using get_object method I've read the zipfile. Using zipfile module i've extracted allthe 14752 json files.And I uploded the json files in an s3 bucket.

## Loading into Database

I've chosen AWS Docuument db which is a NoSQL database to store the data. Using Pymongo module connected with the DocumentDb cluster. I created a database named sec_database inside which I created a collection sec_collection.
Using s3 list_object method I created a list of file names of all the json files. By looping through the list of names I read each json file. For the unique id I derived it from the filename using os module. And I uploaded into the database.
