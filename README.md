# Welcome to Vijoy's Repository!

## I'm Passionate about data (small, big, slow, fast) and the insights from data that drive business outcomes

### Udacity Azure Machine Learning Engineer Scholarship - Optimizing A Pipline in Azure

- Build and optimize an Azure ML model by training two models, one using Scikit-learn algorithm connected to Azure HyperDrive (a hyperparameter tuning engine), and the other, using Azure AutoML automated training process. The optimized or best performing model is chosen from the two approaches. The workflow is as shown below

![image](https://user-images.githubusercontent.com/81923226/114083850-22882f00-98cd-11eb-8ea7-6a873789bd7c.png)

- The Bank Marketing dataset from UCI ML Repository was used to train the two models.
- Tool: Azure ML Studio, Azure Python SDK, Jupyter Notebook

### Pipeline Architecture
The pipeline architecture consists of a python training script (train.py), a tabular dataset downloaded from UCI ML Repository (Bank Marketing Data Set), a Scikit-learn Logistic Regression Algorithm connected to the Azure HyperDrive, a hyperparameter tuning engine, to produce a HyperDrive classifier. The training run was orchestrated by a Jupyter Notebook hosted on a compute instance.

Further, alternatively we use AutoML to generate a model and make comparisons with the Hyperdrive Pipeline.

### Dataset
The dataset was programmatically (using the train.py script) downloaded from the web, split into train and test sets using Sckit-learn train_test_split utility, with the link provided in the train.py script.

### Methodology

1. Connect to Udacity Resource Group & Workspace on the Azure Portal
2. Create a compute cluster, if the compute cluser already exists, then use that one. Else create a new one with vm_size = `STANDARD_D2_V2` having `max_nodes = 4`
3. Define Hyper-Parameter search space by RandomParameterSampling. Here we have considered two parameters - LR Coefficient and Max Iterations.
4. Specify a Bandit Policy and also create a SKLearn estimator with entry script `train.py`
5. Create a HyperDriveConfig using the estimator, hyperparameter sampler, and policy.
6. Run the hyperdrive config experiment and submit it.
7. Create an automl configuration model with primary metric as `accuracy` and `experiment_timeout_minutes=30`
8. Run the AutoML Experiment and Analyze Results.
9. Compare the accuracies of the two models and report your findings.


two input parameters C and max_iter (representing Regularization Strength and Max iterations respectively) were accepted as input to Scikit-Learn's logistic regression. These hyper parameters are tuned using Hyper drive and the best ones are chosen from the sample search space provided.

### Benefits of the parameter sampler chosen
The random parameter sampler for HyperDrive supports discrete and continuous hyperparameters, as well as early termination of low-performance runs. It is simple to use, eliminates bias and increases the accuracy of the model. 

### Benefits of the early stopping policy chosen
The early termination policy BanditPolicy for HyperDrive automatically terminates poorly performing runs and improves computational efficiency. It is based on slack factor/slack amount and evaluation interval and cancels runs where the primary metric is not within the specified slack factor/slack amount compared to the best performing run.
                                     
### Results:

1. VotingEnsemble is chosen as the best model by AutoML for the classification problem, achievening an accuracy of 0.914. 
2. By using Azure's Hyperdrive service, we were able to tune two hyper-parameters (Max Iterators and LR Coefficient), after tuning these over various iterations. It was determined that even after the best chosen parameters. Logistic Regression was able to achieve an accuracy of 0.9096.

3. Azure AutoML's VotingEnsemble model clearly outperforms the model achieved by using Hyperdrive.


## Areas of improvement for future experiments:

Apply model explainability & interpretability of AutoML on more complex and larger datasets, to gain speed and valuable insights in feature engineering, which can in turn be used to explain workings of models to the business-minded individuals and also to refine complex model accuracy

Experiment with different hyperparameter sampling methods like Bayesian sampling or GridSearchCV on the Scikit-learn LogicRegression model or other custom-coded machine learning models to understand more about Hyper-Parameter Tuning and obtain better results (may vary dataset to dataset)




#### Screenshots as below

![image](https://user-images.githubusercontent.com/81923226/114142879-146bfa00-9931-11eb-8a86-01a957e212c5.png)

![image](https://user-images.githubusercontent.com/81923226/114142934-23eb4300-9931-11eb-98ec-139982eb4b81.png)

![image](https://user-images.githubusercontent.com/81923226/114142748-f0a8b400-9930-11eb-96b3-1b1f82c20f21.png)

![image](https://user-images.githubusercontent.com/81923226/114142777-f9998580-9930-11eb-8205-97fda4bc8d7f.png)



![image](https://user-images.githubusercontent.com/81923226/114142804-0027fd00-9931-11eb-88f0-91689b53f284.png)

![image](https://user-images.githubusercontent.com/81923226/114142853-0ae29200-9931-11eb-9bd2-2b2ab117d765.png)

#### Compute Cluster Cleaned

![image](https://user-images.githubusercontent.com/81923226/114293361-13fb6c80-9ab3-11eb-8409-019df8f8950a.png)




