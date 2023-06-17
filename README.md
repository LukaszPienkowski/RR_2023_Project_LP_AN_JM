# Project Description

This repository contains the code for the **Reproducible Research** project, where we try to port R code into Python and make the process reproducible.  
 This README.md file provides instructions on how to replicate the project environment and general findings.

# Replicating the Environment

To replicate the project environment, please follow the steps below:

1. Clone the repository to your local machine using the following command:

    ```
    git clone https://github.com/LukaszPienkowski/RR_2023_Project_LP_AN_JM.git
    ```

2. Create and activate a virtual environment for the project. You can use `venv` or any other virtual environment tool of your choice. Here's an example using `venv`:

    ```
    python3 -m venv myenv
    ```

3. Activate the virtual environment.

- For Windows (Command Prompt):
  ```
  myenv\Scripts\activate.bat
  ```

- For Unix or Linux:
  ```
  source myenv/bin/activate
  ```

4. Install the required dependencies by running the following command:

    ```
    pip install -r requirements.txt
    ```
# Discussion about the Project

## Findings
The results seem fairly similar. However, the lack of any evaluation metric makes it difficult to compare our approach with original approach fully.  
Author also did not set any random seed, making the code dependent on pseudorandom numbers generated in each session, thus making process non-reproducible.  
Code is full of redundant code and contradictory actions. Our approach is simplified and can be reproduced.

## Drawbacks and Limitations

The dataset is in a format which commonly used in data science competitions, in which there is a [train](input/train.csv) and [test](input/test.csv) data. The test data which is used only for the purpose of generating the final predictions after building the model, these predictions are then used by the evaluator to compute the metrics for the performance of the model.

However, in the original code of the author there is many unnecessary redundant such as:

1. Combining the the test and the trainig data: 
- This combinantion was unnecessary knowing the test data does not have any response variable. The author should have the exploratory data analysis and modeling focussing only on the train dataset.

2. Lack of model evaluation:
- A common approach in these type of datasets is to have some split within the training data, some chunck to be used for training and another for evaluating, which can be used to generate many performance metrices that would give the author a good perception on how his model is actually performing, submitting final predictions without prior knowlege of your model performance seems like a self defeting approach.
- Moreveover, the lack of pre-testing makes difficult the replication of the results by other authors.

3. Relying on `RandomForest` model of missing data imputation:  
- Model is used for imputation, but no random seed is set, resulting in different results each time.

4. Statistical flaws, such as:  
- imputing a variable with 70% missing values,
- leaving legacy columns after feature extraction/engineering,

## Conclusion

Our changes were not drastic, it was only simplifying and unification of the whole procedure, adding a classification metric and setting random state in every method relying on pseudo-random numbers.  
It was just enough to make it that **Research** truly **Reproducible**.