# 6220-spam-detection-project
Welcome to our spam detection ensemble repository! 

# Repository Structure

> -- analysis<br>
> -- code<br>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -- models<br>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -- preprocess<br>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -- ensemble<br>
> -- data<br>

- `analysis`: contains all of our statistics and generated word clouds regarding ham/spam misclassification and model performance
- `code`: folder that houses the majority of our pipeline
  - `models`: Python notebooks containing each of the model types (i.e., BiLSTM, NN, and sklearn models)
  - `preprocess`: Python notebooks for processing the individual datasets and then combining the datasets into the `data/fully_combined.csv` file
  - `ensemble`: folder with `Ensemble.ipynb` and model classification results
    - `Ensemble.ipynb`: Python notebook that pools each of the models' individual results into a singular dataframe, then runs the majority voting process on these results
- `data`: folder containing `fully_combined.csv`
  - `fully_combined.csv`: CSV file of our combined dataset

# How to run through the full pipeline

  ## Architecture Diagram
  ![Architecture Diagram](architecture.png)

  ## Data
  Our `fully_combined.csv` dataset consists of three different datasets found from the spam detection model repositories that we were adapting for this project. These datasets are as follows: Enron, ADCG, and Spam Assassin. In total, the `fully_combined` dataset consists of 33,752 emails each classified as either ham (16,143 emails) or spam (17,609 emails), which makes the set very balanced between the two labels. The data format within the `fully_combined.csv` file is a row dedicated to each email and the email represented as the subject + body concatenated into a single string, along with the ham/spam label in a separate column. 

 ### Preprocessing and combining
  We used a combination of three datasets to test our models on: ADCG, SpamAssassin, and Enron.
  
  #### Preprocessing each Dataset Independently
  For each of the three datasets, ADCG, SpamAssassin, and Enron, we took out only necessary features (Subject + Body and the labels) which was done in the three separate `ACDGPreProcess.ipynb`, `spamAssassinPreProcess.ipynb`, and `ENRONSpamEmailProcessing.ipynb`. These python notebooks took consistant features from each of the three datasets we used and put them into respective csv files.
  We then had to clean each of the three datasets uniformly, which was done through the `CombineDataSpamEmailProcessing.ipynb` python notebook. This took out escape sequences, long words, non-ASCII, punctuation, numbers, stopwords and converted to lowercase then lemmatized. Now we have three independent dataframes that are each preprocessed the same way.
  
  #### Combining the Datasets
  From there, given the three preprocessed dataframes, we were easily able to concatenate the three datasets, shuffle the data and finally remove all duplicate emails through the last cell in the `CombineDataSpamEmailProcessing.ipynb` python notebook. This combined dataset was written into the `fully_combined.csv` and could be accessed and used by other models. This combined large dataset is open to the public to use for future spam detection models.
  
  ## Models

  ### sklearn Models: LinearSVC, MultinomialNB, GaussianNB
  These models all accept vectorized emails as input. They have a 60/40 train/test split, and the LinearSVC has the best performance out of the three. To reproduce the vectorized dataset and scikit-learn models, run through the `code/models/sklearn_models.ipynb` notebook. 
  #### Vectorization:
  There are vectorization functions inside of the Python notebook that will run on the `data/fully_combined.csv` dataset. The vectorization process starts off by finding the 6,000 most common words within the `fully_combined.csv` dataset and then vectorizing the `fully_combined.csv` dataset based on this vocabulary. The vectorized dataset is then saved to `data/vectorized_most_common.csv`. 
  #### Results:
  The classification results for each of the sklearn models is combined into a single CSV file and saved under `ensemble/sklearn_results.csv`.
  
  ---

  ### Neural Network
  #### Setup: 
  In order to run the Neural Network notebook, ensure that the full data: `data/fully_combined_data.csv` is uploaded to your drive. Connect to your drive as shown in the first few cells and store the path to the file in the `RAW_DATA_FILE` constant. 
  
  #### Vectorization:
  First, set the `TRAIN_TEST_DIR` constant to a directory in your google drive where you want to store the vectorized train and test data for model training.
  Run through the entire **Data Preparation** section of the notebook to generate vectorized data by the bag of words technique.
  
  #### Results:
  First, set the `DATA_DIR` constant to the value of `TRAIN_TEST_DIR` or the location of the vectorized and split data generated in the _Data Preparation_ section of the notebook.
  Then, run through the section **Model Preparation** to train the model on the training data. If you would like to download a csv of the full data labeled by the neural network then run the **Get Labeling for Data** section. Finally some data statics and some basic additional analysis is included.
  
  ---

  ### Bidirectional LSTM
  In order to run the Bidirectional LSTM notebook, ensure that the data_file filepath is set to the complete dataset. 
  Due to dataset size, this notebook is configured to run in google colab. There are cells in place to handle mounting the drive and accessing the relevant data file if it exists.

  #### Pretrained word embeddings:
  Execution of the notebook cells will download and unzip the pretrained Glove embedding. 
  Stepping through to the end will unpack the dataset and store in the local variables, run the training process, and output the classifications of the model as a csv. 
  This classification output is an input for the ensemble notebook.
  
  ---
