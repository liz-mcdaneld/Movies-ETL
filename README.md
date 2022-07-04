# Movies Data
## Extract, Transform, and Load Movie Data into DataBase

## Purpose
The purpose of this project is to create an automated pipeline that will take in new movie data, extract, transform and then load into existing tables. There are three sources of movie data, Wikipedia, Kaggle, and MovieLens rating. These will be transformed into readable data and added to a PostgreSQL database.

## Task list.
1. Create ETL pipeline to move raw data to SQL database.
2. Clean and transform data sources using Python.
3. Use Regex (regular expressions) to parse and transform data to a readable format.
4. Load data into Database with PostgreSQL.

## Extract the data
Extracting the Wikipedia Movies JSON file into a DataFrame. Initially we start with 193 columns of data.

![wiki_movies_df_png](https://user-images.githubusercontent.com/103263248/177202351-58722505-a7a8-4c2e-acde-3035e5d52300.png)

Extracting the Kaggle Movie Metadata into a DataFrame. Initially we start with 24 columns of data.

![kaggle_metadata_png](https://user-images.githubusercontent.com/103263248/177202370-e73955ca-cb64-477e-a8d2-ec71a8250635.png)

Extracting the Ratings data into a DataFrame. Initially we start with 26,024,289 rows of data.

![ratings_png](https://user-images.githubusercontent.com/103263248/177202397-908497de-c751-4abd-a112-45ad2ccf656c.png)

## Transform the data

### Wikipedia Movies
 Filtered out the TV shows from the wiki movies raw data. Dropped and duplicated IMDB data, while printing any exceptions. Remove columns that have non-null values. Conver the "Box office" data with Regex so that it is in readable format. Clean the budget, realease date, and running time columns. Confirmed the columns that will be in the cleaned Wiki movies DataFrame.

![clean_wiki_movies_columns_png](https://user-images.githubusercontent.com/103263248/177202426-13643dc8-2398-4912-bd19-3f8f3822a7f0.png)

 The transformed Wikipedia Movies Dataframe now only contains 22 columns of data.

 ![clean_wiki_movies_df_png](https://user-images.githubusercontent.com/103263248/177202449-1a8ea173-4d69-4c49-93ef-904fbd9ff1c7.png)

### Kaggle Movies 
Dropped unneccessary columns, 'title_wiki','release_date_wiki','Language','Production company(s)', from the movies DataFrame. Fill in the missing data. Filter to keep neccessary columns, and rename them. Merge the ratings DataFrame with the movies DataFrame and save to movies with ratings DataFrame.

![movies_with_ratings_png](https://user-images.githubusercontent.com/103263248/177202511-f94476fa-67aa-4cdb-b9e3-9f126535635e.png)

The transformed Kaggle Movies merged with Wikipedia Movies DataFrame.

![clean_kaggle_movies_df_png](https://user-images.githubusercontent.com/103263248/177202474-f3ea7dac-7df1-4e32-be71-9d8b6160b807.png)

## Load the data into the Movie Database
Connect to the PostgreSQL database and add the movies DataFrame to a SQL database. Database now contains tables for movies DataFrame and Ratings.
#### Movies Query
![Movies_query](https://user-images.githubusercontent.com/103263248/177202537-287d63fd-4304-46dd-9eb0-c1d88df71490.png)

#### Ratings Query
![Ratings_query](https://user-images.githubusercontent.com/103263248/177202563-77836e27-3814-469a-bb61-b3288662addd.png)
