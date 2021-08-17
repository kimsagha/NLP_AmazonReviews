# Amazon Reviews

## Project Purpose
This is an NLP project which aims to process Amazon reviews using their ratings to predict whether a review is positive or negative.

## Data
* The data was obtained from Kaggle using the following steps:
    1. Download data folder 'archive' from the following link: https://www.kaggle.com/snap/amazon-fine-food-reviews
    2. Open the SQLite database ‘database.sqlite’ in the folder containing the data using e.g., ‘DB Browser for SQLite’
    3. Drop all but the following 3 columns: 'Score', 'Summary' and 'Text'
    5. Export database as .csv-file 'Reviews.csv' to read into .ipynb-files 'reviews.ipynb' and 'reviews_parallelized.ipynb'

## Versions - Normal vs. Parallelized
### 'reviews.ipynb'
* 5000 datapoints of each rating (positive and negative) was used for this initial solution - the entire dataset was too big and thus required too much computational time.
* The data was vectorised and then run through an SVM with a linear kernel.
* The end result was a model with ~84.3% accuracy and an F1 score of 84.0% for positive classifications and ~84.5% for negative.

### 'reviews_parallelized.ipynb'
* The previous solution in 'reviews.ipynb' was extended using Spark, enabling parallel-computing making use of more data.
* The entire dataset was used in theory but undersampling was performed to counteract the class imbalance which consequently reduced the size of the dataset significantly.
* Python package NLTK was installed for NLP purposes.
* Spark NLP library was also installed for parallelised NLP.
* A pipeline was built consisting of 9 steps:
    1. Document Assembler: an entry point into Spark NLP - converts raw text into Spark NLP native objext type 'Document', which can be tokenized
    2. Tokenizer: takes data of 'Document' type and splits its strings by empty spaces into words, i.e., Spark NLP native type 'Token'
    3. Normalizer: removes dirty characters from text and sets all tokens to lowercase letters
    4. Lemmatizer: retrieves the significant part of each word, i.e., the lemma
    5. Stop Words Cleaner: removes insignificant words such as: 'the', 'and', 'of'
    6. Finisher: converts data back into strings which may be used in Spark MLlib
    7. Count Vectorizer: extracts a vocabulary from document collections, converts text documents to vectors of term counts
    8. IDF (Inverse Document Frequency): estimator which computes the IDF-model of a vectorized vocabulary, scaling the features and reducing the weights of commonly appearing words
    9. Logistic Regression: spark ML model which classifies data (pos. or neg., i.e., 1 or 2)
* The end result was an extremely efficient model with ~88.7% accuracy and an F1 score of ~88.7%