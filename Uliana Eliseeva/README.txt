This submission includes files:

1. NN_postagger.ipynb
2. model_parameters_tagger.pt
3. UD_German-GSD-master
4. README.txt
5. Report.pdf


Python version is 3.9.

To reproduce the training, the script NN_postagger.ipynb should reside in the folder with data.py script and data folder UD_German-GSD-master.
The NN_postagger.ipynb is broken down into 10 segments: 

1. DATA PREP - creates data loaders for training, testing, development data sets; creates embeddings for words.
2. SAMPLE DATA EXPLORATION - gives a peak into data structure
3. MODEL CLASS - creates a model class with layers and forward function
4. MODEL INITIALIZATION - defines model architecture parameters, initializes the tagger model
5. HYPERPARAMETERS - defines hyperparameters such as epochs, learning rate, loss function and optimizer
6. TRAINING FUNCTION - training loop for each epoch
7. EVALUATION FUNCTION - evaluates a trained model on each of the passed data sets
8. MODEL TRAINING - trains an initialized model 
9. EVALUATION ON TEST DATA
10. SAVE AND LOAD MODEL PARAMS - saves trained model parameters and loads them as a tagger model

  
