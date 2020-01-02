![cover](https://img3.doubanio.com/view/subject/l/public/s32278660.jpg)

    作者: Brendan Burns / Joe Beda / Kelsey Hightower
    出版社: O'Reilly Media
    副标题: Dive into the Future of Infrastructure
    出版年: 2019-10-29
    页数: 278
    定价: USD 69.99
    装帧: Paperback
    ISBN: 9781492046530

[豆瓣链接](https://book.douban.com/subject/33393703/)

[oreilly.com](https://learning.oreilly.com/library/view/kubernetes-up-and/9781492046523/)

- [Introduction](#introduction)
  - [Velocity](#velocity)
    - [The Value of Immutability](#the-value-of-immutability)
    - [Declarative Configuration](#declarative-configuration)
    - [Self-Healing Systems](#self-healing-systems)
  - [Scaling Your Service and Your Teams](#scaling-your-service-and-your-teams)
    - [Decoupling](#decoupling)
    - [Easy Scaling for Applications and Clusters](#easy-scaling-for-applications-and-clusters)
    - [Scaling Development Teams with Microservices](#scaling-development-teams-with-microservices)
    - [Separation of Concerns for Consistency and Scaling](#separation-of-concerns-for-consistency-and-scaling)
  - [Abstracting Your Infrastructure](#abstracting-your-infrastructure)
  - [Efficiency](#efficiency)
- [Creating and Running Containers](#creating-and-running-containers)
  - [Container Images](#container-images)
    - [The Docker Image Format](#the-docker-image-format)
  - [Building Application Images with Docker](#building-application-images-with-docker)
    - [Dockerfiles](#dockerfiles)
  - [Multistage Image Builds](#multistage-image-builds)
  - [Storing Images in a Remote Registry](#storing-images-in-a-remote-registry)

# Introduction
There are many reasons why people come to use containers and container APIs like Kubernetes, butwe believe they can all be traced back to one of these benefits:

- Velocity
- Scaling (of both software and teams)
- Abstracting your infrastructure
- Efficiency

## Velocity
It is important to note, however, that velocity is not defined in terms of simply raw speed. While your users are always looking for iterative improvement,they are more interested in a highly reliable service.

Consequently, velocity is measured not in terms of the raw number of features you can ship per hour or day, but rather in terms of the number of things you can ship while maintaining a highly available service.

In this way, containers and Kubernetes can provide the tools thatyou need to move quickly, while staying available. The core concepts that enable this are:

- Immutability
- Declarative configuration
- Online self-healing systems

### The Value of Immutability
Containers and Kubernetes encourage developers to build distributed systemsthat adhere to the principles of immutable infrastructure.

### Declarative Configuration
Everything in Kubernetes is a declarative configuration object that represents the desired state of the system.

Much like mutable versus immutable infrastructure, `declarative configuration` is an alternative to `imperative configuration`,where the state of the world is defined by the execution of a series of instructions rather than a declaration of the desired state of the world. While imperative commands define actions, declarative configurations define state.

The combination of declarative state stored in a version control system andthe ability of Kubernetes to make reality match this declarative state makesrollback of a change trivially easy.

### Self-Healing Systems
Kubernetes is an online, self-healing system. When it receives adesired state configuration, it does not simply take a set of actions to make the currentstate match the desired state a single time. It **continuously** takes actions toensure that the current state matches the desired state.

## Scaling Your Service and Your Teams
### Decoupling
In a decoupled architecture, each component is separated from other components bydefined APIs and service load balancers.APIs and load balancers isolate each piece of the system from the others. APIs provide a buffer between implementer and consumer, and load balancers provide a buffer between running instances of each service.

Decoupling components via load balancers makes it easy to scale the programs that make up your service,because increasing the size (and therefore the capacity) of the program can bedone without adjusting or reconfiguring any of the other layers of your service.

Decoupling servers via APIs makes it easier to scale the development teams because each team can focus on a single, smaller microservice with a comprehensible surface area. Crisp APIs between microservices limit the amount of cross-team communication overhead required to build and deploy software. This communication overhead is often the major restricting factor when scaling teams.

### Easy Scaling for Applications and Clusters
Concretely, when youneed to scale yourservice, the immutable, declarative nature of Kubernetes makes this scalingtrivial to implement.

### Scaling Development Teams with Microservices
Kubernetes provides numerousabstractions and APIs that make it easier to build these decoupled microservice architectures:

- **Pods**, or groups of containers, can group together container images developed by different teams into a single deployable unit.
- Kubernetes **services** provide load balancing, naming, and discovery to isolate one microservice from another.
- **Namespaces** provide isolation and access control, so that each microservice can control the degree to which other services interact with it.
- **Ingress** objects provide an easy-to-use frontend that can combine multiplemicroservices into a single externalized API surface area.

### Separation of Concerns for Consistency and Scaling
![](https://learning.oreilly.com/library/view/kubernetes-up-and/9781492046523/assets/kur2_0101.png)

Figure 1-1. An illustration of how different operations teams are decoupled using APIs

## Abstracting Your Infrastructure
The move to application-oriented container APIs like Kubernetes has two concrete benefits. First, as we described previously, it separates developers from specific machines. This makes the machine-oriented IT role easier,since machines can simply be added in aggregate to scale the cluster, and in the context of the cloud it also enables a high degree of portability since developers are consuming a higher-level API that is implemented in terms of the specific cloud infrastructure APIs.

When your developers build their applications in terms of container images and deploy them in terms of portable Kubernetes APIs, transferring your application between environments, or even running in hybrid environments, is simply a matter of sending the declarative config to a new cluster.

## Efficiency
Because developers no longer think in terms of machines, theirapplications can be colocated on the same machines without impacting the applications themselves. This means that tasks from multiple users can be packed tightly onto fewer machines.

# Creating and Running Containers
## Container Images
A **container image** is a binarypackage that encapsulates all of the files necessary to run a program inside ofan OS container. Depending on how you first experiment with containers, you willeither build a container image from your local filesystem or download apreexisting image from a **container registry**.

### The Docker Image Format
The phrases “Docker image format” and “container images” may be a bit confusing.The **image** isn’t a single file but rather a specification for a manifest file thatpoints to other files. The manifest and associated files are often treated byusers as a unit. The level of indirection allows for more efficient storage and transmittal. Associated with this format is an API for uploading and download ingimages to an image registry.

**Container images** are constructed with a series of filesystem layers, where each layer inherits and modifies the layers that came before it. To help explain this in detail, let’s build some containers. Note that for correctness the ordering of the layers should be bottom up, but for ease of understanding we take the opposite approach:

```
.
└── container A: a base operating system only, such as Debian    
    └── container B: build upon #A, by adding Ruby v2.1.10    
    └── container C: build upon #A, by adding Golang v1.6
```

At this point we have three containers: A, B, and C. B and C are forked from Aand share nothing besides the base container’s files. Taking it further, we canbuild on top of B by adding Rails (version 4.2.6). We may also want to support a legacy application that requires an older version of Rails (e.g., version3.2.x). We can build a container image to support that application based on Balso, planning to someday migrate the app to version 4:

```
. (continuing from above)
└── container B: build upon #A, by adding Ruby v2.1.10
    └── container D: build upon #B, by adding Rails v4.2.6
    └── container E: build upon #B, by adding Rails v3.2.x
```

Conceptually, each container image layer builds upon a previous one. Each parent reference is a pointer. While the example here is a simple set of containers,other real-world containers can be part of a larger extensive directed acyclic graph.

`Container` images are typically combined with a container configuration file,which provides instructions on how to set up the container environment and execute an application entry point. The container configuration often includes information on how to set up networking, namespace isolation, resource constraints (cgroups), and what syscall restrictions should be placed on arunning container instance. The container root filesystem and configuration file are typically bundled using the Docker image format.

Containers fall into two main categories:

- System containers
- Application containers

## Building Application Images with Docker
### Dockerfiles
A Dockerfile can be used to automate thecreation of a Docker container image.

Let’s start by building an application image for a simple Node.js program.

Example 2-1. package.json

```json
{ 
    "name": "simple-node",
    "version": "1.0.0",  
    "description": "A sample simple application for Kubernetes Up & Running",  
    "main": "server.js",  
    "scripts": 
    {    
        "start": "node server.js"  
    },  
    "author": ""
}
```

Example 2-2. server.js

```js
var express = require('express');
var app = express();
app.get('/', function (req, res) {  
    res.send('Hello World!');
    });
app.listen(3000, function () {  
    console.log('Listening on port 3000!');  
    console.log('  http://localhost:3000');
    });
```

Example 2-3. .dockerignore

```
node_modules
```

Example 2-4. Dockerfile

```dockerfile
# Start from a Node.js 10 (LTS) image 1
FROM node:10

# Specify the directory inside the image in which all commands will run 2
WORKDIR /usr/src/app

# Copy package files and install dependencies 3
COPY package*.json ./
RUN npm install

# Copy all of the app files into the image COPY . . 4

# The default command to run when starting the container 5
CMD [ "npm", "start" ]
```

1. Every Dockerfile builds on other container images. This line specifies thatwe are starting from the node:10 image on the Docker Hub.  This is apreconfigured image with Node.js 10.
2. This line sets the work directory, in the container image, for all followingcommands.
3. These two lines initialize the dependencies for Node.js.  First we copy thepackage files into the image. This will include package.json andpackage-lock.json. The RUN command then runs the correct command in thecontainer to install the necessary dependencies.
4. Now we copy the rest of the program files into the image.  This will include everything except node_modules, as that is excluded via the .dockerignore file.
5. Finally, we specify the command that should be run when the container is run.

Run the following command to create the simple-node Docker image:

```
$ docker build -t simple-node .
```

When you want to run this image, you can do it with the following command. You cannavigate to http://localhost:3000 to access the program running in thecontainer:

```
$ docker run --rm -p 3000:3000 simple-node
```

## Multistage Image Builds
With multistage builds, rather than producing a single image, a Docker file canactually produce multiple images. Each image is considered a stage. Artifacts can be copied from preceding stages to the current stage.

To illustrate this concretely, we will look at how to build our example application, kuard. This is a somewhat complicated application that involves a React.js frontend (with its own build process) that then gets embedded into a Go program. The Go program runs a backend API server that the React.js frontend interacts with.

A simple Dockerfile might look like this:

```dockerfile
FROM golang:1.11-alpine

# Install Node and NPM
RUN apk update && apk upgrade && apk add --no-cache git nodejs bash npm

# Get dependencies for Go part of build
RUN go get -u github.com/jteeuwen/go-bindata/...
RUN go get github.com/tools/godep

WORKDIR /go/src/github.com/kubernetes-up-and-running/kuard

# Copy all sources in
COPY . .

# This is a set of variables that the build script expects
ENV VERBOSE=0
ENV PKG=github.com/kubernetes-up-and-running/kuard
ENV ARCH=amd64
ENV VERSION=test

# Do the build. This script is part of incoming sources.
RUN build/build.sh
CMD [ "/go/bin/kuard" ]
```

This Dockerfile produces a container image containing a static executable, butit also contains all of the Go development tools and the tools to build the React.js frontend and the source code for the application, neither of which are needed by the final application. The image, across all layers, adds up to over 500 MB.

To see how we would do this with multistage builds, examine this multistage Dockerfile:

```dockerfile
# STAGE 1: Build
FROM golang:1.11-alpine AS build

# Install Node and NPM
RUN apk update && apk upgrade && apk add --no-cache git nodejs bash npm

# Get dependencies for Go part of build
RUN go get -u github.com/jteeuwen/go-bindata/...
RUN go get github.com/tools/godep

WORKDIR /go/src/github.com/kubernetes-up-and-running/kuard

# Copy all sources inCOPY . .

# This is a set of variables that the build script expects
ENV VERBOSE=0
ENV PKG=github.com/kubernetes-up-and-running/kuard
ENV ARCH=amd64
ENV VERSION=test

# Do the build. Script is part of incoming sources.
RUN build/build.sh

# STAGE 2: Deployment
FROM alpine

USER nobody:nobody
COPY --from=build /go/bin/kuard /kuard

CMD [ "/kuard" ]
```

This Dockerfile produces two images. The first is the build image, whichcontains the Go compiler, React.js toolchain, and source code for the program. Thesecond is the deployment image, which simply contains the compiled binary.Building a container image using multistage builds can reduce your finalcontainer image size by hundreds of megabytes and thus dramatically speed upyour deployment times, since generally, deployment latency is gated on networkperformance. The final image produced from this Dockerfile is somewhere around20 MB.

You can build and run this image with the following commands:

```
$ docker build -t kuard .
$ docker run --rm -p 8080:8080 kuard
```

## Storing Images in a Remote Registry




















