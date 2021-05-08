# Challenge 19: Neural Network Charity Analysis

## Overview of Neural Network Charity Analysis

The purpose of the project is to analyse a dataset containing various measures on 34,000 organizations that have been funded by Alphabet Soup. Using neural network analysis, a model will be created to attempt to predict if future applicants would use the funds effectively.  
## Neural Network Charity Analysis Results

The steps for the neural network analysis are:
1. Data Preprocessing 
2. Neural Network Modeling
3. Model Evaluation
### Data Preprocessing

- The target for the model is "IS_SUCCESSFUL" column
- The following columns are the features: 'APPLICATION_TYPE', 'AFFILIATION', 'CLASSIFICATION', 'USE_CASE', 'ORGANIZATION', 'STATUS', 'INCOME_AMT', 'SPECIAL_CONSIDERATIONS', 'ASK_AMT'
- "EIN" and "NAME" columns dropped since they contained unique values
- "APPLICATION_TYPE" and "CLASSIFICATION" columns were binned to reduce the number of distinct values
- Non-numeric columns were converted using OneHotEncoder
- Data was split into features and target then into training and testing datasets
- Data was scaled using StandardScaler
### Compiling, Training, and Evaluating the Model

The neural network model has 2 hidden layers and an output layer. The model weights were saved every 5 epochs during the fit operation, and the final model was saved after 100 epochs. [AlphabetSoupCharity.ipynb](https://github.com/Hala-INTJ/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity.ipynb)

| Layer | No. of Units | Activation Function |
| --- | --- | --- |
| First Layer | 80 | relu |
| Second Layer | 30 | relu|
| Output Layer | 1 | Sigmoid | 


The accuracy after evaluating this model is 72.63%
![](https://github.com/Hala-INTJ/Neural_Network_Charity_Analysis/blob/main/model_accuracy.png)

### Attempts to improve the model accuracy to over 75%

Optimization was approached by making small changes to the overall preprocessing and model creation. The goal was to ensure that if an accuracy improvement was achieved, it would not be negated by a separate concurrent change. 

| Attempt | Changes | Accuracy | File | 
| --- | --- | --- | --- |
| 1 | Added a third layer and set nodes per layer to 2/3 of inputs plus 1 | 0.7254 | [AlphabetSoupCharity-Optimization_Attempt1.ipynb](https://github.com/Hala-INTJ/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity-Optimization_Attempt1.ipynb) |
| 2 | Changed the activation function from relu to tanh | 0.7258 | [AlphabetSoupCharity-Optimization_Attempt2.ipynb](https://github.com/Hala-INTJ/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity-Optimization_Attempt2.ipynb) |
| 3 | Binned "ASK_AMT" column and dropped "STATUS" and "SPECIAL_CONSIDERATIONS" columns | 0.7255 | [AlphabetSoupCharity-Optimization_Attempt3.ipynb](https://github.com/Hala-INTJ/Neural_Network_Charity_Analysis/blob/main/AlphabetSoupCharity-Optimization_Attempt3.ipynb) |

## Neural Network Charity Analysis Summary

We were unsuccessful at achieving an accuracy of 75% or higher. After further analysis of the dataset features, there are several features that have a small number of outliers. Further investigation may indicate that records with an outlier with one feature also have outlier values for other features, and removing these records may result in a more accurate model. Exploring alternative supervised models such as BalancedRandomForestClassifier and EasyEnsembleClassifier may provide better results.
