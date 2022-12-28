# Food Donation Log

This repo is based off of the Django [quick setup](https://docs.djangoproject.com/en/4.1/intro/install/) and [tutorial](https://docs.djangoproject.com/en/4.1/intro/tutorial01/). It basically follows the same structure with a few styling changes.

## Prereqs

1. Python ( I'm using 3.9.6)
2. Git
3. Time

## Installation

1. Navigate to your local directory in terminal.
    1. For example: ```cd ~/Projects/donationLog```
2. Clone the repo to your computer.
    1. Click the green code button and copy the link. I use SSH, you may have to [set up your SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) or use [another authentication method](https://docs.github.com/en/authentication). 
    2. The command will look something like this ```git clone git@github.com:wiredacorn/donationLog.git .``` <br>(The dot at the end instructs git to clone to the current folder.)
2. Install venv
    1. Use python to install venv. ```python3 -m pip install --user virtualenv```
    2. Use venv to establish a virtual environment. ```python3 -m venv .env```
    3. Activate the virtual environemnt in your terminal session. ```source .env/bin/activate```. <br>This virtual environment is now active for the current terminal session. You will have to do this every time you open a new terminal session for this project.
    4. To confirm that the virtual environment is active, use ```which python``` which should display a path to your project folder. <br>If the virtual environment is not active ```which python3``` will display the systems global python instance at ```/user/bin/python3```.
3. Install Django
    1. Once venv is active, use ```python -m pip install Django``` to install.
    2. Open ```python``` to test if Django is installed.
    3. In the python terminal, enter ```import django```, then ```print(django.get_version())``` which should print the installed version.
4. Start the application
    1. Enter ```python manage.py runserver``` to start the local server.
    2. Go to ```http://127.0.0.1:8000/``` in the browser to view the website.
    3. Go to ```http://127.0.0.1:8000/admin``` to view the admin area. Login using ```dev``` and ```password```.


## Usage

Just learning stuff at this point, but here's what I got so far:

1. Main project lives in the root ```donationLog``` folder.
2. Project consists of multiple 'apps' which are in the subfolders. For example the ```polls``` which I set up in the tutorial.
3. ```settings.py``` in the root folder lists all apps which will be used. A bunch of other variables and configurations. Set the admin page template etc.
4. Each app sets up a ```models.py``` file which determines what types of data it will need to store in the database.
5. Each app has a ```urls.py``` file which determines what pages and api endpoints will be available in the app. URLs can be dynamic. Each entry will specify what actions will be taken when the user hits that endpoint. Commonly, you will specify a ```view```.
6. Views are stored in ```views.py``` and will specify the html template and maybe do some data processing or other intermediate steps.
7. The html templates are stored in ```{project}/{app}/templates/{app}/template.html``` for example: ```donationLog/polls/templates/polls/results.html```. The folder structure is needed to allow Django to read the templates.
8. Templates use a template language which allows for accessing data that is passed into the context. We are getting the question number from the url ```localhost/{id}``` for example and passing that to the html template. The below snippet shows how we can access the questions using the ```latest_question_list``` which is passed into the template by ```IndexView``` in ```views.py```.

```
{% for question in latest_question_list %}
    <li><a href="{% url 'polls:detail' question.id %}">{{ question.question_text }}</a></li>
{% endfor %}
```

9. In the ```results.html``` template, the ```Question``` is passed in and is accessed like so:
```
{% for choice in question.choice_set.all %}
    <li>{{ choice.choice_text }} -- {{ choice.votes }} vote{{ choice.votes|pluralize }}</li>
{% endfor %}
```