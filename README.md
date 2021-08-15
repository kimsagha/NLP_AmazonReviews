# Amazon Reviews

## Project Purpose
This is an NLP project which aims to process Amazon reviews using their ratings to predict whether a review is positive or negative.

## Data
* The data was obtained from Kaggle using the following steps:
    1. Download data folder 'archive' from the following link: https://www.kaggle.com/snap/amazon-fine-food-reviews
    2. Open the SQLite database ‘database.sqlite’ in the folder containing the data using e.g., ‘DB Browser for SQLite’
    3. Drop all but the following 3 columns: 'Score', 'Summary' and 'Text'
    5. Export database as .csv-file 'Reviews.csv' to read into .ipynb-file 'reviews.ipynb'