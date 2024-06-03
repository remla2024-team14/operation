# Submission Document

## A5: Istio Service Mesh

- Operation: https://github.com/remla2024-team14/model-training/tree/a5
- App: https://github.com/remla2024-team14/app/tree/a5
- Model-service: https://github.com/remla2024-team14/model-service/tree/a5

Notes:
- The README in operation contains info on the Istio deployment (see "How to: Istio deployment") and additional use case (Egress for controlling external requests)
- Parts not implemented:
  - Stabilization of user requests
  - Deployment of two versions of a Service (note we did deploy two versions of our App, but we did not fully understand this requirement)

## A4: ML Testing

- Model-training: https://github.com/remla2024-team14/model-training/tree/a4 

Notes:
- The folder and file names under the `/tests` directory indicate the ML Testing category e.g. Feature and Data, Model Development, ML Infrastructure, Monitoring
- Our README (section "PyTest for ML Testing") explains our test setup and display our obtained results + adequacy metrics
  - Currently, we have line coverage as adequacy metric but are planning on adding more

## A3: Operate a Webapp

- Operation: https://github.com/remla2024-team14/operation/tree/a3
- App: https://github.com/remla2024-team14/app/tree/a3

Notes:
- See the README inside the `operation` repo for high-level project information and instructions on how to get the app running with Docker-compose
- See the READMEs of the other repositories for specific information
- The following sub-tasks have not been implemented: Prometheus AlertManager


## A2: Images, Releases and Provisioning

operation: https://github.com/remla2024-team14/operation/tree/a2

- Model training: https://github.com/remla2024-team14/model-training/tree/a2
- Model service: https://github.com/remla2024-team14/model-service/tree/a2
- App: https://github.com/remla2024-team14/app/tree/a2
- Lib-ML: https://github.com/remla2024-team14/lib-ml/tree/a2
- Lib-version: https://github.com/remla2024-team14/lib-version/tree/a2

Notes:
- See the README inside the `operation` repo for high-level project information and instructions on how to get the app running with Docker-compose
- See the READMEs of the other repositories for specific information
- The following sub-tasks have not been implemented: Swagger


## A1: ML Config Management

operation: https://github.com/nadinekuo/URL-Fishing-CS4295/tree/v0.0.1

- Download data: https://github.com/nadinekuo/URL-Fishing-CS4295/blob/v0.0.1/src/get_data.py

- Tokenize data: https://github.com/nadinekuo/URL-Fishing-CS4295/blob/v0.0.1/src/tokenize_data.py

- Model training: https://github.com/nadinekuo/URL-Fishing-CS4295/blob/v0.0.1/src/define_train_model.py

- Model prediction: https://github.com/nadinekuo/URL-Fishing-CS4295/blob/v0.0.1/src/predict.py

Notes:
- We implemented all subtasks as specified in the assignment
- See the README for instructions on how to run the project (with DVC), as well as info on our code quality audit