# Pytest Unit Testing Lab

The main focus of this lab is to teach students the basics of unit testing using Python, Pytest, and the Oracle Forecast application designed by Team 6.

## Intro to Pytest

Pytest is a popular testing framework for Python that simplifies the process of writing and running tests. Its main purpose is to help developers ensure their 
code works correctly by providing tools to write small, isolated tests. It supports various types of testing, including unit tests, integration tests, and functional tests.
Pytest works by discovering and running test functions in your code. You write test functions using simple assertions, and pytest automatically finds these tests and 
executes them. It provides detailed output for each test, making it easy to identify and fix issues.

## Lab Objective

Using Python, Pytest, and the Oracle Forecast application students will create a variety of tests cases to test functionalities across the entire application.

## Prerequisites

- Ensure you have performed the "environment_setup.md" lab before beginning. 
- Familiarity with Python 3.8 or later (this lab will use Visual Studio Code for Windows as the IDE, and Google Chrome 
for the browser).
- Familiarity with Python for writing test scripts.
- Familiarity with web technologies such as CSS, HTML.
- Familiarity with Python virtual environments.
- Familiarity using the command prompt.
- Some familiarity with Pytest.
- Basic troubleshooting skills.
  
## Packages and Libraries Used

- Pytest - A testing framework used to write and execute simple and scalable test cases.
- Unittest.mock - A tool for creating mock objects during testing.
- Requests - Used to send HTTP requests, handle responses, interact with web APIs by sending GET, POST, PUT, DELETE requests, etc.
  
## Instructions

### Step 1: Setup

1. Ensure you have performed the "environment_setup.md" lab.
2. Navigate to the tests folder in the project directory.

### Step 2: Step by Step Creating Test Cases

1. Create a new test file named test_app.py. It will test the Flask application instance and its components that are set up and configured in the app.py file.
The tests wil ensure that the application and its components are properly initialized and functioning correctly.

2. In test_app.py import the necessary dependencies.
![Import Statements App](pytest_imports_app.png)
- Pytest: Used for running the test functions.
- From weather_project_folder.app import app, db, bcrypt, cache: Imports the Flask application instance (app), the SQLAlchemy database instance (db),
the bcrypt instance (bcrypt), and the cache instance (cache) from the weather_project_folder.app module.

3. Define a pytest fixture to set up the Flask application for testing.
![Pytest Fixture App](pytest_fixture_app.png)
- Configures the app for testing by setting TESTING to True, using an in-memory SQLite database, and disabling CSRF protection.
- Creates an application context and initializes the database.
- Yields a test client instance, allowing tests to interact with the app.
- After the test is finished, it drops the database to clean up.

4. Create a test case "test_app_exists". A unit test that checks if the Flask applicatin instance exist.
![Pytest Test App Exists](pytest_test_app.png)
- Def test_app_exists(test_client): Defines a test function that uses the test_client fixture.
- Assert app is not None: Asserts that the Flask application instance (app) exists.

5. Create a test case "test_home_page". It verifies that the home page loads correctly.
![Pytest Test Homepage](pytest_homepage.png)
- Sends a GET request to the root URL ('/') using the test_client.
- Checks if the response status code is 200 (OK), indicating a successful request.
- Checks if the response data contains the string 'Weather Dashboard'.

6. Create a test case "test_database_initialization". It will check if the 'user' table exists in the database after intialization.
![Pytest Database Initialize](pytest_database.png)
- With app.app_context(): creates an application context for the test.
- Inspector = db.inspect(db.engine): creates a database inspector object to examine the database schema.
- Tables = inspector.get_table_names(): retrieves a list of table names from the database.
- Assert 'user' in tables: checks if the 'user' table is present in the list of tables. If it's not, the test will fail.

7. Create a test case "test_login_manager_initialization". This is a unit test that checks login manager attribute of the app object is initialized.
![Pytest Login Manager](pytest_login_manager.png)
- Def test_login_manager_initialization(test_client): Defines a test function that uses the test_client fixture.
- Assert app.login_manager is not None: Asserts that the login manager instance (app.login_manager) exists.

8. Create a test case "test_bcrypt_initialization". This test ensures that the bcrypt extension is initialized and can be used for password hashing and encryption.
![Pytest Bcrypt Initialize](pytest_bcrypt.png)
- Def test_bcrypt_initialization(test_client): Defines a test function that uses the test_client fixture.
- Assert bcrypt is not None: Asserts that the bcrypt instance (bcrypt) exists.

9. Create a test case "test_cache_initialization". This is a unit testthat checks if the cache object has been initialized correctly.
![Pytest Cache Initialize](pytest_cache_initial.png)
- Def test_cache_initialization(test_client): Defines a test function that uses the test_client fixture.
- Assert cache is not None: Asserts that the cache instance (cache) exists.

10. Create a test case "test_blueprints_registration". This tests whether the blueprints are registered in the application.
![Pytest Blueprints](pytest_blueprints.png)
- Def test_blueprints_registration(test_client): Defines a test function that uses the test_client fixture.
- Assert 'weather_app' in app.blueprints: Asserts that the weather_app blueprint is registered in the application.
- Assert 'user_auth' in app.blueprints: Asserts that the user_auth blueprint is registered in the application.
- Assert 'error_handler' in app.blueprints: Asserts that the error_handler blueprint is registered in the application.


12. Run the test. Open a new command prompt seperate from the one running the application. Enter this command:
```bash
pytest test_selenium.py
```
If you would like to see the print statements from the functions for debugging enter this command:
```bash
pytest -s test_selenium.py
```
![Test Passed](selenium_test_passed.png)
Ignore the error messages present in the picture, those have to do with my local machine and do not affect the Selenium tests.
Observe how Selenium opens a Chrome window and navigates through it as a regular user would. With the use of time.sleep() functions the user is able to observe the interactions instead of everything happening in a blur. 

## Try it Yourself

Now that you have a decent understanding of how Selenium WebDriver, Pytest, and the Oracle Forecast application work, create your own test to validate the user registration function. Create a test that registers a new user with credentials of your own choosing, have it validate by searching for a succesful registration message, then login using those new credentials. 

## Results Overview
The test_selenium file has tested the following in various ways: form submissions, link and button clicks, dropdown menus, mouse actions, keyboard inputs, layout testing, page navigation, data entry and retrieval, data validation, error messages, and exception handling. There are a plethora of tests that can be written using Selenium WebDriver, these were just a little sample to get you going. 

## Coverage Reports
This test is only part of a suite of various tests designed to create a solid testing plan. Be sure to read the coverage report included with the test suite to better understand how testing is an integral part of the development process.

### Troubleshooting Tips

- If any tests fail ensure they are setup properly. Run the test again, sometimes a test will fail due to network issues, latency issues etc. 
