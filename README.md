# 6220-spam-detection-project
Welcome to our spam detection ensemble repository! 

# Repository Structure

> -- analysis<br>
> -- code<br>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -- models<br>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -- preprocess<br>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -- Ensemble.ipynb<br>
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

  ### Preprocessing and combining

  ## Models

  ### sklearn Models
  #### Vectorization
  
  ---

  ### Neural Network
  Vectorization
  
  ---

  ### Bidirectional LSTM
  In order to run the Bidirectional LSTM notebook, ensure that the data_file filepath is set to the complete dataset. 
  Due to dataset size, this notebook is configured to run in google colab. There are cells in place to handle mounting the drive and accessing the relevant data file if it exists.

  #### Pretrained word embeddings:
  Execution of the notebook cells will download and unzip the pretrained Glove embedding. 
  Stepping through to the end will unpack the dataset and store in the local variables, run the training process, and output the classifications of the model as a csv. 
  This classification output is an input for the ensemble notebook.
  
  ---
