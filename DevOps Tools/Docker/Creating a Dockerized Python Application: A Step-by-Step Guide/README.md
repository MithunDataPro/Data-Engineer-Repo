# Creating a Dockerized Python Application: A Step-by-Step Guide

In this guide, we'll create a simple Python application, Dockerize it, and run it on a custom port using Docker. Let's break this down into a few simple steps.

## Step 1: Creating the Python Application 
First, let's create a simple **Python** web application using **Flask**. Flask is a micro web framework for Python that's easy to get started with.

**Note**:
**Flask**: Flask is a lightweight web framework written in Python, designed to make it easy to build web applications and APIs. It is a microframework, meaning it is minimalistic, does not include built-in features like database integration or form handling by default, and relies on extensions to add additional functionality.


### a. Set up your project directory:
```
mkdir python-docker-app 
cd python-docker-app

```

### b. Create a Python file named app.py: 
Here's a simple web application that responds with "Hello, Docker!" when you visit the root URL.

```bash
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello, Docker!'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)

```

### c. Create a requirements file: 
Save the following in a file named requirements.txt. This file lists the Flask library as a dependency.

```
Flask==2.0.1

```
