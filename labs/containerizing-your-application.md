# Containerizing your application

In this lab you will build your application, run it locally, and then package it into a container. Containers are more lightweight than a full virtual machine for your app and they package your application so that it runs the same across different environments such as development, QA, and production.

## Get the application code

The first hurdle to is the application itself.  How do you write it?  How do you deploy it?

First set up the code and the Go build environment. For this lab we'll be using an example app from GitHub: [kelseyhightower/app](https://github.com/kelseyhightower/app).
```bash
$ mkdir -p $GOPATH/src/github.com/kelseyhightower
$ cd ~
$ git clone https://github.com/kelseyhightower/app
```

## Build the app

Now let's build the app as a static binary and test its functionality.
```bash
$ cd app/monolith
$ go build -tags netgo -ldflags "-extldflags '-lm -lstdc++ -static'" .
$ ./monolith --http :10180 --health :10181 &
$ curl http://127.0.0.1:10180
$ curl http://127.0.0.1:10180/secure
$ curl http://127.0.0.1:10180/login -u user
# Yes the password is 'password'
$ curl http://127.0.0.1:10180/secure -H "Authorization: Bearer <token>"
```

Once we have a binary, we can use Docker to package and distribute it.
```bash
$ docker build -t monolith:1.0.0 .
# Optionally push to Docker Hub using docker push <your_repo>/monolith:1.0.0
$ docker run -d monolith:1.0.0
$ docker ps
$ docker inspect <container-id>
$ curl http://<docker-ip>
$ docker stop <container-id>
$ docker rm <container-id>
$ docker rmi monolith:1.0.0
```
