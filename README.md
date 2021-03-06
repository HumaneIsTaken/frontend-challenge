# Basic Phone Catalogue

This is a very basic phone catalogue that pulls data from an API with one endpoint (/phones).

The api folder contains all the code necessary to run the node.js Phones API, whilst the app/phone-catalogue folder contains everything to get the React App going.

## Setup and Usage
This solution can be set up one of two ways. Locally or via **Docker**.

### Local Setup
Firstly, we set up the Phones API to serve the phones.json to the React App. Go to the **/api** folder.
```
$ npm install
$ node server.js
Phone Catalogue API server up on port 3001
```
We install dependencies and run the API with **node server.js**. This will host the API on http:/localhost:3001

With that running, we now start the React application. Go to the **/app/phone-catalogue** folder and run the following.
```
$ npm install
$ npm start
```
We (again) install the required dependencies and run the app with **npm start**. This will host it on http:/localhost:3000

If you wish to run the test suite for the React Application, run **npm test** 
```
$ npm test
```
Jest will start up and go through the provided tests. NOTE - Test coverage has been reduced in latest commit.

### Docker Setup
To setup this solution via docker, we are interested in the following images.
- jastor7/docker-test:phones-api
- jastor7/docker-test:phones-app

_Both can be seen in the public DockerHub repo here (https://cloud.docker.com/repository/registry-1.docker.io/jastor7/docker-test)_

To setup and run a container for the phones-api run the following.
```
$ docker run --name jastor-phones-api -p 3001:3001 -d jastor7/docker-test:phones-api
```
This will setup the container (named jastor-phones-api) and make it reachable via http://localhost:3001.

**_NOTE: It is important to make sure that the API is reachable via port 3001. In the future, the port will not be hardcoded._**

Likewise, to setup and run a container for the phones-app, run the following.
```
$ docker run --name jastor-phones-app -p 80:3001 -d jastor7/docker-test:phones-app
```
This will setup another container (named jastor-phones-app) and make it reachable via http://localhost.

The following commands might be handy for the docker containers.
```
$ docker start $CONTAINER_NAME
$ docker container stop $CONTAINER_NAME
$ docker container rm $CONTAINER_NAME
```
Note that testing isn't available via docker images, and it will have to be performed locally.
