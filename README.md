# Ruby-EKS-Project
A Ruby on Rails Project application deployed using EKS (Kubernetes) and Dockerized with Docker Compose. This application is made up of a web service and a PostgeSQL service.

## Step 1 Containerize your Rails Application
Clone Rails application

            git clone git@github.com:jasonswett/boats.git

Make sure you have Rails installed
            rails --version
            sudo gem install rails



## Use a Dockerfile to create an image

- Dockerfile Description:


## Create a docker-compose.yml file
This describes how the multiple containers needed in the application will work together.
Each thing that Docker Compose runs is referred to as a "service". In our case, our Rails application is one service ("web") and our PostgreSQL database instance is another service ("database").

- description of docker compose contents

## Make sure to create your init.sql file
This file will create a root user once in every container the first time each is spun up.

## Edit Rails applicationconfig/database.yml 
Ensure that it points to the database instance in the other container you just described.

## Build and Run your container
            docker-compose build
The following will actually run the containers in the app.

            docker-compose up

To finish creating the app, create the database like you would for any Rails application.
docker-compose run web --> runs commands inside the specified container

            docker-compose run web rails db:create
            docker-compose run web rails db:migrate

You can open http://localhost:3000 to see your Dockerized Rails application running in the browser.
            open http://localhost:3000

## Start Here if you have a Containerized Rails Application already

## Generate a Kubernetes Secret
                bundle exec rake secret
                echo -n "sercet key"
                
Create a YAML file of the secret and save it

                apiVersion: v1
                kind: Secret
                metadata:
                name: railsapp-secrets
                type: Opaque
                data:
                secret-key-base:            OGQ0MjhlOWQyN2UzMzIzZjFiMWVjMDA4OTQ4MjAxNzQ4MDIyNGM5OTg0ZmMxMDMyN2Y5NWIwOTkwZWM0NjE3NWQ0M2Q3NTZmZDY0NGMzYmNhMzcwM2EzMzdhOTRjZWQ2OWM4NjhhYjA0NzBhYzIwMWNkMWI2YTgwYzNmODllNGE=
                database-url: bXlzcWw6Ly9kZXBsb3k6c2VjcmV0QDEyNy4wLjAuMS90b2Rv


## Create a Kubernetes Deployment File that contains an image and uses secret keys
Named this file railsapp_deployment.yaml. This file will describe the kubernetes pods and the associated services. We are adding a LoadBalancer Service.

## Installations Needed, Minikube and kubectl

## Creation and Status Commands
                kubectl create -f railsapp_secrets.yaml
                kubectl create -f railsapp_deployment.yaml
                kubectl create -f railsapp_service.yaml
                kubectl get secrets
                kubectl get deployments,pods
                kubectl get services
                minikube ip