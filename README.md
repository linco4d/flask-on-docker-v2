# flask-on-docker-v2 ![Dev Build](https://github.com/linco4d/flask-on-docker/actions/workflows/dev-build.yml/badge.svg)

![Proof](proof.gif)

This repository demonstrates a complete Instagram-style backend tech stack using Docker and Flask, inspired by the Dockerizing Flask with Postgres, Gunicorn, and Nginx tutorial from TestDriven.io. It contains a containerized Python/Flask web application wired up with a PostgreSQL database and configured for both development and production workflows using Docker Compose, production-grade WSGI serving with Gunicorn, and Nginx for front-facing routing and static file handling. The project includes database models, CLI commands, and seed data to help you bootstrap, build, and run an API backend in a reproducible, containerized environment that mirrors real-world deployment architecture.

This application uses Docker Compose for production deployment. The commands below allow you to build, start, and stop the application.

## To build production images:
```
docker compose -f docker-compose.prod.yml build
```
+ Builds Docker images for all services defined in the production configuration.
+ Run this after changing application code or Dockerfiles.

## To start the production environment:
```
docker compose -f docker-compose.prod.yml up -d
```
+ Creates and starts all services in detached mode (runs in the background).
+ After this, the application and its dependencies are running.

## To initialize the database:
```
docker compose -f docker-compose.prod.yml exec web python manage.py create_db
```
+ Executes a command inside the running web container.
+ Initializes or creates the application database.
+ Typically required the first time the application is started.

## To shut down the production environment:
```
docker compose -f docker-compose.prod.yml down
```
+ Stops all running containers and removes them along with the network.
+ Use this to completely stop the application.
