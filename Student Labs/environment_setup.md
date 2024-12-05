# Environment Setup

The main focus of this lab is to install the required dependencies and clone the project repository.

## Lab Objective

Students will use this lab as a first step to setup the GitHub repository, install certain required 
Python dependencies/packages such as Selenium and Playwright, and create the file directory for the test suite. 

## Prerequisites
- Familiarity with Python 3.8 or later, this lab will use Visual Studio Code for Windows as the IDE.
- Familiarity with Python virtual environments.
- Basic troubleshooting skills.

## Instructions

### Step 1: Environment Setup

1. Ensure Python 3.8 or later is installed on your machine.
2. Ensure node.js is installed on your machine, this is required in order for playwright to function properly. Follow the link to download and install
the latest version of [Node.js](https://nodejs.org/en)
4. Clone the project GitHub repository to your local machine.
5. Open the project. *This lab and subsequent labs use Visual Studio Code for Windows.*
6. Open a command prompt and do the following, this will install pipenv, install the required
   dependencies/packages, and activate a virtual environment
   
```bash
pip install pipenv
```
```bash
pipenv install --dev
```
```bash
pipenv shell
```
### Troubleshooting Tips

- Running Visual Studio Code in administrator mode may be necessary if you face issues installing dependencies.
- Installing dependencies one by one may be required if it fails using pipenv and the pipfile,
  if this happens navigate in the project directory to a file named "Pipfile". The required dependencies are located
  in this file and you can install them as needed.
  Use the following command to see what dependencies and packages have been installed. Install any
  remaining dependencies. 

  ```bash
  pipenv graph
  ```
### Step 2: Create Testing Directory
1. In the project directory open the "weather_project_folder".
2. Create a new folder named "tests", all of the test files will be placed in this folder.

You should now be ready to work on the remaining student labs.

