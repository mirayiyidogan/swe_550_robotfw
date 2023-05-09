# Project Preparation

## Project Requirements

Before starting the project, ensure that you have the following requirements in place:

- Python version 3.8 or higher (Make sure to select "Add Python to PATH" during installation to enable easy access)
- An Integrated Development Environment (IDE) such as VSCode or PyCharm
- Virtual Environment:
  - Install the `virtualenvwrapper-win` library by running the command: `pip install virtualenvwrapper-win`

## Setting up the Project

To set up the project, follow these steps:

1. Open a command prompt or terminal to set up and activate the virtual environment.
2. Create a new virtual environment (if needed) by running the command: `mkvirtualenv 550` (You can use an existing virtualenv as well).
3. Activate the virtual environment by running: `workon 550`.
4. Navigate to the directory where the "contents" file is located.
   - Change the directory (cd) to the appropriate location: `cd path/to/contents`.
5. Install the required packages by running: `pip install -r requirements.txt` (This command will download the necessary packages for Robot Framework testing).

## Extension Installations (optional but preferable)

Consider installing the following extensions to enhance your development experience:

- Python Extension for your IDE.
- Robot Framework Language Server:
  - Configure the extension settings by setting the "Robot › Language-server: Python" path to the location of your Python interpreter, e.g., "C:\Users\beyn\Envs\550\Scripts\python.exe".

## Running the Program

- To execute the program, run the following command:
`python main.py`

- To run all the tests, use the following command:
`robot -d result rf_code_basic\tests\api`

# Test Cases

## Happy Case

### Test Case: Verify Login Returns 200

**Description:** This test case verifies that the login API endpoint returns a status code of 200, indicating a successful login.

**Steps:**
1. Log a message to the console, indicating that a request is being sent to the login endpoint.
2. Create a JSON body with the following key-value pairs:
   - "username" set to "admin"
   - "password" set to "masterPass"
3. Send a POST request to the login endpoint (`${GLOBAL_ENDPOINT_LOGIN}`) with the JSON body.
4. Store the response in the variable `${response}`.
5. Validate the JSON response against the reference schema (`${GLOBAL_SCHEMA_LOGIN}`) using the `Validate Json Schema` keyword.

By executing this test case, you can ensure that the login API endpoint is functioning correctly and returns the expected status code and response structure.

### Verify Delete Users

**Description:** This test case verifies the functionality of deleting users through the Delete User API endpoint.

**Steps:**
1. Delete the user with the ID stored in the suite variable `${SUITE_USER_ID}`.
2. Store the response in the variable `${response}`.
3. Validate the JSON response against the user delete schema (`${GLOBAL_SCHEMA_USER_DELETE}`) using the `Validate Schema` keyword.

### Keywords

#### Custom Suite Setup

**Description:** This keyword performs the setup for the test suite.

**Steps:**
1. Authorize the user.
2. Create a new user and store the ID in the variable `${id}`.
3. Set the suite variable `${SUITE_USER_ID}` with the user ID.

### Verify All Users

**Description:** Verify that the Get All Users API endpoint returns a status code of 200 and the expected response.

**Steps:**
1. Log a message to the console, indicating that a request is being sent to the Get All Users endpoint.
2. Create a dictionary `${params}` with the key "filter" set to "all".
3. Send a GET request to the `${GLOBAL_ENDPOINT_USERS}` endpoint with the following parameters:
   - Headers: `${GLOBAL_AUTH_HEADER}`
   - Query Parameters: `${params}`
4. Store the response in the variable `${response}`.
5. Validate the JSON response against the reference schema `${GLOBAL_SCHEMA_USERS}`.

By executing this test case, you can ensure that the Get All Users API endpoint is functioning correctly and returns the expected status code and response structure.

### Verify Create New User ###
Description: This test case verifies the functionality of creating a new user through the Create User API endpoint.

**Steps:**
1. Log a message to the console indicating the request is being sent to ${GLOBAL_ENDPOINT_USERS}.
2. Send a request to create a new user.
3. Store the ID of the created user in the variable ${id}.
4. Set the suite variable ${SUITE_USER_ID} with the user ID.
5. Validate the JSON response against the user post schema ${GLOBAL_SCHEMA_USER_POST} using the Validate Schema keyword.

Please note that the above test case assumes the existence of the necessary resource files, variables, and keywords, and it should be adjusted as per your specific implementation.

Test Case: Verify Existing User

Description: This test case verifies the functionality of retrieving an existing user through the Get User API endpoint.

Test Steps:

Log a message to the console indicating the request is being sent to ${GLOBAL_ENDPOINT_USERS}/1.
Send a GET request to retrieve the user with ID 1.
Store the response in the variable ${response}.
Validate the JSON response against the user ID schema ${GLOBAL_SCHEMA_USERS_ID} using the Validate Schema keyword.
Please note that the above test case assumes the existence of the necessary resource files, variables, and keywords, and it should be adjusted as per your specific implementation.

## Unhappy Case

### Verify Login With Wrong Password Returns 401

**Description:** This test case verifies that the login API endpoint returns a status code of 401 when an incorrect password is provided.

**Test Data:**
- Username: admin
- Password: wrongPass

**Steps:**
1. Log a message to the console, indicating that a request is being sent to the login endpoint.
2. Create a JSON body with the provided username and password.
3. Send a POST request to the login endpoint (${GLOBAL_ENDPOINT_LOGIN}) with the JSON body.
4. Store the response in the variable `${response}`.
5. Validate the JSON response against the error schema (${GLOBAL_SCHEMA_ERROR}) using the `Validate Schema` keyword.

