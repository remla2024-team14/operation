# Operation: URL Phishing (REMLA Team 14)
Central repository that contains all information about running the URL Phishing application and operating the cluster.

Later, this repository will also contain information about provisioning and deployment (Vagrant, Ansible, Docker Compose, Kubernetes etc.).
For now, this repository merely contains a `docker-compose` file, serving as the most simple way to deploy the application for a showcase.



## High-level Architecture

This project contains several independent components which have their dedicated repositories - see the reference architecture below.

Our `app` and `model-service` are released as two separate container images (can be deployed separately from each other).

![alt text](images/arch.png)

_Source: REMLA 2023/2024 Assignment 2_


### Model-service

_Repository link: https://github.com/remla2024-team14/model-service_

- Represents a wrapper service for the released ML model
- Offers a REST API to expose the trained model to other components and make it scalable
- Our ML model is released as well, which can be exchangeable
- Depends on `lib-ml` through PyPi
- Automatic release to GitHub's container registry, with automatic versioning


### Model-training

_Repository link: https://github.com/remla2024-team14/model-training_

- Contains the ML training pipeline for our URL Phising detection application
- All pre-processing logic is powered by our custom library `lib-ml`


### Lib-ml

_Repository link: https://github.com/remla2024-team14/lib-ml_

- Contains the pre-processing logic for data used for ML training and querying incl. tokenization
- Versioned automatically
- Automatically released in PyPi package registry


### Lib-version

_Repository link: https://github.com/remla2024-team14/lib-version_

- A version-aware library that can be asked for the version of the library (see the class `VersionUtil`)
- The library is released automatically to PyPi


### App-frontend and -service

_Repository link: https://github.com/remla2024-team14/app_

- Queries the `model-service` through REST requests, allowing for users to enter URL input for phishing detection
- Depends on the `lib-version` through PyPi, allowing for displaying its version on the main web page
- The URL of the `model-service` is configurable as an environment variable


For further details about the respective repositories, please navigate to their specific project READMEs.

## Installations

1. Ensure you have Docker installed: refer to https://docs.docker.com/compose/install/.

2. Clone this central repository.

```
git clone https://github.com/remla2024-team14/operation.git
```

3. Inside this project, clone the following two projects it serves.

```
git clone https://github.com/remla2024-team14/model-service.git
git clone https://github.com/remla2024-team14/app.git
```

This is what your project will look like roughly:

```
operation
│   README.md
│   docker-compose.yml   
│
└──- app
│   │   app.py
│   │   Dockerfile
|   |    ...
│   │
│   └───templates
│       │   ...
│   
└─── model-service
    │   app.py
    │   Dockerfile
    |     ...
```


## How to: Start the Application

From your project's root, simply run the commands below. This is the power of Docker Compose!

```
docker-compose build     # In case the Dockerfiles have been modified
docker-compose up -d
```

Here, `-d` instructs Docker to start the container as a background daemon.


Upon running `docker ps`, you will see the following two containers being active:

```
CONTAINER ID   IMAGE                     COMMAND           CREATED          STATUS          PORTS                    NAMES
a7988dbfb1c6   operation-app             "python app.py"   35 seconds ago   Up 34 seconds   0.0.0.0:3000->8000/tcp   operation-app-1
ea97335d9dfd   operation-model-service   "flask run"       36 seconds ago   Up 34 seconds   0.0.0.0:5001->5000/tcp   operation-model-service-1
```

Now when you navigate to your localhost (e.g. `http://localhost:3000/`) that serves the `app`, you see the UI of our URL Phishing Detection application:

<img src="images/interface-app.png" alt="drawing" width="500"/>

In the form above, users can enter a URL to check, as well as select a model of choice.

To stop the application, use `docker-compose down`.

# Prometheus and Grafana

To run Prometheus locally without Helm, you need to make sure Prometheus is installed, then run `prometheus.exe --config.file=prometheus.yml`.
To run Grafana locally, just download it and it will continually run on your localhost on port 3000 (use a browser to go to 127.0.0.1:3000). Then configure a data source to the port Prometheus is running (by default, localhost:9093) and importing the dashboard JSON located in the path *grafana-dashboards/dashbard.json*.
