# Ruby-EKS-Project
A Ruby on Rails Project application deployed using EKS (Kubernetes) and Dockerized with Docker Compose. This application is made up of a web service and a PostgeSQL service.

## Step 1 Containerize your Rails Application
Clone Rails application

git clone git@github.com:jasonswett/boats.git

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

