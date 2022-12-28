# Food Donation Log

This repo is based off of the Django tutorial. It basically follows the same structure with a few styling changes.

## Prereqs

1. Python ( I'm using 3.9.6)
2. Time

## Installation

1. Navigate to your local directory in terminal.
    1. For example: ```cd ~/Projects/donationLog```
2. Clone the repo to your computer.
    1. Click the green code button and copy the link. I use SSH, you may have to [set up your SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) or use [another authentication method](https://docs.github.com/en/authentication). 
    2. The command will look something like this ```git clone git@github.com:wiredacorn/donationLog.git .``` <br>(The dot at the end instructs git to clone to the current folder.)
2. Install venv
    1. Use python to install venv. ```python3 -m pip install --user virtualenv```
    2. Use venv to establish a virtual environment.```python3 -m venv .env```
    3. Activate the virtual environemnt in your terminal session. ```source .env/bin/activate```. <br>This virtual environment is now active for the current terminal session. You will have to do this every time you open a new terminal session for this project.
    4. To confirm that the virtual environment is active, use ```which python``` which should display a path to your project foler. <br>If the virtual environment is not active ```which python3``` will display the systems global python instance at ```/user/bin/python3```.
3. Install Django
    1. Once venv is active, use ```python -m pip install Django``` to install.
    2. Open ```python``` to test if Django is installed.
    3. In the python terminal, enter ```import django```, then ```print(django.get_version())``` which should print the installed version.
4. Start the application
    1. Enter ```python manage.py runserver``` to start the local server.
    2. Go to ```http://127.0.0.1:8000/``` in the browser to view the website.
    3. Go to ```http://127.0.0.1:8000/admin``` to view the admin area. Login using ```dev``` and ```password```.


## Installation