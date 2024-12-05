# Robot Framework Lab

The main focus of this lab is to teach students acceptance testing using Robot Framework, SeleniumLibrary, RequestsLibrary, and Oracle Forecast developed by Team 6. 

## Intro to Robot Framework

Robot Framework is one of many automation frameworks, it is used for test automation and robotic process automation. It uses a keyword-driven approach, making it easy to create 
readable and reusable test cases, this allows both technical and non-technical team members to understand and contribute to testing. Robot Framework generates detailed logs 
and reports in HTML format, providing clear insights into test results and helping identify issues quickly. Follow this link to learn more about
[Robot Framework](https://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html).


## Lab Objective

Using Robot Framework, SeleniumLibrary, and the RequestsLibrary, users will create a variety of tests designed to meet the specifications outlined in the following business requirements.
Robot Framework will serve as the main framework to organize and execute the test cases, ensuring that the application meets the specified acceptance criteria.
## Business Requirements for Acceptance Testing

Based on the user stories found throughout the sprint files in the project documentation the following business requirements can be used to create our acceptance tests:
- Account Registration - The system shall provide a registration form for new users to create an account.
The registration process shall be quick and easy, requiring minimal information (e.g., username, email, password).
- Login - The system shall provide a login form for users to access their accounts.
The login process shall be quick and easy, allowing users to access the weather application promptly.
- Current Weather Data - The system shall display the current weather data for the user's selected location.
The weather data shall include temperature, humidity, wind speed, and other relevant metrics.
- Hourly Weather Data - The system shall display hourly weather data for the user's selected location.
The hourly data shall include temperature, chance of precipitation, and other relevant metrics.
- Daily Weather Forecast - The system shall display a daily weather forecast for the user's selected location.
The daily forecast shall include temperature, chance of precipitation, and other relevant metrics.

## Prerequisites

- Ensure you have performed the "environment_setup.md" lab before beginning. 
- Familiarity with Python 3.8 or later (this lab will use Visual Studio Code for Windows as the IDE, and Google Chrome 
for the browser).
- Familiarity with Python for writing test scripts.
- Familiarity with web technologies such as CSS, HTML.
- Familiarity with Python virtual environments.
- Familiarity using the command prompt.
- Some familiarity with Robot Framework.
- Basic troubleshooting skills.
  
## Packages and Libraries Used

- Robot Framework will manage and execute the test cases.
- SeleniumLibrary will handle the UI testing to ensure the user interface meets the acceptance criteria.
- RequestsLibrary will verify the backend APIs to ensure they provide the correct data.
  
## Instructions

### Step 1: Setup

1. Ensure you have performed the "environment_setup.md" lab.
2. If the "environment_setup.md" lab was performed succesfully then Robot Framework, SeleniumLibrary, and RequestsLibrary should already be install on the machine.
3. Navigate to the tests folder in the project directory.
4. Create a new folder named acceptancetests and navigate into it.
5. Create a new file named test_robot_acceptance.robot.
6. Open a command prompt and use the following to launch the flask application. You may need to cd into the weather_project_folder directory.

```bash
flask run
``` 

### Step 2: Step by Step Creating Test Cases

1. Create a settings section, the Settings section in a Robot Framework test file is used to define the configuration and setup for
the test suite.
![Robot Settings](robot_settings.png)
