# Flask Application Deployment Documentation

## Overview

This documentation provides a step-by-step guide for developing and deploying a Flask web application on Toystack.io as the deployment platform.

### Prerequisites

- Python installed on your local machine ([Download Python](https://www.python.org/downloads/))
- Git installed on your local machine ([Download Git](https://git-scm.com/downloads))
- A GitHub account ([GitHub](https://github.com/))

## Step 1: Create a Flask Application

1. Create a new directory for your Flask application:

   ```bash
   mkdir flask_app
   cd flask_app
   ```

2. Create a virtual environment (optional but recommended):

   ```bash
   python -m venv venv
   ```

3. Activate the virtual environment:

   ```bash
   venv\Scripts\activate
   ```

4. Install Flask:

   ```bash
   pip install Flask
   ```

5. Create a simple Flask app (e.g., `app.py`):

   ```python
   from flask import Flask

   app = Flask(__name__)

   @app.route('/')
   def hello():
       return 'Hello, World!'
   ```

6. Test the application locally

   ```
   python app.py
   ```

7. Browse the URL. This should display "Hello, World!".
   ```
   http://localhost:5000/
   ```

## Step 2: Create Dockerfile and Requirements.txt

1. Create a Dockerfile to dockerize the application.

   ```FROM python:3.8

       ENV PYTHONUNBUFFERED 1
       RUN mkdir /workdir
       WORKDIR /workdir
       COPY requirements.txt /workdir/
       RUN pip install --upgrade pip wheel
       RUN pip install -r requirements.txt
       COPY . /workdir/

       CMD ["python", "-m", "flask", "run", "--host=0.0.0.0", "--port=5000"]
   ```

2. Create Requirement.txt with necessary python modules to run the application.

   ```blinker==1.7.0
       click==8.1.7
       colorama==0.4.6
       Flask==3.0.1
       itsdangerous==2.1.2
       Jinja2==3.1.3
       MarkupSafe==2.1.4
       Werkzeug==3.0.1
   ```

## Step 3: Initialize a Git Repository

1. Initialize a Git repository:

   ```bash
   git init
   ```

2. Add and commit your Flask application:

   ```bash
   git add .
   git commit -m "Initial commit"
   ```

## Step 4: Create a GitHub Repository

1. Log in to your GitHub account.

2. Click on the "+" icon in the top right corner and select "New repository."

3. Fill in the repository name, description, and other details.

4. Click "Create repository."

## Step 5: Connect GitHub Repository

1. Copy the repository URL from your GitHub repository page.

2. Connect your local repository to the GitHub repository:

   ```bash
   git remote add origin <repository-url>
   ```

3. Push your code to GitHub:

   ```bash
   git push -u origin master
   ```

## Step 6: Deploy on Toystack.io

1. Browse the Toystack application ([Toystack.io](https://dashboard.toystack.io/))

2. Sign up using your Github account.

3. Once signed in, authorize toystack application to access your Github account.

4. On the dashboard, click on "Add New Repository" button.

5. On Connect a repository screen, click on "Sync with Github" button and then click on install button. This will install Toystack app on Github. Then click the install button.

6. Go back to Toystack site, you will now see the repository added. Click on "Import" button to import the code to Toystock.

7. Configure the Project settings. Next, Activate the repository.

8. Click on "Deploy from a branch" button to deploy the code. Select your branch and deployment validity.

9. Click on Deploy button. This will deploy the code.

10. To view the logs and get the application URL, click on deployment details. Access the application through URL displayed in the logs.
