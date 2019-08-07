# Orchestrating the Cloud with Kubernetes 

## Overview

In this lab you will learn how to:

* Provision a complete [Kubernetes](http://kubernetes.io/) cluster using [Kubernetes Engine](https://cloud.google.com/container-engine).
* Deploy and manage Docker containers using kubectl.
* Break an application into microservices using Kubernetes' Deployments and Services.

Kubernetes is all about applications. In this part of the lab you will use an example application called "app" to complete the labs.

> [App](https://github.com/kelseyhightower/app) is hosted on GitHub and provides an example 12-Factor application. During this lab you will be working with the following Docker images:
>
> * [kelseyhightower/monolith](https://hub.docker.com/r/kelseyhightower/monolith) - Monolith includes auth and hello services.
> * [kelseyhightower/auth](https://hub.docker.com/r/kelseyhightower/auth) - Auth microservice. Generates JWT tokens for authenticated users.
> * [kelseyhightower/hello](https://hub.docker.com/r/kelseyhightower/hello) - Hello microservice. Greets authenticated users.
> * [ngnix](https://hub.docker.com/_/nginx) - Frontend to the auth and hello services.


Kubernetes is an open source project (available on [kubernetes.io](http://kubernetes.io/)) which can run on many different environments, from laptops to high-availability multi-node clusters, from public clouds to on-premise deployments, from virtual machines to bare metal.

For this lab, using **a managed environment** such as Kubernetes Engine allows you to focus on experiencing Kubernetes rather than setting up the underlying infrastructure.

## Setup and Requirements

### Qwiklabs setup

#### Before you click the Start Lab button

Read these instructions. Labs are timed and you cannot pause them. The timer, which starts when you click Start Lab, shows how long Cloud resources will be made available to you.

This Qwiklabs hands-on lab lets you do the lab activities yourself in a real cloud environment, not in a simulation or demo environment. It does so by giving you new, temporary credentials that you use to sign in and access the Google Cloud Platform for the duration of the lab.

#### What you need

To complete this lab, you need:

* Access to a standard internet browser (Chrome browser recommended).
* Time to complete the lab.

***Note:*** If you already have your own personal GCP account or project, do not use it for this lab.

### Google Cloud Platform Console

#### How to start your lab and sign in to the Console

1. Click the **Start Lab** button. If you need to pay for the lab, a pop-up opens for you to select your payment method. On the left is a panel populated with the temporary credentials that you must use for this lab.
2. Copy the username, and then click **Open Google Console**. The lab spins up resources, and then opens another tab that shows the **Choose an account page**.
   ***Tip:*** Open the tabs in separate windows, side-by-side.
3. On the Choose an account page, click **Use Another Account**.
4. The Sign in page opens. Paste the username that you copied from the Connection Details panel. Then copy and paste the password.
   ***Important:*** You must use the credentials from the Connection Details panel. Do not use your Qwiklabs credentials. If you have your own GCP account, do not use it for this lab (avoids incurring charges)
5. Click through the subsequent pages:

* Accept the terms and conditions.
* Do not add recovery options or two-factor authentication (because this is a temporary account).
* Do not sign up for free trials.

After a few moments, the GCP console opens in this tab.

> **Note:** You can view the menu with a list of GCP Products and Services by clicking the **Navigation menu** at the top-left, next to "Google Cloud Platform".

### Activate Google Cloud Shell

**Google Cloud Shell** is a **virtual machine that is loaded with development tools**. It offers a persistent 5GB home directory and runs on the Google Cloud. Google Cloud Shell provides **command-line access** to your GCP resources.

1. In GCP console, on the top right toolbar, click the Open Cloud Shell button.
2. In the dialog box that opens, click **START CLOUD SHELL**:
  > You can click "START CLOUD SHELL" immediately when the dialog box opens. 
  
  It takes a few moments to provision and connect to the environment. When you are connected, you are already authenticated, and the project is set to your *PROJECT_ID*. For example:
  
  **gcloud** is the command-line tool for Google Cloud Platform. It comes pre-installed on Cloud Shell and support tab-completion.
  
  You can list the active account name with this command:
  ```
  gcloud auth list
  ```
  
  
  Output:
  ```
  Credentialed accounts:
  - <myaccount>@<mydomain>.com (active)
  ```
  
  
  Example output:
  ```
  Credentialed accounts:
  - google1623327_student@qwiklabs.net
  ```
  
  
  You can list the project ID with this command:
  ```
  gcloud config list project
  ```
  
  
  Output:
  ```
  [core]
  project = <projectID>
  ```
  
  
  Example output:
  ```
  [core]
  project = qwiklabs-gcp-44776a13dea667a6
  ```
  
  
  > Full documentation of **gcloud** is available on [Google Cloud gcloud Overview](https://cloud.google.com/sdk/gcloud)
  
## Google Kubernetes Engin

In the cloud shell environment type the following command to set the zone:

```
gcloud config set compute/zone us-central1-b
```

After you set the zone, start up a cluster for use in this lab:

```
gcloud container clusters create io
```

> **Note:** It will take a while to create a cluster - Kubernetes Engine is provisioning a few Virtual Machines behind the scenes for you to play with!

## Get the sample code

Clone the GitHub repository from the Cloud Shell command line:

```
git clone https://github.com/googlecodelabs/orchestrate-with-kubernetes.git
```

```
cd orchestrate-with-kubernetes/kubernetes
```

List the files to see what you're working with:

```
ls
```

The sample has the following layout:

```
deployments/  /* Deployment manifests */
  ...
nginx/        /* nginx config files */
  ...
pods/         /* Pod manifests */
  ...
services/     /* Services manifests */
  ...
tls/          /* TLS certificates */
  ...
cleanup.sh    /* Cleanup script */
```

Now that you have the code -- it's time to give Kubernetes a try!

## Quick Kubernetes Demo

The easiest way to get started with Kubernetes is to use the `kubectl create` command. Use it to launch a single instance of the nginx container:

```
kubectl create deployment nginx --image=nginx:1.10.0
```

Kubernetes has created a deployment -- more about deployments later, but for now all you need to know is that deployments keep the pods up and running even when the nodes they run on fail.

In Kubernetes, all containers run in a pod. Use the `kubectl get pods` command to view the running nginx container:

```
kubectl get pods
```

Once the nginx container is running you can expose it outside of Kubernetes using the `kubectl expose` command:

```
kubectl expose deployment nginx --port 80 --type LoadBalancer
```

So what just happened? Behind the scenes Kubernetes created an external Load Balancer with a public IP address attached to it. Any client who hits that public IP address will be routed to the pods behind the service. In this case that would be the nginx pod.

List our services now using the `kubectl get services` command:

```
kubectl get services
```

> **Note:** It may take a few seconds before the `ExternalIP` field is populated for your service. This is normal -- just re-run the `kubectl get services` command every few seconds until the field populates.

Add the External IP to this command to hit the Nginx container remotely:

```
curl http://<External IP>:80
```

And there you go! Kubernetes supports an easy to use workflow out of the box using the `kubectl` run and expose commands.

### Test Completed Task

Click Check my progress below to check your lab progress. If you successfully created Kubernetes cluster and deploy Nginx container, you'll see an assessment score.

[] Create a Kubernetes cluster and launch Nginx container 

Now that you've seen a quick tour of kubernetes, it's time to dive into each of the components and abstractions.

## Pods

At the core of Kubernetes is the [Pod](http://kubernetes.io/docs/user-guide/pods/).

Pods represent and hold a collection of one or more containers. Generally, if you have multiple containers with a hard dependency on each other, you package the containers inside a single pod.

![Pods](Kubernetes_02_01.jpeg)

In this example there is a pod that contains the monolith and nginx containers.

Pods also have [Volumes](http://kubernetes.io/docs/user-guide/volumes/). Volumes are data disks that live as long as the pods live, and can be used by the containers in that pod. Pods provide a shared namespace for their contents which means that the two containers inside of our example pod can communicate with each other, and they also share the attached volumes.

Pods also share a network namespace. This means that there is one IP Address per pod.

Now let's take a deeper dive into pods.

## Creating Pods

Pods can be created using pod configuration files. Let's take a moment to explore the monolith pod configuration file. Run the following:

```
cat pods/monolith.yaml
```

The output shows the open configuration file:

```
apiVersion: v1
kind: Pod
metadata:
  name: monolith
  labels:
    app: monolith
spec:
  containers:
    - name: monolith
      image: kelseyhightower/monolith:1.0.0
      args:
        - "-http=0.0.0.0:80"
        - "-health=0.0.0.0:81"
        - "-secret=secret"
      ports:
        - name: http
          containerPort: 80
        - name: health
          containerPort: 81
      resources:
        limits:
          cpu: 0.2
          memory: "10Mi"
```

There's a few things to notice here. You'll see that:

* your pod is made up of one container (the monolith).
* you're passing a few arguments to our container when it starts up.
* you're opening up port 80 for http traffic.
