# Playwright Lab

The main focus of this lab is to teach students automation testing using Playwright, various other tools, and Oracle Forecast developed by Team 6.

## Intro to Playwright

Playwright is a framework that is used for automating web browser interactions. It supports testing across multiple browsers and provides 
tools for reliable, fast, and efficient web application testing. It is one of the newer testing tools as it was launched in 2020. It supports a variety of programming languages; 
however, this lab will focus on using Python as well as Chrome for the web browser. Follow this link to learn more about [Playwright](https://playwright.dev/docs/intro)

## Lab Objective

Using Playwright, Python, and the pytest library, students will create a variety of tests that will cover the following: form submissions, link and button clicks, dropdown menus, mouse actions, keyboard inputs, layout testing, page navigation, data entry and retrieval, data validation, error messages, and exception handling.

## Prerequisites

- Ensure you have performed the "environment_setup.md" lab before beginning.
- Familiarity with Python 3.8 or later (this lab will use Visual Studio Code for Windows as the IDE, and Google Chrome 
for the browser).
- Familiarity with Python for writing test scripts.
- Familiarity with web technologies such as CSS, HTML.
- Familiarity with Python virtual environments.
- Familiarity using the command prompt.
- Some familiarity with Playwright.
- Basic troubleshooting skills.
  
## Packages and Libraries Used

- Playwright - A browser automation framework that allows you to control browsers (Chrome for this lab).
- Pytest - A testing framework used to write and execute simple and scalable test cases.

## Instructions

### Step 1: Setup

1. Ensure you have performed the "environment_setup.md" lab.
2. Install browsers for Playwright. After completing the "environment_setup.md" lab Playwright should already be installed, however, we must
still install the browsers that Playwright will use. Do this by running the following command:

```bash
playwright install
```

4. Navigate to the tests folder in the project directory.
5. Create a new file name test_playwright.py
6. Open a command prompt and use the following to launch the flask application. You may need to cd into the weather_project_folder directory.

```bash
flask run
```
5. Once the application is running open it in Chrome, navigate to the registration page and create a user with the following credentials (username: group6, email: group6@gmail.com, password: password), if the user already exists continue ahead with the lab. 

### Step 2: Step by Step Creating Test Cases
