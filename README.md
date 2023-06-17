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

# Findings
The results seem fairly similar. However, the lack of the response variable in the testing dataset used by the author, creates difficulty in creating any comparison metrics.

## Drawbacks and Limitations

The dataset is in a format which commonly used in data science competitions, in which there is a [train](input/train.csv) and [test](input/test.csv) data. The test data which is used only for the purpose of generating the final predictions after building the model, these predictions are then used by the evaluator to compute the metrics for the performance of the model.

However, in the original code of the author there is many unnecessary redundtant work that done such as;

1. Combining the the test and the trainig data. \
- This combinantion was unnecessary knowing the test data does not have any response variable. The author should have the exploratory data analysis and modeling focussing only on the train dataset.
2. Lack of traing the model
- A common approach in these type of datasets is to have some split within the training data, some chunck to be used for traing and another for testing(pre testing), the testing part in this case can be used to generate many performance metrices that would give the author a good perception on how his model is actually performing, submitting final predictions without prior knowlege of your model performance seems like a self defeting approach.
- Moreveover, the lack of pre-testing makes difficult the replication of the results by other authors.

## Conclusion
