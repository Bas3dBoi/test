# Centsible Sprint 1 Test Plan

## 1. Introduction

This document outlines the testing plan for our web application, Centsible. The primary goal is to ensure the application functions correctly and meets the specified requirements.

## 2. Testing Tools

The application will be tested using the following testing tools:

- Pytest for unit testing and integration testing
- Selenium for end-to-end testing and UI testing
- Requests Library for any API testing
- Coverage for code coverage analysis and reporting where necessary

## 3. Test Cases Sprint 1

The test cases for Sprint 1 will cover the following areas:

- Database Initialization
- User Authentication
- Form Submission
  
## 3.1 Example Test Cases

- Test case 1: Test User Authentication

```python

import pytest
from flask import Flask
from flask_login import LoginManager
...

def test_validate_username(app):

    user = User(username="testuser", email="testuser@gmail.com", password=bcrypt.generate_password_hash("password").decode('utf-8'))
    db.session.add(user)
    db.session.commit()

    with app.test_request_context('/register'):
        form = RegisterForm(username="testuser", email="newuser@gmail.com", password="password")
        with pytest.raises(Exception):
            form.validate_username(form.username)

```

- Test Case 2: Test Selenium Register User

```python

import pytest
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
...

  def test_register_user(driver):
    driver.get("<http://127.0.0.1:5000/register>")

    username_input = WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.NAME, "username"))
    )
    email_input = driver.find_element(By.NAME, "email")
    password_input = driver.find_element(By.NAME, "password")

    username_input.send_keys("group7")
    email_input.send_keys("<group7@gmail.com>")
    password_input.send_keys("password")
    time.sleep(2)  # Pause for 2 seconds to observe the filled form

    signup_button = driver.find_element(By.XPATH, "//input[@type='submit' and @value='Sign Up']")
    signup_button.click()
    time.sleep(2)  # Pause for 2 seconds to observe the click action

    success_message = WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.XPATH, "//p[@class='success' and contains(text(), 'Registration Successful!')]"))
    )
    assert "Registration Successful!" in success_message.text
    time.sleep(2)  # Pause for 2 seconds to observe the result

```

Test Case 3: Test Database Initialization

```python

import pytest

def test_database_initialization(test_client):
    with app.app_context():
        inspector = db.inspect(db.engine)
        tables = inspector.get_table_names()
        assert 'user' in tables

```
