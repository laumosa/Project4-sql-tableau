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
``` SQL
SELECT decade, name, average_rating FROM movies_table 
           WHERE average_rating IS NOT NULL
           AND decade = '2000s'
           OR decade = '2010s'
           OR decade = '2020s'
           ORDER BY average_rating DESC
           LIMIT 5;
 ```
2. Which film has the longest duration?
``` SQL
SELECT name, duration_min FROM movies_table 
           ORDER BY duration_min DESC
           LIMIT 1;
 ```
3. Who are the directors with more than 9 films in the database?
``` SQL
SELECT director, COUNT(name) FROM movies_table 
           WHERE director IS NOT NULL
           GROUP BY director
           HAVING COUNT(name) > 9
           ORDER BY COUNT(name) DESC;
 ```
4. What is the average rating of films in Horror genre?
``` SQL
SELECT AVG(average_rating) FROM movies_table 
           WHERE average_rating IS NOT NULL
           AND genre LIKE '%%Horror%%';
 ```
5. What is the average rating of films in Comedy genre?
``` SQL
SELECT AVG(average_rating) FROM movies_table 
           WHERE average_rating IS NOT NULL
           AND genre LIKE '%%Comedy%%';
 ```
6. In how many films did Robin Williams appear?
``` SQL
SELECT COUNT(name) FROM movies_table 
           WHERE cast LIKE '%%Robin Williams%%';
 ```
7. How many films were released in each decade?
``` SQL
SELECT decade, COUNT(name) FROM movies_table 
           WHERE decade IS NOT NULL
           GROUP BY decade
           ORDER BY decade;
 ```
14. Which films have an average rating below or equal to 1?
``` SQL
SELECT name, average_rating FROM movies_table 
           WHERE average_rating <= 1;
 ```
 
 ## Visualization - Tableau
