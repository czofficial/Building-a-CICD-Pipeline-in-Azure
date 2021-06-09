# Building a CI/CD Pipeline in Azure

* [Overview](#overview)
* [Instructions](#instructions)

## Overview
This project is part of the Udacity Cloud DevOps using Microsoft Azure Nanodegree Program.

The first part of this project can be found in the following [GitHub Repo](https://github.com/czofficial/Udacity-Cloud-DevOps-using-Microsoft-Azure-Nanodegree-Program/tree/master/C2-AgileDevelopmentwithAzure).

## Instructions
### Create GitHub Actions Workflow
1. Go to your GitHub Repo
2. Got to Actions
3. Go to 'New workflow' and 'set up a new workflow yourself'
4. Configure your YML file as such:
```
name: Python application test with Github Actions

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Set up Python 3.5
      uses: actions/setup-python@v1
      with:
        python-version: 3.5
    - name: Install dependencies
      run: |
        make install
    - name: Lint with pylint
      run: |
        make lint
    - name: Test with pytest
      run: |
        make test
```
5. Verify your successfull run in 'All Workflows'

A prerequisite for having a successfull CI workflow in GitHub Actions is a 'Makefile' and a 'requirements.txt'. In this project, I will only use pylint for code testing, not pytest. In the requirements file, you need to state the python libraries that are needed to get the Flask web app running. With this in place, a new push to the GitHub repo will automatically trigger the CI workflow in GitHub Actions (testing the app.py file). A pylint score below 10 will result in a failed CI build. That's the sign to refactor your code according to the pylint standards.


### Deploy the Flask Web App in Azure Cloud Shell
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
5. Install dependencies (pip & requirements) in the Python virtual environment and run CI part (only linting).
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

### Deploy the Flask Web App to Azure App Service
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
One of the enhancements you can do is setting up the whole CI/CD workflow in Azure DevOps Repo & Azure DevOps Pipelines alone, leaving out GitHub and GitHub Actions completely. Personally, I found it a bit confusing doing the CI part in GitHub (Actions) and the CD part in Azure DevOps (Pipelines).