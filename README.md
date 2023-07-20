# Module 12 Report Template

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* In this project, I use multiple techniques to train and evaluate supervised machine learning models based on loan risk.
*  We use a dataset of historical lending activity from a peer-to-peer lending services company to build models that can identify the creditworthiness of borrowers.
* Within the data, we have the following variables, to use when training the models on the borrowers credit rating:
![df_screenshot](https://github.com/eemahazion/credit-risk-classification/assets/124013416/ffbd38b4-23ca-494c-aed0-60611f0cc489)

* From these data points, we remove the loan_status, as that is the thing we are trying to predict with the model. Whether a loan is risky (1) or healthy (0). We then split the data into testing and training data using sklearn model's train_test_split function. Once this is done we use the LogisticRegression algorithm and fit this onto the training data. Once the model is trained on the data we can implement this onto the testing data's independent variables(x data/x axis). The outputs we will then compare to the test data to see the accuracy of the LogisticRegression model.

## Results
* Once looking at the output of the models accuracy/results score we noticed some issues:![first classification report](https://github.com/eemahazion/credit-risk-classification/assets/124013416/307e0509-57c8-4eaf-94db-11dd7f1579fa)

*The .91 recall indicates that this model was only able to call out 91% of the risky loans as risky, meaning 9% of risky loans will be "approved" as healthy, which wouldnt be good for a loan company.
*Another thing that stands out is the precision of .85 or 85%, meaning that 15% of the loans called risky were actually healthy. Keep in mind there were only 619 loans called risky in this analysis.
*My observation is that this model could be better, and when looking at the data, we see that it is in fact imbalanced, with most of the loans being healthy. 76,036/77,536 loans were healthy. It would make for a more accurate model to have more examples of bad loans to train the LogisticRegression algorithm on.
  Hence we import the RandomOverSampler class from the imblearn python library. This evens out the data to now show 56,271 risky and healthy loans each, perfectly balanced.
  
* Once we run the same LogisticRegression algorithm on this new balanced data we did in fact see that the mode was actually better than the original results:
  
  ![second classification report](https://github.com/eemahazion/credit-risk-classification/assets/124013416/43f9aaaf-8986-44f9-8b8e-3aedabe46104)

*We see an improvement in that we capture almost of the risky loans (99% recall) despite slightly lower accuracy and having some healthy loans captured in the risky loan bucket.
*As for the healthy loans, it remains accurate as before.


## Summary
In conclusion the model becomes better as we have a more balanced data set, as that allows the model to train itself on the different outcomes and scenarios evenly, in **human terms**.

