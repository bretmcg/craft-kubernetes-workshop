# Kubernetes workshop

In this workshop you will learn how to:

* Provision Kubernetes using [Google Container Engine](https://cloud.google.com/container-engine)
* Deploy and manage Docker containers using kubectl

Kubernetes Version: 1.2.2

## Workshop setup

### Google Cloud Platform account setup
1. Navigate to https://console.cloud.google.com and login with your credentials.
1. Select your project from the project listing.
1. Click the following button to activate [Cloud Shell](https://cloud.google.com/shell/docs),
which is your "command line in the cloud" and will be used complete the labs. ![Cloud Shell Icon](https://cloud.google.com/shell/docs/images/shell_icon.png)

### Provision Kubernetes using Google Container Engine (GKE)

Kubernetes can be configured with many options and add-ons, but can be time consuming to bootstrap from the ground up. In this section you will bootstrap Kubernetes using [Google Container Engine](https://cloud.google.com/container-engine) (GKE).

In your **Cloud Shell** terminal, issue the following commands (feel free to change the zone or cluster name):

```
gcloud config set compute/zone europe-west1-b
gcloud container clusters create myk8scluster --num-nodes 3
```
### Clone repository

In your Cloud Shell environment clone the following repository.

```
git clone https://github.com/bretmcg/kubernetes-workshop.git
cd kubernetes-workshop/kubernetes
```

## Labs

Kubernetes is all about applications and in this section you will utilize the Kubernetes API to deploy, manage, and upgrade applications. In this part of the workshop you will use an example application called "app" to complete the labs.

  1. [Containerizing your application](labs/containerizing-your-application.md)
  1. [Creating and managing pods](labs/creating-and-managing-pods.md)
  1. [Monitoring and health checks](labs/monitoring-and-health-checks.md)
  1. [Managing application configurations and secrets](labs/managing-application-configurations-and-secrets.md)
  1. [Creating and managing services](labs/creating-and-managing-services.md)
  1. [Creating and managing deployments](labs/creating-and-managing-deployments.md)
  1. [Rolling out updates](labs/rolling-out-updates.md)

## Lab Docker images

[App](https://github.com/kelseyhightower/app) is hosted on GitHub and provides an example 12 Facter application. During this workshop you will be working with the following Docker images:

* [kelseyhightower/monolith](https://hub.docker.com/r/kelseyhightower/monolith) - Monolith includes auth and hello services.
* [kelseyhightower/auth](https://hub.docker.com/r/kelseyhightower/auth) - Auth microservice. Generates JWT tokens for authenticated users.
* [kelseyhightower/hello](https://hub.docker.com/r/kelseyhightower/hello) - Hello microservice. Greets authenticated users.
* [ngnix](https://hub.docker.com/_/nginx) - Frontend to the auth and hello services.

## Links

  * [Kubernetes](http://googlecloudplatform.github.io/kubernetes)
  * [gcloud Tool Guide](https://cloud.google.com/sdk/gcloud)
  * [Docker](https://docs.docker.com)
  * [etcd](https://coreos.com/docs/distributed-configuration/getting-started-with-etcd)
  * [nginx](http://nginx.org)
