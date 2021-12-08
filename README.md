# 6220-spam-detection-project
Welcome to our spam detection ensemble repository! 

# Repository Structure

# How to run through the full pipeline

  ## Data

  ### Preprocessing and combining

  ## Models

  ### sklearn Models
  Vectorization
  
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
