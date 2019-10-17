# DIFI Poc1: Classification of UNSPSC codes
 
## Overview of the notebooks in this repository
 * Analyse_wrong_predictions.ipynb: Simple notebook set up for analysing wrong predictions in a structured manner
 * Prepare_Transaction_data.ipynb: Contains the concatenation and preprocessing of the transaction data
 * Prepare_Catalog_data: Contains the preprocessing of the catalog data
 * Logistic_Regression_model.ipynb: Training and evaluation of Logistic Regression model. The logistic regression model showed some promise but was ultimately discarded for the BiLSTM model.
 * BiLSTM_model.ipynb : Training and evaluation of deep learning model. This is the main model and notebook of POC1
 
 
## Pre-requisites

Standard python environment with Numpy, Pandas, sklearn and Keras installed. The project was developed using python 3.6/3.7 and a gpu enabled TensorFlow backend for Keras


## Additional notes

### Tokenizer
The BiLSTM model will fit a "tokenizer" on the training data. This is needed for tokenizing new sentences/descriptions into the format the trained model expects. The notebook will store the tokenizer in the current working directory during each training of the model. 

### Business codes
We also need to store the mapping between business codes (næringskode) and embedding index in order to be able to add this information for future predictions. The notebook will also take care of storing this mapping during training. Note that while you don't have to add a business code when prediction, all evaluation has been based on providing one. In order to properly support unknown codes, you might want to train the model with a set of training samples without business codes. Unknown business codes have the mapping index 0 for all runs
