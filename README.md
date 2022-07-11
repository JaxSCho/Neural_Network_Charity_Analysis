# Neural Network Charity Analysis

## Project Overview 

Beks has come a long way since her first day at that boot camp five years ago—and since earlier this week, when she started learning about neural networks! Now, she is finally ready to put her skills to work to help the foundation predict where to make investments.

With your knowledge of machine learning and neural networks, you’ll use the features in the provided dataset to help Beks create a binary classifier that is capable of predicting whether applicants will be successful if funded by Alphabet Soup.

From Alphabet Soup’s business team, Beks received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as the following:

## Results

### Data Processing

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

- Our first hidden layer will have an input_dim equal to the length of the scaled feature data X , 29 neuron units, and will use the relu activation function.
- Our second hidden layer will have 14 neuron units and also will use the relu activation function.
- Our output layer uses the signmoid activation function to help us predict the probability an application is successful (i.e., uses the loan money effectively).
- The loss function should be binary_crossentropy, using the adam optimizer.

We didn't want our deeper layers to overfit the input data and therefore, we did not use two to three times the number of neurons as the input variables.

![image](https://user-images.githubusercontent.com/99936542/178182165-e003a563-ffb3-4dbd-ba74-9645b360baa8.png)

<b>Fig.1 - Deep Learning Model Summary </b> 

Looking at our deep learning model's performance metrics, the model was able to correctly identify if an Alphabet Soup-funded organization will be successful approximately 72.5% of the time. Therefore, the model was unable to achieve the target predictive accuracy of 75%. 

![image](https://user-images.githubusercontent.com/99936542/178182295-d2e57684-9e45-480e-bea5-9ee7266c4fd8.png)

<b>Fig.2 - Deep Learning Model Performance Metrics </b>

### Attempting to Optimize the Model

We took the following steps to try to increase model performance:

1. We changed the cutoff point for APPLICATION_TYPE and CLASSIFICATION categorical variables based on the density plot.
    - APPLICATION_TYPE
    
![image](https://user-images.githubusercontent.com/99936542/178182397-f810a99d-df8d-4c47-86b3-a3bc1318eafe.png)

2. Additional neurons were added to the hidden layers as well as one additional hidden layer was added

![image](https://user-images.githubusercontent.com/99936542/178182473-c8c011ce-acc5-4d9e-bf02-0b792098e840.png)

3. The activation function of hidden layers was changed for optimization (relu to tanh)

![image](https://user-images.githubusercontent.com/99936542/178182563-d5bf2f9d-1484-4976-b40a-cbbe84565504.png)

## Summary

Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and explain your recommendation.