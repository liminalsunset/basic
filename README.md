**This assumes you have python instsalled on your machine <3**

** consider adding a check python version and how to upgrade, how to restart your env if it gets deactivated/you restart vscode or something **

1. Make a directory for the project
2. CD into the directory
3. Set up a virtual environment for your project:
    python3 -m venv env-name
4. Open vscode and in the vscode terminal type:
    source env_name/bin/activate
5. After you've created and activated your virtual environment (venv):
    **should I add that you'll see the venv before your directory name in terminal?**
    python3 -m pip install Django
6. It might be suggested you update pip (skip this otherwise):
    python3 -m pip install --upgradepip
7. Start your Django project:
    django-admin startproject project_name
8. cd into your project
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

    pip freeze > requirements.txt (I would google this further, but basically it seems to just keep track of your dependencies)

20. git init
21. git add .
22. git commit -m "first commit"
23. git branch -M main
24. git remote add origin .. (past your git remote origin address)
25. git push -u origin main

