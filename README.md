# DeasignNewbie: Dimensional Scaffolding for Text-to-Image Product Design

<p align="center" width="100%">
<img src="cover.png" alt="DesignNewbieTeaser" style="width: 80%; min-width: 300px; display: block; margin: auto;">
</p>

DesignNewbie is an AI-enabled product design interface for novice users that provides dimensional scaffolding for text-to-image models.

Generative AI has enabled novice designers to create professional-looking visual representations of product concepts quickly. However, novices also have limited domain knowledge, which could constrain their ability to write prompts that effectively explore a product design space. DesignNewbie aims to help them generate prompts for a text-to-image model by surfacing key design dimensions from generated images.

Below, we'd like to describe the setup instructions for the web application. 

## Setting Up the Environment
To set up, you must have a working Firebase project, generate `.env` containing your OpenAI API key and other certification keys, and download the necessary packages.
### Step 1: Create a Firebase project
The logged data and generated images are stored in [Firebase](https://firebase.google.com/docs) by default. Use your own account to start a project and enable Realtime Database and Storage.


### Step 2: Generate Environment Variable File
Create a file under the project's root folder named `.env`. The Web Application will get private inputs from this file, including your OpenAI api key and Firebase configurations. Bellow is the required variables, please configure the vallues according to your own account and setup.

#### OpenAI key
You need a paid OpenAI account to support the DALLe3 model, GPT-4o model, and GPT-4o-mini model.
```
REACT_APP_OPENAI_API_KEY=Your own OpenAI key
```

#### Firebase SDK configuration
You can find the Database URL in the Realtime Database tab and the other information in the `SDK Setup and Configuration` section under Project Overview.

```
FIREBASE_DB_URL=Your own Firebase Realtime Database's URL

REACT_APP_FIREBASE_API_KEY=Get the following information in Project Overview
REACT_APP_FIREBASE_AUTH_DOMAIN=
REACT_APP_FIREBASE_PROJECT_ID=
REACT_APP_FIREBASE_STORAGE_BUCKET=
REACT_APP_FIREBASE_MESSAGING_SENDER_ID=
REACT_APP_FIREBASE_APP_ID=
REACT_APP_FIREBASE_MEASUREMENT_ID=
```

#### Backend
Auto-uploading to the Storage using scripts requires a private key. Go to your Firebase project settings and access the `Service account` section. Create and download a private key and put it under the `backend/key` folder.

```
FIREBASE_CERT_PATH=PATH to your Storage_private_key.json

REACT_APP_BACKEND_URL=localhost:31 
# the backend will run on port 31 by default. You may change its behavior in backend_server.py
```

### Step 3: Installation
You will have to install both the Python backend and the React frontend.

#### Backend
The dependency for the backend is recorded in `backend_requirement.txt`. You may install them directly, but we strongly suggest you use a [Python virtual environment](https://docs.python.org/3/library/venv.html).
```
# install virtual environment
python3 -i pip install virtualenv
python3 -m venv <virtual-environment-name>

# activate virtual environment
source <virtual-environment-name>/bin/activate

# install python packages
python3 -i pip install -r backend_requirement.txt
```

#### React Web Application
Execute the `npm install` command under the project's root folder. The required dependencies will be installed according to the project.

### Step 4: Start the Web Application
Go to the project's root directory. Start the backend server first using. Then, you may run the `npm start` to start the Web Application.
```
# under DesignNewbie
python3 backend_server.py
npm start
```
Note: the Web Application will run on localhost:3030. If another process occupies the port, you may change the port number in `package.json` Line 7.

## Run DesignNewbie's Testing Interface
You may use any browser to access the interface on the localhost. The default route `localhost:3030/` will lead you to an empty panel with the username "TestUser". Here, you may explore the tool without a hard time limit.

## Start a Full Task Session
To start a full session, access the endpoint `localhost:3030/Start` and enter a user name. The corresponding user will be set up in the database. Each user name will have 60 minutes to access the session before being blocked.


## Authors and Citation

## Acknowledgement
This public repo is not meant for production usage and the Web App is set to run on localhost. To securely run the application online, please consider host the application using [nginx](https://nginx.org/en/docs/) or [Apache](https://httpd.apache.org/docs/2.4/).

The application is developed and tested in Node version 14.18.3 and Python version 3.10.2.
