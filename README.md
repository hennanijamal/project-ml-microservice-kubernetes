[![CircleCI](https://circleci.com/gh/hennanijamal/project-ml-microservice-kubernetes.svg?style=svg)](https://circleci.com/gh/hennanijamal/project-ml-microservice-kubernetes)

## Project Overview

In this project, you will apply the skills you have acquired in this course to operationalize a Machine Learning Microservice API. 

You are given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

Your project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:
* Test your project code using linting
* Complete a Dockerfile to containerize this application
* Deploy your containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Upload a complete Github repo with CircleCI to indicate that your code has been tested

You can find a detailed [project rubric, here](https://review.udacity.com/#!/rubrics/2576/view).

**The final implementation of the project will showcase your abilities to operationalize production microservices.**

---

## Setup the Environment

* Create a virtualenv and activate it
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

#### Notes on running Shell file
* If you are experiencing the following issues running the shell files, 
    ``` 
    /usr/bin/env: 'bash\r': No such file or directory
    ``` 
    or

    ``` 
    bash: ./run_docker.sh: /usr/bin/env: bad interpreter: No such file or directory    
    ``` 
    As a quick fix, you can run this

    ```
    sed $'s/\r$//' ./shellFileName.sh > ./shellFileName.unix.sh
    ```

    and run the shellFileName.unix.sh instead. Replace shellFileName by the shell file you are trying to run.

    Get more details here https://github.com/Ardakilic/backmeup/issues/5.
    
  
If you are unable to resolve these issues with the suggestion above, try running the commands from the shell file manually on the terminal.

###  Running `web app`

1. Afer successfully running the above files in Docker or Kubernnerts, run localhost:8000 on your browser.
2. Run the `./make_predictions.sh` from the terminal (the terminal here is different form the one used to deploy the app).
3. You can now view the logs in a seperate terminal with the commands;
    - `docker logs containerID` (when deployed on docker. Get the containerID with the command `docker ps -l`)
    - `kubectl logs project-ml-microservice-kubernetes` (when deployed on kubernetes).

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
* run `minikube start` (make sure you have a virtual machine installed e.g Virtual box)
* run `./run_kubernetes.sh`
* Create Flask app in Container
* Run via kubectl

### Include Files

***.cicleci/config.yml***: This files contains code to test the project on CircleCi

***output_txt_files/docker_out.txt***: File with logs including predictions run in docker.

***output_txt_files/kubernetes_out.txt***: File with logs including predictions run in kubernetes.

***requirements.txt***: File includes dependencies that are required for this project

***app.py***: This file contains the flask app codes.

***run_docker.sh***: This shell script run and build a docker image locally and runs the flask app from the docker image.

***run_kubernetes.sh***: This shell script runs the docker image from within a kubernetes cluster and deploys the flask app.

***uploade_docker.sh***: This shell script pushes the local docker image to my docker repository.

***make_predictions.sh***: This shell script is responsible for sending some input data to your containerized application via the appropriate port (port 8000 in this case).

***Makefile***: This contains intructions to setup your system with the `make` command.

***Dockerfile***: Docker can build images automatically by reading the instructions from a Dockerfile.

***README.md***: This file contains instructions on how to setup and run the project.

***BugsReport.md***: This file contains a brief report on the bugs fund while running the project and possible fixes.

#### NOTE!!:
You will have to modify the docker image id in line 15 of the `upload_docker.sh` file with your own image ID obtained when you create a local docker image. Get the imageID with the command `docker image ls`
