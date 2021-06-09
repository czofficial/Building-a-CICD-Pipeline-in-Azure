# Building a CI/CD Pipeline in Azure

* [Overview](#overview)
* [Instructions](#instructions)

## Overview
This project is part of the Udacity Cloud DevOps using Microsoft Azure Nanodegree Program.

The first part of this project can be found in the following [GitHub Repo](https://github.com/czofficial/Udacity-Cloud-DevOps-using-Microsoft-Azure-Nanodegree-Program/tree/master/C2-AgileDevelopmentwithAzure).

## Instructions
### Deploy the Flask web app in Azure Cloud Shell
1. Launch an Azure Cloud Shell Environment, create ssh keys and upload them into your GitHub account.
````
ssh-keygen -t rsa
````
2. Clone the GitHub project into your Azure Cloud Shell environment.
````
git clone git@github.com:czofficial/Building-a-CICD-Pipeline-in-Azure.git
````
3. CD into your project directory and create the Python virtual environment via the Makefile.
```
make setup
```
4. Activate the Python virtual environment.
```
source ~/.udacity-devops/bin/activate
```
5. Install dependencies (pip & requirements) in the Python virtual environment and run CI part (only installing and linting).
```
make all
```
6. Start Flask web app
```
python app.py
```
7. Open second Azure Cloud Shell terminal and test the app by making a prediction
```
./make_prediction.sh
```

Successfull output:
![cloud-shell-prediction](./screenshots/cloud-shell_prediction.png)

### Deploy the App to Azure App Service
Text

<TODO:  Instructions for running the Python project.  How could a user with no context run this project without asking you for any help.  Include screenshots with explicit steps to create that work. Be sure to at least include the following screenshots:

* Project running on Azure App Service

* Project cloned into Azure Cloud Shell

* Passing tests that are displayed after running the `make all` command from the `Makefile`

* Output of a test run

* Successful deploy of the project in Azure Pipelines.  [Note the official documentation should be referred to and double checked as you setup CI/CD](https://docs.microsoft.com/en-us/azure/devops/pipelines/ecosystems/python-webapp?view=azure-devops).

* Running Azure App Service from Azure Pipelines automatic deployment

* Successful prediction from deployed flask app in Azure Cloud Shell.  [Use this file as a template for the deployed prediction](https://github.com/udacity/nd082-Azure-Cloud-DevOps-Starter-Code/blob/master/C2-AgileDevelopmentwithAzure/project/starter_files/flask-sklearn/make_predict_azure_app.sh).
The output should look similar to this:

```bash
udacity@Azure:~$ ./make_predict_azure_app.sh
Port: 443
{"prediction":[20.35373177134412]}
```

* Output of streamed log files from deployed application
> 

## Enhancements
Text