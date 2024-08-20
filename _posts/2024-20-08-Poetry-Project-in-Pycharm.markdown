---

layout: single
title:  "Poetry Project in Pycharm with Python 3.12.5"
date:   2024-20-08 15:46:24 +0100
published: true

---
## How to create Poetry Project in PyCharm?

1.  In PyCharm Terminal , go to specific directory and and type command - 'poetry new Project-Name'
2.  cd into Project directory - 'cd Project-Name'
3.  Inside project folder, now add poetry using command - 'poetry env use python3'
4.  Poetry which Python version to use 'poetry env use python3'
5.  If you have created a venv (virtual enviorment) using Interpreter option of PyCharm make sure to use that venv
6.  If Poetry is still giving the error, you can manually activate the virtual environment, 'source .venv/bin/activate'
7.  Validate the path of active venv using 'poetry env info --path'. This same path must be selected as Interpreter under Pythorm settings . If not make sure to modify it and add path by Selecting the python executable within the .venv/bin/ directory
8.  Then run 'poetry install'
9.  Check python version in terminal if its the same one you set from venv 'python3 --version'
10. Finally you are ready to run your project , use command - 'poetry run python <project-name>/<file-name>.py'

Note:
When you observe a red marks on python package imports, even after adding it via poetry then make sure to validate venv paths and interpreter path is the same.

