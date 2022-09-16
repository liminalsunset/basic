**This assumes you have python instsalled on your machine <3**

** consider adding a check python version and how to upgrade, how to restart your env if it gets deactivated/you restart vscode or something **

1. Make (or navigate to) a directory for the project
2. CD into the directory

** might be easier to open code here, so you don't have to activate the env twice--either do it initially or wait until after you're at the point you need a .gitignore

3. Set up a virtual environment for your project:
    python3 -m venv env-name

Actually I could just keep going in the terminal wait for VSCode... so skip to 5 once you activate your env

4. Open vscode and in the vscode terminal type:
    source env_name/bin/activate

After you've created and activated your virtual environment (venv):
    ** should I add that you'll see the venv before your directory name in terminal? ** Also, I did look into this and your do want your virtualenv at the top of your root directory (the same directory that contains your project--but you could be more organized and nerdy about it and there's like, virtualenvwrapper too: https://stackoverflow.com/questions/1783146/where-in-a-virtualenv-does-the-custom-code-go/1783482#1783482)

5. python3 -m pip install Django

6. It might be suggested you update pip (skip this otherwise):
    python3 -m pip install --upgradepip
7. Start your Django project:
    django-admin startproject project_name
8. cd into your project

Switch the order here:

9. python3 manage.py runserver
10. check out http://localhost:8000/ to see that the install worked correctly :)
11. You have unapplied migrations:
    python3 manage.py migrate 


12. Create a new repo on github, don't initialize with anything and wait to do anything else because you likely don't want to publish your secret key to git:

Luckily we have python decouple availabe (https://pypi.org/project/python-decouple/) to read more.

13. Find a .gitignore like:
    https://djangowaves.com/tips-tricks/gitignore-for-a-django-project/

14. Make sure your .gitignore ignores .env

15. Back in VSCode: 
    Add the .gitignore at the same directory level as manage.py <=== !

16. Make an .env file at the same directory level as manage.py
    -    aside: (decouple supports both .ini and .env files.)

17. Cut your secret key from settings.py (in project directory) and paste it in your .env 

18. Where your security key was in settings.py, replace that with (this is case sensitive, you're probably already aware but just in case):

    from decouple import config

    SECRET_KEY = config(“SECRET_KEY”)

19. Then in your terminal run:

    pip install python-decouple

    Is python-decouple not working? Tried fix to uninstall decouple, decouple isn't installed, and python-decouple is, but it's still saying can't import config, yes I checked the install too--I even tried to install based on requirements.txt and requirements are already satisfied. So...

    other fixes include: installing python-decouple outside of venv, also just restarting the terminal >.>

    pip freeze > requirements.txt (I would google this further, but basically it seems to just keep track of your dependencies)

    https://appdividend.com/2022/06/15/python-unresolved-import/ - could just be a pylance/interpreter thing as it's running locally, despite unresolved stuff. I tried pointing it accordingly and it still didn't resolve the linting? issue.

    

20. git init
21. git add .
22. git commit -m "first commit"
23. git branch -M main
24. git remote add origin .. (past your git remote origin address)
25. git push -u origin main

