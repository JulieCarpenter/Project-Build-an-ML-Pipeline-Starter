# Build an ML Pipeline for Short-Term Rental Prices in NYC
You are working for a property management company renting rooms and properties for short periods of time on various rental platforms. You need to estimate the typical price for a given property based on the price of similar properties. Your company receives new data in bulk every week. The model needs to be retrained with the same cadence, necessitating an end-to-end pipeline that can be reused.

## Links to github repository and Weights & Biases
https://github.com/JulieCarpenter/Project-Build-an-ML-Pipeline-Starter.

https://wandb.ai/123julz/nyc_airbnb?workspace=user-123julz

## Table of contents

- [Preliminary steps](#preliminary-steps)
  * [Fork the Starter Kit](#fork-the-starter-kit)
  * [Create environment](#create-environment)
  * [Create connection to Weights and Biases](#Create-connection-to-Weights-and-Biases)
- [The steps](#the-steps)

## Preliminary steps

### Fork the Starter kit
Fork and clone the repository 'Project-Build-an-ML-Pipeline-Starter.git'

### Create environment
Create a Conda environment in which to run the pipeline

### Create connection to Weights and Biases
Log into Weights & Biases with API key  

## The steps

#### Download Data: 
Save data as sample.csv to Weights & Biases

#### Data Cleaning:
Use the 'basic cleaning' step that cleans the sample.csv artifact and creates a new clean_sample.csv with the cleaned data.
Expected results:
![image](https://github.com/JulieCarpenter/Project-Build-an-ML-Pipeline-Starter/assets/108777878/a233b054-63f9-4730-b758-4b1d14b385ac)

#### Data Check:
Test row count - Check that row count is between 15,000 and 1,000,000
Test price range - Check that prices in data are within the expected range using min_price and max_price.
Expected results:
![image](https://github.com/JulieCarpenter/Project-Build-an-ML-Pipeline-Starter/assets/108777878/b9bceb11-e291-4d2d-924d-7aaf5a2dbc17)

#### Initial Training:
   Data Split:
   Split the data into training and testing datasets
   Expected results:
   ![image](https://github.com/JulieCarpenter/Project-Build-an-ML-Pipeline-Starter/assets/108777878/80bf50e1-fe16-4097-9ca7-e5ab2573afed)

   Train Random Forest:
   Run the training step with varying the hyperparameters of the Random Forest model. Note: this step may take a while to complete.
   This is done by exploiting the Hydra configuration system. It uses the multi-run feature (adding the -m option at the end of the hydra_options 
   specification), and sets the parameter modeling.random_forest.max_depth to 10, 50, and the modeling.random_forest.n_estimators to 100, 200.
     mlflow run . \
     -P steps=train_random_forest \
     -P hydra_options="modeling.random_forest.max_depth=10,50           modeling.random_forest.n_estimators=100,200 -m"
   Expected results:
   ![image](https://github.com/JulieCarpenter/Project-Build-an-ML-Pipeline-Starter/assets/108777878/355c82fb-5f8b-4db7-9dc5-4ad58d6649ef)
   ![image](https://github.com/JulieCarpenter/Project-Build-an-ML-Pipeline-Starter/assets/108777878/19cd82d4-b945-41bb-8314-c8168f40a442)

#### Model Selection and Test:
Select the best model and and tag it as 'prod.' This step is NOT run by default when you run the pipeline. In fact, it needs the manual step of promoting    a model to prod before it can complete successfully. 
   Test the model with the test dataset by runnung:
      mlflow run . -P steps=test_regression_model
   Expected results:
   ![image](https://github.com/JulieCarpenter/Project-Build-an-ML-Pipeline-Starter/assets/108777878/54aac75e-c113-47db-9e55-78668e12ba82)
   ![image](https://github.com/JulieCarpenter/Project-Build-an-ML-Pipeline-Starter/assets/108777878/321957f1-09cb-4bc2-a9d1-3a14f5f056fd)
   




   
    





