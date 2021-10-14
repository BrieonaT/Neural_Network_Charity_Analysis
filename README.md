
## Overview
Alphabet Soup is a philanthropic organization that serves to help fund organizations that protect the environment, improve the lives of people and unite the world. This analysis dives into given data to figure out which organizations are trustworthy to invest in and which are too high risk. The initial data hosts 34,000 different organizations that have been funded by Alphabet Soup in the past.

For clarification purposes, below are a list of column names and what they represent to the data:
- EIN and NAME—Identification columns
- APPLICATION_TYPE—Alphabet Soup application type
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special consideration for application
- ASK_AMT—Funding amount requested
- IS_SUCCESSFUL—Was the money used effectively


## Results

Data Preprocessing
- The target variable for this model is IS_SUCESSFUL
- The features for this model are APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, INCOME_AMT, SPECIAL_CONSIDERATIONS, and ASK_AMT
- EIN and NAME are not targets or features for this model, and should be removed for a cleaner result.

Compiling, Training, and Evaluating the Model
- The initial model contained 2 hidden models, one with 80 neurons and one with 30. Both of these hidden layers utilized using ReLU activation, along with a Sigmoid output layer. The use of a Sigmoid output layer comes with the fact that we want our output to be binary.
- The initial model did not reach target model performance, as it fell short at 60% accuracy. 
![InitialOutput](https://github.com/BrieonaT/Neural_Network_Charity_Analysis/blob/main/Resources/Images/initial_output.png)

- In subsequent models, various approaches were taken to improve performance.  In the first optimization attempt, the amount of neurons on hidden layers was increads, from 80 and 30 to 170 and 60, along with the activation was changed to tanh on both. The number of epochs was also changed, from 100 to 150. However, this did not help and actually decreased the success rate from 60% to 59%. In the second optimization attempt, the columns of USE_CASE and AFFILIATION were dropped, in order to see if that would reduce unnecessary noise on results and increase accuracy. In addition, the model was changed to three hidden layers, using respectively, 130, 90 and 50 neurons, along with keeping the ReLU activation. Alongside this, the epochs were increased to 200. Again, this optimization did not work,  and further decreased accuracy to 51%. The last optimization attempt kept columns the same, except for the dropped EIN and NAME columns, but again changed the model. This attempt saw an extra hidden layer added again, with respectively, 100, 30 and 20 neurons used. The activation was also changed to LeakyReLU and the epochs were increased again to 250. While performing better than the second attempt, it still failed to perform efficiently, clocking in at 53% accuracy.  


Optimization 1's results:

![Op1_Output](https://github.com/BrieonaT/Neural_Network_Charity_Analysis/blob/main/Resources/Images/optimization_output_1.png)

Optimization 2's results:

![Op2_Output](https://github.com/BrieonaT/Neural_Network_Charity_Analysis/blob/main/Resources/Images/optimization_output_2.png)

Optimization 3's results:

![Op3_Output](https://github.com/BrieonaT/Neural_Network_Charity_Analysis/blob/main/Resources/Images/optimization_output_3.png)



## Summary
In conclusion, none of the models reached the desired 75% accuracy and fell short by 15% or more each time. For this specific analysis, it might be more optimal to try a different model. A suggested model that could be used is possibly logistic regression, as it predicts a binary outcome. In addition, you could still play around and mix and match different usages of neurons, number of layers, epochs and dropping certain columns and try your luck that way, however it might be more time consuming than it’s worth.
