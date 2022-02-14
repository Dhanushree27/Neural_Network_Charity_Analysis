# Charity Analysis - Neural Network

![image](https://user-images.githubusercontent.com/90650562/153954368-0175d49e-e5ed-45af-ad73-d5a533e3e040.png)

## Overview
This analysis was initiated with the intention to identify charities to invest in, based on whether the applicant will be successful if funded by the foundation. The approach taken was to create a binary classifier using deep learning techniques on a dataset containing 34000 datapoints, which possesed information on the charity and whether it succeeded or not. 

**Preprocessing**
- Irrelevant fields were removed
- Application Type and Classification which had more than 10 unique values were bucketed and binned
- Filtered data with status '1'
- Text fields were encoded using 'OneHotEncoder'
- The data was split into Features and Target
- The features and target were then split into training and testing datasets
- The feature dataset was scaled using 'StandardScaler'

**Initial Model**
Model:Keras sequential model 
Hidden Layers: 2 layers (80 and 30 perceptrons), using 'relu' activation 
Output Layer: 'sigmoid' activation
Optimizer: adam
Loss: binary crossentropy
Metric: accuracy

## Results

### Data Preprocessing

**The Target**
- Is Successful

**Features taken into consideration**
- Application type
- Affiliation
- Classification
- Use Case
- Organization
- Ask Amt
- Income Amt

**Irrelevant fields**
- Name - Identifier. Therefore, would not have served a purpose
- EIN - Identifier. Therefore, would not have served a purpose
- Status - Only 5 were not active. Data was filtered to active data. Also, cross checking with feature importances of random forest revealed low importance (Removed as part of optimization)
- Special Considerations - Limited difference. Cross checking with feature importances of random forest revealed low importance (Removed as part of optimization)

### Compiling, Training, and Evaluating the Model

**How many neurons, layers, and activation functions did you select for your neural network model, and why?**
The initial model resulted in an accuracy score of 72.8%. In an attempt to improve the accuracy score, different combination of neurons, hidden layers, and activation function were used. The analysis was documented in : [Feature Analysis](https://github.com/Dhanushree27/Neural_Network_Charity_Analysis/blob/main/Learning_Models.xlsx)

Final Model:
Hidden Layer 1: 80, 'relu' activation
Hidden Layer 2: 30, 'relu' activation
Hidden Layer 3: 10, 'relu' activation

It was observed that increasing the neurons did not improve the accuracy considerably. The final accuracy reached was 73.46%

Though similar improvement was observed with 'sigmoid' activation function, 'relu' was used since it is suggested activation method for multilayer perceptron and also because it is not affected by the vanishing gradients problem

**Were you able to achieve the target model performance?**
Despite more than 20 attempts to optimize the model by removing noise, changing the number of neurons, layers and activation function, the model was unable to achieve accuracy more than 73.4%. The combinations attempted can be found in [Feature Analysis](https://github.com/Dhanushree27/Neural_Network_Charity_Analysis/blob/main/Learning_Models.xlsx)

**What steps did you take to try and increase model performance?**
- Two of the input dimensions (status, special consideration) were removed. In the case of status, data was filtered to contain active status. The fields were removed after observing the value counts, and the feature importance from RFC model
- Neurons: Neurons were increased as well as decreased in an attempt to improve accuracy
- Hidden Layers: Layers were increases to 3 in an attempt to increse accuracy
- Activation function: Different combinations of relu, tanh and sigmoid were attempted

## Summary
The final model using 3 hidden layers with 'relu' activation was able to achieve accuracy of 73.4%. Despite different combinations in the model, the accuracy fluctuated between 72.8 to 73.4%. The 'sigmoid' activation model also rivaled in performance to the 'relu' activation model.

Attempting to classify the data using RandomForestClassifier and LogisticRegression resulted in accuracy scores of 70.2% and 72.2% respectively, suggesting that the deep learning model has performed better in this case. Further attempts can be made to tune the deep learning model to achieve a better accuracy score.





