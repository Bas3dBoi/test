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

12. Run the test. Open a command prompt and ensure you are in the tests directory, use this command:
```bash
pytest test_app.py
```
![Test Passed APP](pytest_app_passed.png)

13. Create a new test file named "test_user_auth.py". This file is a test suite for the user authentication components of the application.

14. In "test_user_auth.py" import the necessary packages.
![Import User Auth](pytest_user_auth_imports.png)
- Import pytest: Imports the pytest library, which is used for writing and running test cases.
- From flask import Flask: Imports the Flask class to create a Flask application instance.
- From flask_login import LoginManager: Imports the LoginManager class from Flask-Login to manage user sessions.
- From weather_project_folder.blueprints.userauth.user_auth import User, RegisterForm, load_user: Imports the User model, RegisterForm class, and load_user function from the user authentication blueprint.
- From weather_project_folder.extensions import db, bcrypt: Imports the SQLAlchemy database instance (db) and the bcrypt instance (bcrypt) from the extensions module.

15. Define a pytest fixture to set up an in-memory SQLite database, initiallizze various extensions, and create database tables.
![Pytest UserAuth Fixture](pytest_userauth_fixture.png)
- Create a new instance of the Flask web framework, passing the current module name (__name__) as the app name.
- Set the database URI to an in-memory SQLite database, which means the database will be created in RAM and deleted when the test is finished.
- Set a secret key for the app, which is used for security purposes such as signing session cookies.
- Initialize the database (using SQLAlchemy) and bcrypt (a password hashing library) with the Flask app.
- Create a new instance of the LoginManager class and initialize it with the Flask app.
- Push the app context which makes the app instance available to other parts of the code.
- Create all the database tables defined in the app's models.
- Yield the app instance to the test, allowing it to use the app for testing purposes.
- After the test is finished it drops all the database tables to clean up.

16. Create a test case "test_validate_username". This tests the validate_username method of the RegisterForm class.
![Pytest Userauth Username](pytest_userauth_username.png)
- Def test_validate_username(app):: Defines a test function that uses the app fixture.
- Docstring: Describes the purpose of the test, which is to verify that the validate_username method of the RegisterForm class correctly identifies an existing username.
- User = User(...): Creates a new User instance with the username "testuser".
- Db.session.add(user): Adds the new user to the database session.
- Db.session.commit(): Commits the transaction to save the user to the database.
- With app.test_request_context('/register'): Creates a test request context for the /register endpoint.
- Form = RegisterForm(...): Creates a new RegisterForm instance with the username "testuser".
- With pytest.raises(Exception):: Asserts that an exception is raised when calling form.validate_username(form.username), indicating that the username "testuser" already exists.

17. Create a test case "test_load_user". This test checks if load_user correctly retireves a user from the database.
![Pytest Userauth Load User](pytest_userauth_load.png)
- User = User(...): Creates a new User instance with the username "testuser".
- Db.session.add(user): Adds the new user to the database session.
- Db.session.commit(): Save the user to the database.
- Loaded_user = load_user(user.id): Calls the load_user function with the user's ID and stores the result in loaded_user.
- Assert loaded_user == user: Asserts that the loaded user is the same as the original user.

18. 12. Run the test. Open a command prompt and ensure you are in the tests directory, use this command:
```bash
pytest test_user_auth.py
```
![Test Passed Userauth](pytest_userauth_passed.png)

## Try it Yourself

Now that you have a decent understanding of how Selenium WebDriver, Pytest, and the Oracle Forecast application work, create your own test to validate the user registration function. Create a test that registers a new user with credentials of your own choosing, have it validate by searching for a succesful registration message, then login using those new credentials. 

## Results Overview
The test_selenium file has tested the following in various ways: form submissions, link and button clicks, dropdown menus, mouse actions, keyboard inputs, layout testing, page navigation, data entry and retrieval, data validation, error messages, and exception handling. There are a plethora of tests that can be written using Selenium WebDriver, these were just a little sample to get you going. 

## Coverage Reports
This test is only part of a suite of various tests designed to create a solid testing plan. Be sure to read the coverage report included with the test suite to better understand how testing is an integral part of the development process.

### Troubleshooting Tips

- If any tests fail ensure they are setup properly. Run the test again, sometimes a test will fail due to network issues, latency issues etc. 
