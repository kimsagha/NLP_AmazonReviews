# Amazon Reviews

## Project Purpose
This is an NLP project which aims to process Amazon reviews using their ratings to predict whether a review is positive or negative.

## Data
* The data was obtained from Kaggle using the following steps:
    1. Download data folder 'archive' from the following link: https://www.kaggle.com/snap/amazon-fine-food-reviews
    2. Open the SQLite database ‘database.sqlite’ in the folder containing the data using e.g., ‘DB Browser for SQLite’
    3. Drop all but the following 3 columns: 'Score', 'Summary' and 'Text'
    4. Get counts for each rating (i.e., Score) to obtain knowledge of the data distribution using the following SQLite statements:
        * SELECT count(Reviews.Score)  FROM Reviews WHERE Reviews.Score == 1;
- 52268

SELECT count(Reviews.Score)  FROM Reviews WHERE Reviews.Score == 2;
- 29769

SELECT count(Reviews.Score)  FROM Reviews WHERE Reviews.Score == 3;
- 42640

SELECT count(Reviews.Score)  FROM Reviews WHERE Reviews.Score == 4;
- 80655

SELECT count(Reviews.Score)  FROM Reviews WHERE Reviews.Score == 5;
- 363122