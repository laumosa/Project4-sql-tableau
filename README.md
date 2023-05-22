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
**A) Evolution of film genres across decades:**
The database includes data from the 1900s to the 2020s; however, there is only sufficient data available for the 60s, 70s, 80s, and 90s to facilitate meaningful comparisons among them. Consequently, we have selected these decades to construct a bar plot per decade and examine the progression of film genres over time.
Observing the plots below, it becomes evident that the genre "drama" holds the highest frequency, followed by comedy and action during the 60s, 70s, and 80s. Conversely, the genres of family and children dominate the 90s. Notably, the western genre has experienced a significant decline over time, whereas others, such as romance, have consistently maintained their respective positions in the ranking.
![image](https://github.com/laumosa/Project4-sql-tableau/assets/83134591/d8c31384-84f7-4d4d-a83c-ddafb0e36ae1)
![image](https://github.com/laumosa/Project4-sql-tableau/assets/83134591/5ea6c7b9-4966-4b53-898b-e94b75611e51)
![image](https://github.com/laumosa/Project4-sql-tableau/assets/83134591/d7bd592d-a5a0-4e7e-a578-8086507fd567)
![image](https://github.com/laumosa/Project4-sql-tableau/assets/83134591/bd8ae275-746e-413c-a662-df3b93a9bed0)

**B) List of movies from the 21st century acccording to its average rate:**
The highest-rated film of the 21st century is "Avenged" directed by Michael S. Ojeda, followed by "2001: A Space Odyssey" and "Casablanca". Subsequently, the average ratings of the remaining films fall below 9.
![image](https://github.com/laumosa/Project4-sql-tableau/assets/83134591/4d6de8b5-d620-4354-9b75-4d5ed552f051)

C) Comedy vs. Horror films duration:
I have conducted a comparison of film frequencies using a histogram plot for both the comedy and horror genres, given their contrasting nature. As depicted in the plot, a significant majority of films fall within the 60 to 100-minute range. However, for durations exceeding 100 minutes, comedy films exhibit higher frequency compared to horror films, while the reverse holds true for films lasting less than 60 minutes. It is important to acknowledge that the compilation of films may contain a greater number of comedies than horror films, potentially introducing bias into the results.
![image](https://github.com/laumosa/Project4-sql-tableau/assets/83134591/3405e679-6f79-45c2-8fed-cba0e5d528ad)





