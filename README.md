# Welcome to Vijoy's Repository!

## I'm Passionate about data (small, big, slow, fast) and the insights from data that drive business outcomes

### Udacity Azure Machine Learning Engineer Scholarship - Optimizing A Pipline in Azure

- Build and optimize an Azure ML model by training two models, one using Scikit-learn algorithm connected to Azure HyperDrive (a hyperparameter tuning engine), and the other, using Azure AutoML automated training process. The optimized or best performing model is chosen from the two approaches. The workflow is as shown below

![image](https://user-images.githubusercontent.com/81923226/114083850-22882f00-98cd-11eb-8ea7-6a873789bd7c.png)

- The Bank Marketing dataset from UCI ML Repository was used to train the two models.
- Tool: Azure ML Studio, Azure Python SDK, Jupyter Notebook

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
                                     
### Results:

1. VotingEnsemble is chosen as the best model by AutoML for the classification problem, achievening an accuracy of 0.914. 
2. By using Azure's Hyperdrive service, we were able to tune two hyper-parameters (Max Iterators and LR Coefficient), after tuning these over various iterations. It was determined that even after the best chosen parameters. Logistic Regression was able to achieve an accuracy of 0.9096.

3. Azure AutoML's VotingEnsemble model clearly outperforms the model achieved by using Hyperdrive.




#### Screenshots as below

![image](https://user-images.githubusercontent.com/81923226/114142879-146bfa00-9931-11eb-8a86-01a957e212c5.png)

![image](https://user-images.githubusercontent.com/81923226/114142934-23eb4300-9931-11eb-98ec-139982eb4b81.png)

![image](https://user-images.githubusercontent.com/81923226/114142748-f0a8b400-9930-11eb-96b3-1b1f82c20f21.png)

![image](https://user-images.githubusercontent.com/81923226/114142777-f9998580-9930-11eb-8205-97fda4bc8d7f.png)



![image](https://user-images.githubusercontent.com/81923226/114142804-0027fd00-9931-11eb-88f0-91689b53f284.png)

![image](https://user-images.githubusercontent.com/81923226/114142853-0ae29200-9931-11eb-9bd2-2b2ab117d765.png)