### Verify Login With Wrong User Returns 401

**Description:** This test case verifies that the login API endpoint returns a status code of 401 when an incorrect username is provided.

**Test Data:**
- Username: guest
- Password: masterPass

**Steps:**
1. Log a message to the console, indicating that a request is being sent to the login endpoint.
2. Create a JSON body with the provided username and password.
3. Send a POST request to the login endpoint (${GLOBAL_ENDPOINT_LOGIN}) with the JSON body.
4. Store the response in the variable `${response}`.
5. Validate the JSON response against the error schema (${GLOBAL_SCHEMA_ERROR}) using the `Validate Schema` keyword.

### Verify Login With Empty Data Returns 401

**Description:** This test case verifies that the login API endpoint returns a status code of 401 when empty data is provided.

**Test Data:**
- Username: (empty)
- Password: (empty)

**Steps:**
1. Log a message to the console, indicating that a request is being sent to the login endpoint.
2. Create a JSON body with the provided empty username and password.
3. Send a POST request to the login endpoint (${GLOBAL_ENDPOINT_LOGIN}) with the JSON body.
4. Store the response in the variable `${response}`.
5. Validate the JSON response against the error schema (${GLOBAL_SCHEMA_ERROR}) using the `Validate Schema` keyword.

### Verify Login With Wrong User And Password Returns 401

**Description:** This test case verifies that the login API endpoint returns a status code of 401 when both the username and password are incorrect.

**Test Data:**
- Username: guest
- Password: wrongPass

**Steps:**
1. Log a message to the console, indicating that a request is being sent to the login endpoint.
2. Create a JSON body with the provided username and password.
3. Send a POST request to the login endpoint (${GLOBAL_ENDPOINT_LOGIN}) with the JSON body.
4. Store the response in the variable `${response}`.
5. Validate the JSON response against the error schema (${GLOBAL_SCHEMA_ERROR}) using the `Validate Schema` keyword.

## Test Cases

### Verify Get Users Wrong Token

**Description:** Verify that the Get Users API endpoint returns 401 with wrong token.

**Steps:**
1. Send a GET request to `${GLOBAL_ENDPOINT_USERS}` with wrong token in the authorization header.
2. Validate the response against the error schema.

### Verify Get Users Empty Token

**Description:** Verify that the Get Users API endpoint returns 401 with empty token.

**Steps:**
1. Send a GET request to `${GLOBAL_ENDPOINT_USERS}` with empty token in the authorization header.
2. Validate the response against the error schema.

### Verify Get Users ID Wrong Token

**Description:** Verify that the Get Users by ID API endpoint returns 401 with wrong token.

**Steps:**
1. Send a GET request to `${GLOBAL_ENDPOINT_USERS}/1` with wrong token in the authorization header.
2. Validate the response against the error schema.

### Verify Get Users ID Empty Token

**Description:** Verify that the Get Users by ID API endpoint returns 401 with empty token.

**Steps:**
1. Send a GET request to `${GLOBAL_ENDPOINT_USERS}/1` with empty token in the authorization header.
2. Validate the response against the error schema.

### Verify Post Users Wrong Token

**Description:** Verify that the Post Users API endpoint returns 401 with wrong token.

**Steps:**
1. Send a POST request to `${GLOBAL_ENDPOINT_USERS}` with wrong token in the authorization header.
2. Validate the response against the error schema.

### Verify Post Users Empty Token

**Description:** Verify that the Post Users API endpoint returns 401 with empty token.

**Steps:**
1. Send a POST request to `${GLOBAL_ENDPOINT_USERS}` with empty token in the authorization header.
2. Validate the response against the error schema.

### Verify Delete Users Wrong Token

**Description:** Verify that the Delete Users API endpoint returns 401 with wrong token.

**Steps:**
1. Send a DELETE request to `${GLOBAL_ENDPOINT_USERS}/1` with wrong token in the authorization header.
2. Validate the response against the error schema.

### Verify Delete Users Empty Token

**Description:** Verify that the Delete Users API endpoint returns 401 with empty token.

**Steps:**
1. Send a DELETE request to `${GLOBAL_ENDPOINT_USERS}/1` with empty token in the authorization header.
2. Validate the response against the error schema.

### Verify Create User With 0 Contracts Is Not Working

**Description:** This test case verifies that creating a user with 0 contracts is not allowed and returns an expected status code of 400.

**Test Steps:**
1. Log a message to the console indicating the request is being sent to `${GLOBAL_ENDPOINT_USERS}`.
2. Send a request to create a new user with `numberOfContracts` set to 0.
3. Store the response in the variable `${response}`.
4. Validate the JSON response against the error contracts schema `${GLOBAL_SCHEMA_ERROR_CONTRACTS}` using the `Validate Schema` keyword.

### Verify Create User With 4 Contracts Is Not Working

**Description:** This test case verifies that creating a user with 4 contracts is not allowed and returns an expected status code of 400.

**Test Steps:**
1. Log a message to the console indicating the request is being sent to `${GLOBAL_ENDPOINT_USERS}`.
2. Send a request to create a new user with `numberOfContracts` set to 4.
3. Store the response in the variable `${response}`.
4. Validate the JSON response against the error contracts schema `${GLOBAL_SCHEMA_ERROR_CONTRACTS}` using the `Validate Schema` keyword.


