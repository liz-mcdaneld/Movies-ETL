# Movies Data
## Extract, Load, and Transform Movie Data

## Purpose
The purpose of this project is to create an automated pipeline that will take in new movie data, extract, transform and then load into existing tables. There are three sources of movie data, Wikipedia, Kaggle, and MovieLens rating. These will be transformed into readable data and added to a PostgreSQL database.

## Task list.
1. Create ETL pipeline to move raw data to SQL database.
2. Clean and transform data sources using Python.
3. Use Regex (regular expressions) to parse and transform data to a readable format.
4. Load data into Database with PostgreSQL.

## Extract the data
Extracting the Wikipedia Movies JSON file into a DataFrame. Initially we start with 193 columns of data.

[png]

Extracting the Kaggle Movie Metadata into a DataFrame. Initially we start with 24 columns of data.

[png]

Extracting the Ratings data into a DataFrame. Initially we start with 26,024,289 rows of data.

[png]

## Transform the data

### Wikipedia Movies
 Filtered out the TV shows from the wiki movies raw data. Dropped and duplicated IMDB data, while printing any exceptions. Remove columns that have non-null values. Conver the "Box office" data with Regex so that it is in readable format. Clean the budget, realease date, and running time columns. Confirmed the columns that will be in the cleaned Wiki movies DataFrame.

 [png]

 The transformed Wikipedia Movies Dataframe now only contains 22 columns of data.

 [png]

### Kaggle Movies 
Dropped unneccessary columns, 'title_wiki','release_date_wiki','Language','Production company(s)', from the movies DataFrame. Fill in the missing data. Filter to keep neccessary columns, and rename them. Merge the ratings DataFrame with the movies DataFrame and save to movies with ratings DataFrame.

[png]

The transformed Kaggle Movies merged with Wikipedia Movies DataFrame.

[png]

## Load the data into the Movie Database
Connect to the PostgreSQL database and add the movies DataFrame to a SQL database. Database now contains tables for movies DataFrame and Ratings.
#### Movies Query
[movies_query] 

#### Ratings Query
[ratings_query]