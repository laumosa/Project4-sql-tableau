# Project4-sql-tableau
## Goal
The objective of this project consists on identifying a dataset and subsequently extracting, cleaning, and loading the dataset into SQL for the purpose of executing queries to explore the data. 
Furthermore, Tableau will be employed to create visual representations of the data.

## Tools
- Python 
- SQL
- Tableau

## Information source
Dataset hosted on Kaggel (https://www.kaggle.com/) titled "Movies from Allmovie.com". This dataset contains over 430.000 movies listed in allmovie.com, offering a comprehensive look at the world of film and filmmakers.

## Database description
- Each row of the database refers to a film.
- For each film it is given certain information such as title, genre, released date, language, director, duration, synopsis, average rating, cast, among others.
- The database contains 10.524 rows and 16 columns.

## Cleaning - Python
- Check for null values and duplicates
- Create a new column that denotes the decade in which each film was released based on its release date.
- Convert the duration of each film (given in hours and minutes) into a unified measure of minutes.
- Create a column for each film genre. 
- Save the dataset as a csv named "movies_dataset_clean".

## Querying - SQL
A list of questions have been set to use SQL for query its answer:
1. What are the top 5 highest-rated films of the 21st century?
```SQL
SELECT decade, name, average_rating FROM movies_table 
           WHERE average_rating IS NOT NULL
           AND decade = '2000s'
           OR decade = '2010s'
           OR decade = '2020s'
           ORDER BY average_rating DESC
           LIMIT 5;``` 
3. Which film has the longest duration?
4. Who are the directors with more than 9 films in the database?
5. What is the average rating of films in Horror genre?
6. What is the average rating of films in Comedy genre?
7. In how many films did Robin Williams appear?
8. How many films were released in each decade?
9. Which films have an average rating below or equal to 1?

