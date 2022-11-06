A comparision of building & running micro service architecture on OCF and EKS
===========================================================================================
This project is a comparision of steps and complexity involved in deploying an application build using microservice architecture in OCF (Open Cloud Foundry) and K8s (on EKS). The project is a modified version of a Voting App originally built by Docker team to demonstrate using containers and Docker Swarm.

Original repo (https://github.com/dockersamples/example-voting-app)



Getting started 
---------------
Download [Docker Desktop](https://www.docker.com/products/docker-desktop) for Mac or Windows. [Docker Compose](https://docs.docker.com/compose) will be automatically installed. On Linux, make sure you have the latest version of [Compose](https://docs.docker.com/compose/install/). 


Docker-compose file is included in the project. Navigate to example-voting-app and run following command to build and run it Docker desktop.

```
docker-compose up -d
```


Run the app in Kubernetes
-------------------------



Run the app in OCF
-------------------------


Architecture
-----

![Architecture diagram](architecture.png)

* A front-end web app in [Python](/vote) which lets you vote between two options
* A [Redis](https://hub.docker.com/_/redis/) queue which collects new votes
* A [.NET Core](/worker/src/Worker),  worker which consumes votes and stores them in…
* A [Postgres](https://hub.docker.com/_/postgres/)  database backed by a Docker volume
* A [Node.js](/result)  webapp which shows the results of the voting in real time




Notes
-----

The voting application only accepts one vote per client. It does not register votes if a vote has already been submitted from a client.

This isn't an example of a properly architected perfectly designed distributed app... it's just a simple 
example of the various types of pieces and languages you might see (queues, persistent data, etc), and how to 
deal with them at a basic level. 
