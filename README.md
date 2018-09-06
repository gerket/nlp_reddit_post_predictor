# Predicting Which Subreddit A Post Is From
The prompt for this project was to rebuild the reddit database by predicting which post goes to which subreddit.  In order to do this, we need to gather our own training data by interacting with the reddit api to scrape posts from two different subreddits. Then we have to create a model to take in information about the post, such as the title and body, and use that as our features for the models.

The subreddits that I chose for this project are r/buildapc and r/talesfromtechsupport.

In order to figure out which model is optimal, I have created a function that takes in multiple parameters including data cleaning options, different models, different vectorizers, and hyper-parameters for each. The function then goes through and tests all of the different combinations of these parameters, with multiple different hyper-parameters for each of them as well.

#### FileTree
- Data/
    - main_dataframe.csv  
    The data that is used with the models, training and testing

    - new_data.csv  
    The data that is scraped from Reddit using the Data

    - backup_filename.csv  
    Backups of the main dataframe

- TG-Project3-Actual_Starter_Code-working.ipynb  
The main notebook with all of the EDA and models

- Data-Gathering-Script.ipynb
The supporting notebook with the data scraping


## Results

The function found that we should:
- clean the data by stemming it
- use the TF-IDF vectorizer with hyper-parameters:
    - `max_df=1`
    - `min_df=3`
    - `ngrams_range=(1,1)`
- use the ExtraTrees model with hyper-parameters:
    - `criterion='gini'`
    - `n_estimators=200`

This model had a cross_val_score of 0.99473 and a score of 0.99369 on testing data.

The 10 most important words*, as weighted by the model, are:
 - 'gt'
 - 'oh'
 - 'call'
 - 'storie'
 - 'email'
 - 'com'
 - 'minute'
 - 'phone'
 - 'http'
 - 'work'

 *_The words are stemmed so some may seem cut off_
