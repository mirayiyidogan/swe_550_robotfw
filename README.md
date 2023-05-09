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


