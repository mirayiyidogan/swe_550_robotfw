###Project Preparation###

1- Project Requirements
-Python version 3.8 or higher (You need to select "add python to PATH" in order for us to build up virtual environment)
-VSCode or PyCharm
-Virtual Environment
--in order to set up a virtual environment we need to upload related libraries: pip install virtualenvwrapper-win

2-Setting up the Project
In order to start your project first you need to open virtual environment in case you wanted to create another virtual
environment. Open a command prompt and write:
- mkvirtualenv 550 #There is already a virtualenv in your project folder so you may use that one
- workon 550 #In order to work on the virtual environment which is already created, run given command
- cd contents #Go to the directory where the "contents" file is located
- pip install -r requirements.txt #This command will download the related packages we need for Robotframework testing

3-Extension Installations(prefable)
Python
Robot Framework Language Server #Inside the extension settings, need to set up Robot › Language-server: Python as 
"C:\Users\beyn\Envs\550\Scripts\python.exe" means where you python package is located

In order to run the program , "python main.py"


In order to run all test, need to run above command
robot -d result rf_code_basic\tests\api

In order to use related postman collection, you need to first use "login" to authanticate with "inherit from parent which is login in this case. Our RobotFW starts with login as well in order to authanticate.

