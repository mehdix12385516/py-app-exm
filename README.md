# Python Flask - Demo Web Application

This is a simple Python Flask web application. The app provides system information and a realtime monitoring screen with dials showing CPU, memory, IO and process information.

The app has been designed with cloud native demos & containers in mind, in order to provide a real working application for deployment, something more than "hello-world" but with the minimum of pre-reqs. It is not intended as a complete example of a fully functioning architecture or complex software design.

Typical uses would be deployment to Kubernetes, demos of Docker, CI/CD (build pipelines are provided), deployment to cloud (Azure) monitoring, auto-scaling

## Screenshot

![screen](https://user-images.githubusercontent.com/14982936/30533171-db17fccc-9c4f-11e7-8862-eb8c148fedea.png)


## Building & Running Locally

### Pre-reqs

- Be using Linux, WSL or MacOS, with bash, make etc
- [Python 3.8+](https://www.python.org/downloads/) - for running locally, linting, running tests etc
- [Docker](https://docs.docker.com/get-docker/) - for running as a container, or image build and push

Clone the project to any directory where you do development work

```
git clone https://github.com/benc-uk/python-demoapp.git
```

### Make-app

To Make application working locally in linux platform, you may flow the instructins below:

```text
- Install python 
- pip install --no-cache-dir -r requirements.txt 
- gunicorn -b 0.0.0.0:5000 run:app
- Then navigate to localhost:5000


```

To Make application working for docker platform, you may flow the instructins below:

```text
- Use a python Image ( <= 3.9 )
- Move the root directory of the application as it will the base of you installation
- Copy the requirements.txt inside the docker build ENV (root directory of the application)
- Copy run.py inside the docker build ENV (root directory of the application)
- Copy the folder /app into the same location as befor /app
- Install the requirements.txt for the application based on this file, (pip install --no-cache-dir -r requirements.txt)
- Expose the port 5000
- Redirect the EntryPoint to gunicorn application with the nessesary flags

```

# Containers

Public container image is [available on GitHub Container Registry](https://github.com/users/benc-uk/packages/container/package/python-demoapp)

Run in a container with:

```bash
docker run --rm -it -p 5000:5000 ghcr.io/benc-uk/python-demoapp:latest
```


## Running in Azure App Service (Windows)

Just don't flow this documentation but you should use "pip install waitress" rather than "gunicorn" then :

```bash
waitress-serve --listen=127.0.0.1:5000 run:app'
```