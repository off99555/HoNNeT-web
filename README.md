# HoNNeT-web
[Website](https://honnet.herokuapp.com/) for my [HoNNeT](https://github.com/off99555/HoNNeT) deep learning side-project.

This app will load the trained `keras` deep learning model trained from the main **HoNNeT** repository
and predicts which team would win, how long the match is going to last, and whether the team
would lose by conceding or by the main tower being destroyed.

It contains the files required to run the web inside Heroku. I use Vue.js,
Bulma.io and Flask as web technology stack.

The only file for web interface is `templates/index.html`. It contains heavy use of
Jinja2 templating, Bulma.io CSS classes, and Vue.js scripting.

## Role of each file
- `honnet_brain.h5` is the Keras model representing the knowledge of the neural
  network (about 1 MB in size)
- `honnet_brain_architecture.*` are text files generated to show the
  architecture of the network in human-readable format only, they are not used for
  anything else
- `app.py` is the main application to run
- `heroes_name.pkl` is a **pickle** generated file containing HoN hero names as
  a python dictionary, it's used to convert from `hero_id` to `hero_name` and
  vice versa
- `honnet.py` is a module containing related functions to use the brain
- `requirements.txt` is containing all modules required to run `app.py`, (this
  file is generated by calling `pip freeze > requirements.txt`)
- `Procfile` is for Heroku, it will read and run the command inside this file to
  start the web
- `runtime.txt` is for Heroku, it will read this file to figure out which Python
  version to use

## Requirements
- Python 3
- virtualenv (`pip install virtualenv`)

## Running on local host (your machine)
1. Clone this repository and `cd` into it.
2. Create a development environment dedicated for this repository because we are
   going to install something here: run `virtualenv venv`
3. Tell python to use the environment recently created by running `source
   activate venv` (or `activate venv` if you are on Windows).
4. Install dependencies: `pip install -r requirements.txt` (`gunicorn` is
   unnecessary, don't worry if there is an error installing it, it's required for
   the real Linux web server only)
   This will install some libraries into that `venv` directory.
5. Enter `python app.py` to run the application
6. Open web browser and go to http://127.0.0.1:5000/
7. Play with the application.

## Disclaimer
The data used for training the model needs to be updated regularly because heroes mechanisms are updated often.
Look at the date of the `honnet_brain.h5` to see when it was last updated.

Have fun!
