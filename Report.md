# Alphabet Soup Charity Report
The goal was to train a neural network to predict with 75% or higher accuracy which charities will be successful based on the dataset at https://static.bc-edx.com/data/dl-1-2/m21/lms/starter/charity_data.csv.


## Target and Features
The target variable is the IS_SUCCESSFUL column.

The feature variables are:
- APPLICATION_TYPE
- AFFILIATION
- CLASSIFICATION
- USE_CASE
- ORGANIZATION
- STATUS
- INCOME_AMT	
- ASK_AMT

These variables were removed as they were not targets or features:
- EIN
- NAME
- SPECIAL_CONSIDERATIONS

## Optimization and Results
When optimizing I first tried seeing what features I could drop and if they had any effect on accuracy, then I tried several different bin sizes on APPLICATION_TYPE and CLASSIFICATION. I also tried everything from 1 to 3 hidden layers with different numbers of neurons in the different layers, as well as different activation functions and different numbers of epochs. I found lots of different ways to get between 69% and 71%, but could not get up to 75%.

Because I could not get beyond 70% accuracy I decided to improve processing time and see how I could reduce the number of neurons and layers while still maintaining 70%. I finally stuck with limiting APPLICATION_TYPES to 9 bins (everything under 500 goes in Other) and limiting CLASSIFICATION to 6 bins (everything under 1000 goes in Other). Between this and the data in the other columns that gives 41 input dimensions. I then only used 1 relu hidden layer with 20 neurons and a sigmoid output layer. I saw no benefits when trying other activation functions. This was able to return a model with 70% accuracy in 25 epochs. My next step if I were to spend more time on this would be to experiment with binning the ASK_AMT column and see if that has any impact on the accuracy.