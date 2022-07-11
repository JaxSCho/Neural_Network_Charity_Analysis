# Neural Network Charity Analysis

## Project Overview 

To help Alphabet Soup predict where to make investments, we used the features in the provided dataset to help Beks create a binary classifier that is capable of predicting whether applicants will be successful if funded by the foundation. The provided CSV dataset containing more than 34,000 organizations that have received funding from Alphabet Soup over the years from Alphabet Soup’s business team. 

## Results

### Data Processing

With this dataset are a number of columns that capture metadata for more than 34,000 organizations that recieved funding from Alphabet Soup over the years. We have preprocessed the dataset in order to compile, train, and evaluate the neural network model.

- **Target variable for model:** Effective use of money flag (IS_SUCCESSFUL)
- **Feature variables for model:** 
    - Alphabet Soup application type (APPLICATION_TYPE)
    - Affiliated sector of industry (AFFILIATION)
    - Government organization classification (CLASSIFICATION)
    - Use case for funding (USE_CASE)
    - Organization type (ORGANIZATION)
    - Active status (STATUS) 
    - Income classification (INCOME_AMT)
    - Special consideration for application (SPECIAL_CONSIDERATIONS)
    - Funding amount requested (ASK_AMT)
- **Variables that were removed from the input data that were neither targets nor features:** Identification columns (EIN and NAME)

### Compiling, Training, and Evaluating the Model

We used typical typical binary classifier parameters for our deep learning model:

- Our first hidden layer will have an input_dim equal to the length of the scaled feature data X (43), 29 neuron units, and will use the relu activation function.
- Our second hidden layer will have 14 neuron units and also will use the relu activation function.
- Our output layer uses the signmoid activation function to help us predict the probability an application is successful (i.e., uses the loan money effectively).
- The loss function should be binary_crossentropy, using the adam optimizer.

Since we didn't want our deeper layers to overfit the input data, we did not use two to three times the number of neurons as the input variables as a general suggestion.

![image](https://user-images.githubusercontent.com/99936542/178182165-e003a563-ffb3-4dbd-ba74-9645b360baa8.png)

<b>Fig.1 - Deep Learning Model Summary </b> 

Looking at our deep learning model's performance metrics, the model was able to correctly identify if an Alphabet Soup-funded organization will be successful approximately 72.5% of the time. Therefore, the model was unable to achieve the target predictive accuracy of 75%. 

![image](https://user-images.githubusercontent.com/99936542/178182295-d2e57684-9e45-480e-bea5-9ee7266c4fd8.png)

<b>Fig.2 - Deep Learning Model Performance Metrics </b>

### Attempting to Optimize the Model

We took the following steps to try to increase our model performance:

1. We changed the cutoff point for APPLICATION_TYPE categorical variable based on the density plot to reduce the amount in the features dataset. We used the density plot to identify where counts "fall off" and set the threshold within this region. 

![image](https://user-images.githubusercontent.com/99936542/178187112-b50dbf3f-410c-420e-9d89-53d48cd59183.png)

<b>Fig.3 - APPLICATION_TYPE Density Plot </b>

According to the density plot above, the most common unique values have more than 5,000 instances within the dataset. Therefore, we can bucket any application type that appears fewer than 5,000 times in the dataset as "Other".

![image](https://user-images.githubusercontent.com/99936542/178187717-201f334e-7c42-45d9-9767-7475ec4e5d51.png)

<b>Fig.4 - Attempt 1 - Performance Metrics </b>

The model was able to correctly identify if an Alphabet Soup-funded organization will be successful approximately 70.6% of the time. Therefore, the model was still unable to achieve the target predictive accuracy of 75%.

2. Then, we added additional neurons were added to the first two hidden layers as well as an additional third hidden layer. We increased from 29 to 34 neurons for the first hidden layer and increased from 14 to 17 neurons for the second. The additional third hidden layer had 8 neurons.

![image](https://user-images.githubusercontent.com/99936542/178187777-80f97b67-88e6-4a1c-b9e5-dd7115036068.png)

<b>Fig.5 - Attempt 2 - Performance Metrics </b>

The model was able to correctly identify if an Alphabet Soup-funded organization will be successful approximately 70.8% of the time. Therefore, the model was still unable to achieve the target predictive accuracy of 75%.

3. For our third attempt, the activation function of hidden layers was changed for optimization from relu to tanh for all hidden layers.

![image](https://user-images.githubusercontent.com/99936542/178187812-63ddc2f2-c86f-44e4-a01a-94e97537b8d8.png)

<b>Fig.6 - Attempt 3 - Performance Metrics </b>

The model was able to correctly identify if an Alphabet Soup-funded organization will be successful approximately 70.6% of the time. Therefore, the model was still unable to achieve the target predictive accuracy of 75%.

## Summary

Overall, the deep learning model generated a moderately strong binary classifier capable of predicting whether applicants will be successful if funded by Alphabet Soup. The model was able to correctly identify if an Alphabet Soup-funded organization will be successful approximately 72.5% of the time. After several attempts to optimize the model, we were unable to increase to over a target predictive accuracy of 75%. 

It may be worthwhile to explore another supervised machine learning model could solve this classification problem. Random forest models are generally able to achieve comparable predictive accuracy on large tabular data with less code and faster performance than neural networks. With more than 34,000 organizations in this tabular dataset, an ensemble-based random forest model may be favorable starting point.