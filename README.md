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
