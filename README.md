# Movies-ETL
The purpose of this analysis is to help Brita, who needs to gather data from wikipedia and kaggle and combine them and save them in to a SQL Database for hackathon event.

## Overview of the analysis
ETL is a datapipeline process,Extract,Transform and Load.It is the process of moving information between databases.It is a core concept in data engineering ensuring that data is consistent and maintains its integrity.Without consistent robust data any type of analysis is impossible.
A well designed ETL pipeline strives to automate as much as data wrangling as it can.We will be using Python and Pandas for data wrangling and Postgres SQL to store the finished data.The idea behind ETL is straight forward rawdata exists in multiple places and need to be cleaned and structured before storing the data.In this analysis,We will be extracting the wikipedia and kaggle data from the respective files,Transform the datasets by cleaning them up and joining them together and load the cleaned dataset in to a sql database.

## Resources Used
*DataSources*: [ratings.csv](https://github.com/fathi129/Movies-ETL/blob/master/Resources/ratings.csv), 
[movies_metadata.csv](https://github.com/fathi129/Movies-ETL/blob/master/Resources/movies_metadata.csv), [wikipedia_movies.json](https://github.com/fathi129/Movies-ETL/blob/master/Resources/wikipedia_movies.json) <br>
*Software used*: PostgreSQL 11, Pgadmin 4, Pandas, Jupyter notebook<br> 
*Language*: Python,SQL <br>

## Deliverable 1: 
### 1.Write an ETL Function to Read Three Data Files
It is the process of gathering data from multiple sources.These resources can include but are not limited to CSV's,API's,JSON files,Excel files,data gathered from web scraping and data queried from another database.In this process we have gathered data from wikimedia,kaggle data and ratings data.
The three data files are read and converted to dataframes.

<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/wiki_movies_dataframe.png" width = 800><br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/kaggle_metadata.png" width = 800><br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/ratings.png" width = 500><br>

## Deliverable 2:
### 2.Extract and Transform the Wikipedia Data

After the data is gathered,we manipulate the data to our liking before inserting in to the final database.It involves read the data in to pandas and removing null values.It may involve removing entire columns if it is not required for the final product.Any type of alteration we perform on the data is called transformation.Here in this data we have 193 columns we have to reduce the columns by dropping the null values and duplicates.we have used regex funcion to find the pattern matching in hte columns.After performing the transformation the wikipedia data looks like this.The number of columns has been reduced to 23.
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/cleaned_wiki_movies_df.png" width = 800><br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/wiki_movies_columns.png" width = 800><br>

## Deliverable 3:
### 2.Extract and Transform the Kaggle data

The transformation is performed on kaggle data by dropping the null values,by removing the unnecessary columns.Then the kaggle data is merged with wiki data and movie data frame is created.The movie data frame is merged with the ratings and movies with ratings dataframe is created.
The merged movies dataframe looks like this below.

<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/movie_with_ratings_df.png" width = 800><br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/movie_df.png" width = 800><br>

## Deliverable 4:
### 4.Create the Movie Database

Finally the transormed data is loaded to its destination.It can be done fromPython directly using Pandas.to_sql method and sql Alchemy,to insert a data frame in to a table with in a database.
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/final_etl.png" width = 800><br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/ETL%20screenshots/importing_rows.png" width = 800><br>

When we check database and the tables using sql query,we can see teh data has been loaded in to it.
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/Resources/movies_query.png" width = 600><br>
<img src = "https://github.com/fathi129/Movies-ETL/blob/master/Resources/ratings_query.png" width = 600><br>











