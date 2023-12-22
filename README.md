

Environment:
Fork and clone the repository 'Project-Build-an-ML-Pipeline-Starter.git',
Create a Conda environment,
Log into Weights & Biases with API key,  

Download Data:

Data Cleaning:
Use the 'basic cleaning' step that cleans the sample.csv artifact and creates a new clean_sample.csv with the cleaned data.
Expected results:
![image](https://github.com/JulieCarpenter/Project-Build-an-ML-Pipeline-Starter/assets/108777878/a233b054-63f9-4730-b758-4b1d14b385ac)

Data Check:
Test row count - Check that row count is between 15,000 and 1,000,000
Test price range - Check that prices in data are within the expected range using min_price and max_price.
Expected results:
![image](https://github.com/JulieCarpenter/Project-Build-an-ML-Pipeline-Starter/assets/108777878/b9bceb11-e291-4d2d-924d-7aaf5a2dbc17)

Initial Training:
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
    -P hydra_options="modeling.random_forest.max_depth=10,50 modeling.random_forest.n_estimators=100,200 -m"
   Expected results:
   



