# Video-Streaming-Churn-Prediction-Project
Project for predicting user subscription churn on video streaming service.
Video streaming provider has asked me to build a machine-learning model to predict if the user will continue his subscription to the video streaming service.
I was provided with a dataset containing a sample of subscriptions that were initiated and snapshotted at a particular date before the subscription was canceled. Subscription cancellation can happen for a multitude of reasons, including:
1. The customer completes all the content he was interested in and no longer needs the subscription.
2. The customer finds himself to be too busy and cancels his subscription until a later time.
3. The customer determines that the streaming service is not the best fit for him, so he cancels and looks for something better suited.
Regardless of the reason, the video streaming company has a vested interest in understanding the likelihood of each individual customer to churn in their subscription so that resources can be allocated appropriately to support customers. In this challenge, I was using my machine learning toolkit to do just that!

## Dataset description
The provided dataset has one row of data for each subscriber and it is divided into train and test sets.
The training set contains 70% of the overall sample (243,787 subscriptions and importantly, will reveal whether or not the subscription was continued into the next month (the “ground truth”).
The testing dataset contains the same information about the remaining segment of the overall sample (104,480 subscriptions) but does not disclose the “ground truth” for each subscription. The goal of this project is to predict this outcome!
Both train and test datasets contain one row for each unique subscription. For each subscription, a single observation (CustomerID) is included during which the subscription was active.
In addition to this identifier column, the training dataset also contains the task's target label, a binary column Churn.
In addition to that column, both datasets have an identical set of features that can be used to train the model to make predictions.

## Data Loading and Preparation
I imported the necessary Python modules and I loaded the datasets.
After that, I explored, cleaned, and validated the data.
The datasets contain 6 features with float, 4 features with integer, and 10 features with object type.
10 float and integer features are continuous, and 10 object features are categorical.
Taking into account this dataset structure, I chose tree-based models, especially CatBoost which can effectively use the categorical features.

## Feature Engineering
During this phase, I engineered new interaction features among the continuous features and their interaction with user churn.
Next, I checked the churn among all the categorical features' values to find some correlation with user churn.

## Correlation among features
By using the correlation matrix and Pearson correlation method, I plotted a correlation heatmap.
From the heatmap, I identified 4 interaction features highly correlated with other features. No matter that tree-based models are resilient to multicollinearity, I dropped those features from the model.

## Numerical Features Scaling
Because of very different ranges of numerical features' values, it is recommended to scale the numerical features before training the chosen models. 

## Assigning the predictors and the target variable
I split the training set into training and validation sets in order to check the performance of the model on the validation set before the prediction on the test dataset. 

## Testing with different tree-based ML models
I conducted tests on three different tree-based ML models:
1. LightGBM,
2. XGBoost,
3. CatBoost, and
4. HistGradientBoost

I also conducted tests on ensemble 
