# Movies-ETL
This analysis aims to help Brita, who needs to gather data from Wikipedia and Kaggle, combine them, and save them into a SQL Database for the hackathon event.

## Overview of the analysis
ETL is a data pipeline process, Extract, Transform and Load. It is the process of moving information between databases. It is a core concept in data engineering, ensuring that data is consistent and maintains its integrity. Without consistent robust data, any type of analysis is impossible. A well-designed ETL pipeline strives to automate as much data wrangling as possible. We will be using Python and Pandas for data wrangling and Postgres SQL to store the finished data. The idea behind ETL is straight forward raw data exists in multiple places and need to be cleaned and structured before storing the data. In this analysis, We will be extracting the Wikipedia and Kaggle data from the respective files, Transforming the datasets by cleaning them up and joining them together, and loading the cleaned dataset into a SQL database. 
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/etl_process.png" width = 800><br>

## Resources Used
*DataSources*: [ratings.csv](https://github.com/fathi129/Movies-ETL/blob/master/Resources/ratings.csv), 
[movies_metadata.csv](https://github.com/fathi129/Movies-ETL/blob/master/Resources/movies_metadata.csv), [wikipedia_movies.json](https://github.com/fathi129/Movies-ETL/blob/master/Resources/wikipedia_movies.json) <br>
*Software used*: PostgreSQL 11, Pgadmin 4, Pandas, Jupyter notebook<br> 
*Language*: Python, SQL <br>

## Deliverable 1: 
### 1. Write an ETL Function to Read Three Data Files
It is the process of gathering data from multiple sources. These resources can include but are not limited to CSVs, APIs, JSON files, Excel files, data collected from web scraping, and data queried from another database. We have gathered data from Wikipedia,Kaggle data, and ratings data in this process. The three data files are read and converted to data frames.

<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/wiki_movies_dataframe.png" width = 800><br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/kaggle_metadata.png" width = 800><br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/ratings.png" width = 500><br>

## Deliverable 2:
### 2. Extract and Transform the Wikipedia Data

After the data is gathered, we manipulate the data to our liking before inserting it into the final database. It involves reading the data into pandas and removing null values. It may include removing entire columns if it is not required for the final product. Any alteration we perform on the data is called transformation. Here in this data, we have 193 columns; we have to reduce the columns by dropping the null values and duplicates. We have used the regex function to find the pattern matching in the columns. After performing the transformation, the Wikipedia data looks like this. The number of columns has been reduced to 23. 
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/cleaned_wiki_movies_df.png" width = 800><br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/wiki_movies_columns.png" width = 800><br>

## Deliverable 3:
### 3. Extract and Transform the Kaggle data

The transformation is performed on Kaggle data by dropping the null values and removing unnecessary columns. Then the Kaggle data is merged with wiki data, and the movie data frame is created. The movie data frame is combined with the ratings, and movies with rating data frame is created. The merged movie data frame looks like this below.

<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/movie_with_ratings_df.png" width = 800><br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/movie_df.png" width = 800><br>

## Deliverable 4:
### 4.Create the Movie Database

Finally, the transformed data is loaded to its destination. It can be done from Python directly using the Pandas.to_sql method and SQL Alchemy to insert a data frame into a table within a database. The following syntax is used to establish the connection to the database. Finally, after performing all the ETL processes, the movie data frame has 6052 rows, and the rating data frame has 26024289 rows.

<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/dbconnection.png" width = 800><br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/final_etl.png" width = 800><br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/importing_rows.png" width = 800><br>

When we check the database and the tables using sql query, we can see the data has been loaded into it.<br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/Resources/movies_query.png" width = 600><br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/Resources/ratings_query.png" width = 600><br>











