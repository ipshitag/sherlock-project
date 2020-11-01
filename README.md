# Sherlock: data and deployment scripts.

Sherlock is a deep-learning approach to semantic data type detection which is important for, among others, data cleaning and schema matching. This repository provides data and scripts to guide the deployment of Sherlock.


### Demonstration of usage
A notebook can be found in `notebooks/` which shows how to download the raw and preprocessed data files, and demonstrates the usage of Sherlock.


### Data
Data can be downloaded using the `download_data()` function in the `helpers` module.
This will download 3.6GB of data into the `data` directory.


### Making predictions for new dataset
To use the pretrained model for generating predictions for a new dataset, features can be extracted using the `features.preprocessing` module. Please note that extracting features can take quite long due to the unoptimized code.
With the resulting feature vectors, the pretrained Sherlock model can be deployed on the dataset.

To retrain Sherlock, you are currently restricted to using 78 classes to comply with the original model architecture.
However, you can alter the model through the `models/sherlock_model.json` if you want to change the number of units in the final softmax layer.


### Retraining Sherlock
Sherlock can be retrained by using the code in the `deploy.train_sherlock` module.



## Project Organization
     
    ├── docs   <- Files for https://sherlock.media.mit.edu landing page.
     
    ├── data   <- Placeholder directory to download data into.
     
    ├── notebooks   <- Notebooks demonstrating the deployment of Sherlock using this repository.
            └── retrain_sherlock.ipynb
     
    ├── sherlock                
        ├── deploy  <- Scripts to (re)train models on new data and generate predictions.
            └── classes_sherlock.npy
            └── model_helpers.py
            └── predict_sherlock.py
            └── train_sherlock.py
        ├── features     <- Scripts to turn raw data, storing raw data columns, into features.
            ├── feature_column_identifiers   <- directory to hold feature names categorized by feature set.
               └── char_col.tsv
               └── par_col.tsv
               └── rest_col.tsv
               └── word_col.tsv
            └── bag_of_characters.py
            └── bag_of_words.py
            └── par_vec_trained_400.pkl
            └── paragraph_vectors.py
            └── preprocessing.py
            └── word_embeddings.py
        ├── models  <- Trained models.
            ├── sherlock_model.json
            └── sherlock_weights.h5
    
    └── requirements.txt <- Project dependencies.

------------
