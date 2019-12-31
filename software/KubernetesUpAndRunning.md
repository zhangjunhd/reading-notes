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
























