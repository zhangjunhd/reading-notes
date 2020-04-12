![cover](https://img1.doubanio.com/view/subject/s/public/s33321778.jpg)

    作者: Neal Ford / Mark Richards
    出版社: O'Reilly Media
    副标题: A Comprehensive Guide to Patterns, Characteristics, and Best Practices
    出版年: 2020-2-18
    页数: 396
    定价: USD 69.99
    装帧: Paperback
    ISBN: 9781492043454

- [豆瓣](https://book.douban.com/subject/34464806/)
- [oreilly](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/)

---

- [1.Introduction](#1introduction)
  - [Defining Software Architecture](#defining-software-architecture)
  - [Laws of Software Architecture](#laws-of-software-architecture)
- [I.Foundations](#ifoundations)
- [2.Architectural Thinking](#2architectural-thinking)
  - [Architecture Versus Design](#architecture-versus-design)
  - [Technical Breadth](#technical-breadth)
  - [Analyzing Trade-Offs](#analyzing-trade-offs)
- [3.Modularity](#3modularity)
  - [Definition](#definition)
  - [Measuring Modularity](#measuring-modularity)
    - [Cohesion](#cohesion)
    - [Coupling](#coupling)
    - [Abstractness, Instability, and Distance from the Main Sequence](#abstractness-instability-and-distance-from-the-main-sequence)
    - [Connascence](#connascence)
      - [Static connascence](#static-connascence)
      - [Dynamic connascence](#dynamic-connascence)
      - [Connascence properties](#connascence-properties)
    - [Unifying Coupling and Connascence Metrics](#unifying-coupling-and-connascence-metrics)
- [4.Architecture Characteristics Defined](#4architecture-characteristics-defined)
  - [Architectural Characteristics (Partially) Listed](#architectural-characteristics-partially-listed)
    - [Operational Architecture Characteristics](#operational-architecture-characteristics)
    - [Structural Architecture Characteristics](#structural-architecture-characteristics)
    - [Cross-Cutting Architecture Characteristics](#cross-cutting-architecture-characteristics)
- [5.Identifying Architectural Characteristics](#5identifying-architectural-characteristics)
  - [Extracting Architecture Characteristics from Domain Concerns](#extracting-architecture-characteristics-from-domain-concerns)
  - [Extracting Architecture Characteristics from Requirements](#extracting-architecture-characteristics-from-requirements)
  - [Case Study: Silicon Sandwiches](#case-study-silicon-sandwiches)
    - [Explicit Characteristics](#explicit-characteristics)
    - [Implicit Characteristics](#implicit-characteristics)
- [6.Measuring and Governing Architecture Characteristics](#6measuring-and-governing-architecture-characteristics)
  - [Measuring Architecture Characteristics](#measuring-architecture-characteristics)
    - [Operational Measures](#operational-measures)
    - [Structural Measures](#structural-measures)
    - [Process Measures](#process-measures)
  - [Governance and Fitness Functions](#governance-and-fitness-functions)
    - [Governing Architecture Characteristics](#governing-architecture-characteristics)
    - [Fitness Functions](#fitness-functions)
- [7.Scope of Architecture Characteristics](#7scope-of-architecture-characteristics)
  - [Coupling and Connascence](#coupling-and-connascence)
  - [Architectural Quanta and Granularity](#architectural-quanta-and-granularity)
- [8.Component-Based Thinking](#8component-based-thinking)
  - [Component Scope](#component-scope)
  - [Architect Role](#architect-role)
    - [Architecture Partitioning](#architecture-partitioning)
  - [Developer Role](#developer-role)
  - [Component Identification Flow](#component-identification-flow)
    - [Identifying Initial Components](#identifying-initial-components)
    - [Assign Requirements to Components](#assign-requirements-to-components)
    - [Analyze Roles and Responsibilities](#analyze-roles-and-responsibilities)
    - [Analyze Architecture Characteristics](#analyze-architecture-characteristics)
    - [Restructure Components](#restructure-components)
  - [Component Granularity](#component-granularity)
  - [Component Design](#component-design)
    - [Discovering Components](#discovering-components)
    - [Actor/Actions approach](#actoractions-approach)
    - [Event storming](#event-storming)
    - [Workflow approach](#workflow-approach)
- [II.Architecture Styles](#iiarchitecture-styles)
- [9.Foundations](#9foundations)
  - [Fundamental Patterns](#fundamental-patterns)
    - [Big Ball of Mud](#big-ball-of-mud)
    - [Unitary Architecture](#unitary-architecture)
    - [Client/Server](#clientserver)
  - [Monolithic Versus Distributed Architectures](#monolithic-versus-distributed-architectures)
    - [Fallacy #1: The Network Is Reliable](#fallacy-1-the-network-is-reliable)
    - [Fallacy #2: Latency Is Zero](#fallacy-2-latency-is-zero)
    - [Fallacy #3: Bandwidth Is Infinite](#fallacy-3-bandwidth-is-infinite)
    - [Fallacy #4: The Network Is Secure](#fallacy-4-the-network-is-secure)
    - [Fallacy #5: The Topology Never Changes](#fallacy-5-the-topology-never-changes)
    - [Fallacy #6: There Is Only One Administrator](#fallacy-6-there-is-only-one-administrator)
    - [Fallacy #7: Transport Cost Is Zero](#fallacy-7-transport-cost-is-zero)
    - [Fallacy #8: The Network Is Homogeneous](#fallacy-8-the-network-is-homogeneous)
    - [Other Distributed Considerations](#other-distributed-considerations)
      - [Distributed logging](#distributed-logging)
      - [Distributed transactions](#distributed-transactions)
      - [Contract maintenance and versioning](#contract-maintenance-and-versioning)
- [10.Layered Architecture Style](#10layered-architecture-style)
  - [Topology](#topology)
  - [Layers of Isolation](#layers-of-isolation)
  - [Adding Layers](#adding-layers)
  - [Other Considerations](#other-considerations)
  - [Why Use This Architecture Style](#why-use-this-architecture-style)
  - [Architecture Characteristics Ratings](#architecture-characteristics-ratings)
- [11.Pipeline Architecture Style](#11pipeline-architecture-style)
  - [Topology](#topology-1)
    - [Pipes](#pipes)
    - [Filters](#filters)
  - [Architecture Characteristics Ratings](#architecture-characteristics-ratings-1)
- [12.Microkernel Architecture Style](#12microkernel-architecture-style)
  - [Topology](#topology-2)
    - [Core System](#core-system)
    - [Plug-In Components](#plug-in-components)
  - [Registry](#registry)
  - [Contracts](#contracts)
  - [Architecture Characteristics Ratings](#architecture-characteristics-ratings-2)
- [13.Service-Based Architecture Style](#13service-based-architecture-style)
  - [Topology](#topology-3)
  - [Topology Variants](#topology-variants)
  - [Service Design and Granularity](#service-design-and-granularity)
  - [Database Partitioning](#database-partitioning)
  - [Architecture Characteristics Ratings](#architecture-characteristics-ratings-3)
  - [When to Use This Architecture Style](#when-to-use-this-architecture-style)
- [14.Event-Driven Architecture Style](#14event-driven-architecture-style)
  - [Topology](#topology-4)
  - [Broker Topology](#broker-topology)
  - [Mediator Topology](#mediator-topology)
  - [Asynchronous Capabilities](#asynchronous-capabilities)
  - [Error Handling](#error-handling)
  - [Preventing Data Loss](#preventing-data-loss)
  - [Broadcast Capabilities](#broadcast-capabilities)
  - [Request-Reply](#request-reply)
  - [Choosing Between Request-Based and Event-Based](#choosing-between-request-based-and-event-based)
  - [Architecture Characteristics Ratings](#architecture-characteristics-ratings-4)
- [15.Space-Based Architecture Style](#15space-based-architecture-style)
  - [General Topology](#general-topology)
    - [Processing Unit](#processing-unit)
    - [Virtualized Middleware](#virtualized-middleware)
      - [Messaging grid](#messaging-grid)
      - [Data grid](#data-grid)
      - [Processing grid](#processing-grid)
      - [Deployment manager](#deployment-manager)
      - [Data Pumps](#data-pumps)
      - [Data Writers](#data-writers)
      - [Data Readers](#data-readers)
  - [Data Collisions](#data-collisions)
  - [Cloud Versus On-Premises Implementations](#cloud-versus-on-premises-implementations)
  - [Replicated Versus Distributed Caching](#replicated-versus-distributed-caching)
  - [Near-Cache Considerations](#near-cache-considerations)
  - [Architecture Characteristics Ratings](#architecture-characteristics-ratings-5)
- [16.Orchestration-Driven Service-Oriented Architecture](#16orchestration-driven-service-oriented-architecture)
  - [Topology](#topology-5)
  - [Taxonomy](#taxonomy)
    - [Business Services](#business-services)
    - [Enterprise Services](#enterprise-services)
    - [Application Services](#application-services)
    - [Infrastructure Services](#infrastructure-services)
    - [Orchestration Engine](#orchestration-engine)
    - [Message Flow](#message-flow)
  - [Reuse…and Coupling](#reuseand-coupling)
  - [Architecture Characteristics Ratings](#architecture-characteristics-ratings-6)
- [17.Microservices Architecture](#17microservices-architecture)
  - [Topology](#topology-6)
  - [Distributed](#distributed)
  - [Bounded Context](#bounded-context)
    - [Granularity](#granularity)
    - [Data Isolation](#data-isolation)
  - [API Layer](#api-layer)
  - [Operational Reuse](#operational-reuse)
  - [Frontends](#frontends)
  - [Communication](#communication)
    - [Choreography and Orchestration](#choreography-and-orchestration)
    - [Transactions and Sagas](#transactions-and-sagas)
  - [Architecture Characteristics Ratings](#architecture-characteristics-ratings-7)
- [III.Techniques and Soft Skills](#iiitechniques-and-soft-skills)
- [19.Architecture Decisions](#19architecture-decisions)

# 1.Introduction
## Defining Software Architecture
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0102.png)

Figure 1-2. Architecture consists of the structure combined with architecture characteristics (“-ilities”), architecture decisions, and design principles

The `structure` of the system, as illustrated in Figure 1-3, refers to the type of architecture style (or styles) the system is implemented in (such as microservices, layered, or microkernel).

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0103.png)

Figure 1-3. Structure refers to the type of architecture styles used in the system

The `architecture characteristics` define the success criteria of a system, which is generally orthogonal to the functionality of the system. 

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0104.png)

Figure 1-4. Architecture characteristics refers to the “-ilities” that the system must support

`Architecture decisions` define the rules for how a system should be constructed.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0105.png)

Figure 1-5. Architecture decisions are rules for constructing systems

If a particular architecture decision cannot be implemented in one part of the system due to some condition or other constraint, that decision (or rule) can be broken through something called a `variance`.

A `design principle` differs from an architecture decision in that a design principle is a guideline rather than a hard-and-fast `rule`.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0106.png)

Figure 1-6. Design principles are guidelines for constructing systems

## Laws of Software Architecture
First Law of Software Architecture:

>Everything in software architecture is a trade-off.

Second Law of Software Architecture:

>Why is more important than how.

# I.Foundations
# 2.Architectural Thinking
## Architecture Versus Design
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0202.png)

Figure 2-2. Traditional view of architecture versus design

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0203.png)

Figure 2-3. Making architecture work through collaboration

## Technical Breadth
A developer’s early career focuses on expanding the top of the pyramid, to build experience and expertise.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0204.png)

Figure 2-4. The pyramid representing all knowledge

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0205.png)

Figure 2-5. Developers must maintain expertise to retain it

Unlike a developer, who must have a significant amount of `technical depth` to perform their job, a software architect must have a significant amount of `technical breadth` to think like an architect and see things with an architecture point of view.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0206.png)

Figure 2-6. What someone knows is technical depth, and how much someone knows is technical breadth

As an architect, breadth is more important than depth. Because architects must make decisions that match capabilities to technical constraints, a broad understanding of a wide variety of solutions is valuable. Thus, for an architect, **the wise course of action is to sacrifice some hard-won expertise and use that time to broaden their portfolio**, as shown in Figure 2-7. 

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0207.png)

Figure 2-7. Enhanced breadth and shrinking depth for the architect role

## Analyzing Trade-Offs
To quote Mark (one of your authors):

>Architecture is the stuff you can’t Google.

**Everything in architecture is a trade-off**, which is why the famous answer to every architecture question in the universe is “it depends.” 

To quote Neal (another one of your authors):

>There are no right or wrong answers in architecture—only trade-offs.

To quote Rich Hickey, the creator of the Clojure programming language:

>Programmers know the benefits of everything and the trade-offs of nothing. Architects need to understand both.

# 3.Modularity
## Definition
We use `modularity` to describe a logical grouping of related code, which could be a group of classes in an object-oriented language or functions in a structured or functional language. 

## Measuring Modularity
### Cohesion
`Cohesion` refers to what extent the parts of a module should be contained within the same module. In other words, it is a measure of how related the parts are to one another. Ideally, a cohesive module is one where all the parts should be packaged together, because breaking them into smaller pieces would require coupling the parts together via calls between modules to achieve useful results.

>Attempting to divide a cohesive module would only result in increased coupling and decreased readability. -Larry Constantine

Computer scientists have defined a range of cohesion measures, listed here from best to worst:

- Functional cohesion
  - Every part of the module is related to the other, and the module contains everything essential to function.
- Sequential cohesion
  - Two modules interact, where one outputs data that becomes the input for the other.
- Communicational cohesion
  - Two modules form a communication chain, where each operates on information and/or contributes to some output. For example, add a record to the database and generate an email based on that information.
- Procedural cohesion
  - Two modules must execute code in a particular order.
- Temporal cohesion
  - Modules are related based on timing dependencies. For example, many systems have a list of seemingly unrelated things that must be initialized at system startup; these different tasks are temporally cohesive.
- Logical cohesion
  - The data within modules is related logically but not functionally. For example, consider a module that converts information from text, serialized objects, or streams. Operations are related, but the functions are quite different. A common example of this type of cohesion exists in virtually every Java project in the form of the StringUtils package: a group of static methods that operate on String but are otherwise unrelated.
- Coincidental cohesion
  - Elements in a module are not related other than being in the same source file; this represents the most negative form of cohesion.

### Coupling
`Afferent coupling` measures the number of incoming connections to a code artifact (component, class, function, and so on). `Efferent coupling` measures the outgoing connections to other code artifacts. 

### Abstractness, Instability, and Distance from the Main Sequence
`Abstractness` is the ratio of abstract artifacts (abstract classes, interfaces, and so on) to concrete artifacts (implementation). It represents a measure of abstractness versus implementation. 

`Instability`, is defined as the ratio of efferent coupling to the sum of both efferent and afferent coupling. The instability metric determines the `volatility` of a code base.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0302.png)

Figure 3-2. The main sequence defines the ideal relationship between abstractness and instability

The `distance` metric imagines an ideal relationship between abstractness and instability; classes that fall near this idealized line exhibit a healthy mixture of these two competing concerns. 

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0303.png)

Figure 3-3. Normalized distance from the main sequence for a particular class

The closer to the line, the better balanced the class. Classes that fall too far into the upper-righthand corner enter into what architects call the `zone of uselessness`: code that is too abstract becomes difficult to use. Conversely, code that falls into the lower-lefthand corner enter the `zone of pain`: code with too much implementation and not enough abstraction becomes brittle and hard to maintain, illustrated in Figure 3-4.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0304.png)

Figure 3-4. Zones of Uselessness and Pain

### Connascence
>Two components are connascent if a change in one would require the other to be modified in order to maintain the overall correctness of the system.-Meilir Page-Jones

#### Static connascence
Architects view the following types of static connascence as the degree to which something is coupled, either afferently or efferently:

- Connascence of Name (CoN):Multiple components must agree on the name of an entity.
  - Names of methods represents the most common way that code bases are coupled and the most desirable, especially in light of modern refactoring tools that make system-wide name changes trivial.
- Connascence of Type (CoT):Multiple components must agree on the type of an entity.
  - This type of connascence refers to the common facility in many statically typed languages to limit variables and parameters to specific types. However, this capability isn’t purely a language feature—some dynamically typed languages offer selective typing, notably Clojure and Clojure Spec.
- Connascence of Meaning (CoM) or Connascence of Convention (CoC):Multiple components must agree on the meaning of particular values.
  - The most common obvious case for this type of connascence in code bases is hard-coded numbers rather than constants. For example, it is common in some languages to consider defining somewhere int TRUE = 1; int FALSE = 0. Imagine the problems if someone flips those values.
- Connascence of Position (CoP):Multiple entities must agree on the order of values.
  - This is an issue with parameter values for method and function calls even in languages that feature static typing. For example, if a developer creates a method void updateSeat(String name, String seatLocation) and calls it with the values updateSeat("14D", "Ford, N"), the semantics aren’t correct even if the types are.
- Connascence of Algorithm (CoA):Multiple components must agree on a particular algorithm.
  - A common case for this type of connascence occurs when a developer defines a security hashing algorithm that must run on both the server and client and produce identical results to authenticate the user. Obviously, this represents a high form of coupling—if either algorithm changes any details, the handshake will no longer work.

#### Dynamic connascence
The following is a description of the different types of dynamic connascence:

- Connascence of Execution (CoE):The order of execution of multiple components is important.

Consider this code:

```java
email = new Email();
email.setRecipient("foo@example.com");
email.setSender("me@me.com");
email.send();
email.setSubject("whoops");
```

It won’t work correctly because certain properties must be set in order.

- Connascence of Timing (CoT):The timing of the execution of multiple components is important.
  - The common case for this type of connascence is a race condition caused by two threads executing at the same time, affecting the outcome of the joint operation.
- Connascence of Values (CoV):Occurs when several values relate on one another and must change together.
  - Consider the case where a developer has defined a rectangle as four points, representing the corners. To maintain the integrity of the data structure, the developer cannot randomly change one of points without considering the impact on the other points.
- Connascence of Identity (CoI):Occurs when several values relate on one another and must change together.
  - The common example of this type of connascence involves two independent components that must share and update a common data structure, such as a distributed queue.

#### Connascence properties
- Strength
  - Architects determine the strength of connascence by the ease with which a developer can refactor that type of coupling; different types of connascence are demonstrably more desirable, as shown in Figure 3-5. 

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0305.png)

Figure 3-5. The strength on connascence provides a good refactoring guide

- Locality
  - The locality of connascence measures how proximal the modules are to each other in the code base. Proximal code (in the same module) typically has more and higher forms of connascence than more separated code (in separate modules or code bases). In other words, forms of connascence that indicate poor coupling when far apart are fine when closer together.
- Degree
  - The degree of connascence relates to the size of its impact—does it impact a few classes or many? Lesser degrees of connascence damage code bases less.

### Unifying Coupling and Connascence Metrics
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0306.png)

Figure 3-6. Unifying coupling and connascence

# 4.Architecture Characteristics Defined
The architect must consider many other factors in designing a software solution, as illustrated in Figure 4-1.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0107.png)

Figure 4-1. A software solution consists of both domain requirements and architectural characteristics

Architects may collaborate on defining the domain or business requirements, but one key responsibility entails defining, discovering, and otherwise analyzing all the things the software must do that isn’t directly related to the domain functionality: `architectural characteristics`.

An architecture characteristic meets three criteria:

- Specifies a nondomain design consideration
- Influences some structural aspect of the design
- Is critical or important to application success

These interlocking parts of our definition are illustrated in Figure 4-2.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0402.png)

Figure 4-2. The differentiating features of architecture characteristics

## Architectural Characteristics (Partially) Listed
### Operational Architecture Characteristics
Table 4-1. Common operational architecture characteristics

Term | Definition
---|---
Availability | How long the system will need to be available (if 24/7, steps need to be in place to allow the system to be up and running quickly in case of any failure).
Continuity | Disaster recovery capability.
Performance | Includes stress testing, peak analysis, analysis of the frequency of functions used, capacity required, and response times. Performance acceptance sometimes requires an exercise of its own, taking months to complete.
Recoverability | Business continuity requirements (e.g., in case of a disaster, how quickly is the system required to be on-line again?). This will affect the backup strategy and requirements for duplicated hardware.
Reliability/safety | Assess if the system needs to be fail-safe, or if it is mission critical in a way that affects lives. If it fails, will it cost the company large sums of money?
Robustness | Ability to handle error and boundary conditions while running if the internet connection goes down or if there’s a power outage or hardware failure.
Scalability | Ability for the system to perform and operate as the number of users or requests increases.

Operational architecture characteristics heavily overlap with operations and DevOps concerns, forming the intersection of those concerns in many software projects.

### Structural Architecture Characteristics
Table 4-2. Structural architecture characteristics

Term | Definition
---|---
Configurability | Ability for the end users to easily change aspects of the software’s configuration (through usable interfaces).
Extensibility | How important it is to plug new pieces of functionality in.
Installability | Ease of system installation on all necessary platforms.
Leverageability/reuse | Ability to leverage common components across multiple products.
Localization | Support for multiple languages on entry/query screens in data fields; on reports, multibyte character requirements and units of measure or currencies.
Maintainability | How easy it is to apply changes and enhance the system?
Portability | Does the system need to run on more than one platform? (For example, does the frontend need to run against Oracle as well as SAP DB?
Supportability | What level of technical support is needed by the application? What level of logging and other facilities are required to debug errors in the system?
Upgradeability | Ability to easily/quickly upgrade from a previous version of this application/solution to a newer version on servers and clients.

### Cross-Cutting Architecture Characteristics
Table 4-3. Cross-cutting architecture characteristics

Term | Definition
---|---
Accessibility | Access to all your users, including those with disabilities like colorblindness or hearing loss.
Archivability | Will the data need to be archived or deleted after a period of time? (For example, customer accounts are to be deleted after three months or marked as obsolete and archived to a secondary database for future access.)
Authentication | Security requirements to ensure users are who they say they are.
Authorization | Security requirements to ensure users can access only certain functions within the application (by use case, subsystem, webpage, business rule, field level, etc.).
Legal | What legislative constraints is the system operating in (data protection, Sarbanes Oxley, GDPR, etc.)? What reservation rights does the company require? Any regulations regarding the way the application is to be built or deployed?
Privacy | Ability to hide transactions from internal company employees (encrypted transactions so even DBAs and network architects cannot see them).
Security | Does the data need to be encrypted in the database? Encrypted for network communication between internal systems? What type of authentication needs to be in place for remote user access?
Supportability | What level of technical support is needed by the application? What level of logging and other facilities are required to debug errors in the system?
Usability/achievability | Level of training required for users to achieve their goals with the application/solution. Usability requirements need to be treated as seriously as any other architectural issue.

# 5.Identifying Architectural Characteristics
## Extracting Architecture Characteristics from Domain Concerns
A common anti-pattern in architecture entails trying to design a `generic architecture`, one that supports all the architecture characteristics.

Table 5-1. Translation of domain concerns to architecture characteristics

Domain concern | Architecture characteristics
---|---
Mergers and acquisitions| Interoperability, scalability, adaptability, extensibility
Time to market | Agility, testability, deployability
User satisfaction | Performance, availability, fault tolerance, testability, deployability, agility, security
Competitive advantage | Agility, testability, deployability, scalability, availability, fault tolerance
Time and budget | Simplicity, feasibility

## Extracting Architecture Characteristics from Requirements
Some architecture characteristics come from explicit statements in requirements documents. Others come from inherent domain knowledge by architects, one of the many reasons that domain knowledge is always beneficial for architects.

A few years ago, Ted Neward, a well-known architect, devised architecture `kata`s, a clever method to allow nascent architects a way to practice deriving architecture characteristics from domain-targeted descriptions. 

Each kata has predefined sections:

- Description
  - The overall domain problem the system is trying to solve
- Users
  - The expected number and/or types of users of the system
- Requirements
  - Domain/domain-level requirements, as an architect might expect from domain users/domain experts
- Additional context
  - Many of the considerations an architect must make aren’t explicitly expressed in requirements but rather by implicit knowledge of the problem domain

## Case Study: Silicon Sandwiches
To show how architects derive architecture characteristics from requirements, we introduce the Silicon Sandwiches kata.

- Description
  - A national sandwich shop wants to enable online ordering (in addition to its current call-in service).
- Users
  - Thousands, perhaps one day millions
- Requirements
  - Users will place their order, then be given a time to pick up their sandwich and directions to the shop (which must integrate with several external mapping services that include traffic information)
  - If the shop offers a delivery service, dispatch the driver with the sandwich to the user
  - Mobile-device accessibility
  - Offer national daily promotions/specials
  - Offer local daily promotions/specials
  - Accept payment online, in person, or upon delivery
- Additional context
  - Sandwich shops are franchised, each with a different owner
  - Parent company has near-future plans to expand overseas
  - Corporate goal is to hire inexpensive labor to maximize profit

First, separate the candidate architecture characteristics into explicit and implicit characteristics.

### Explicit Characteristics
One of the first details that should catch an architect’s eye is the number of users: currently thousands, perhaps one day millions (this is a very ambitious sandwich shop!). Thus, `scalability`—the ability to handle a large number of concurrent users without serious performance degradation—is one of the top architecture characteristics.

However, we also probably need `elasticity`—the ability to handle bursts of requests. 

Scalability looks like the graph shown in Figure 5-1.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0501.png)

Figure 5-1. Scalability measures the performance of concurrent users

Elasticity, on the other hand, measures bursts of traffic, as shown in Figure 5-2.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0502.png)

Figure 5-2. Elastic systems must withstand bursts of users

The requirement for elasticity did not appear in the Silicon Sandwiches requirements, yet the architect should identify this as an important consideration. **Requirements sometimes state architecture characteristics outright, but some lurk inside the problem domain**.

An architect should consider each of these business requirements in turn to see if architecture characteristics exist:

1. Users will place their order, then be given a time to pick up their sandwich and directions to the shop (which must provide the option to integrate with external mapping services that include traffic information).
2. If the shop offers a delivery service, dispatch the driver with the sandwich to the user.(No special architecture characteristics seem necessary to support this requirement.)
3. Mobile-device accessibility.(This requirement will primarily affect the design of the application, pointing toward building either a portable web application or several native web applications. Given the budget constraints and simplicity of the application, an architect would likely deem it overkill to build multiple applications, so the design points toward a mobile-optimized web application. Thus, the architect may want to define some specific performance architecture characteristics for page load time and other mobile-sensitive characteristics. Notice that the architect shouldn’t act alone in situations like this, but should instead collaborate with user experience designers, domain stakeholders, and other interested parties to vet decisions like this.)
4. Offer national daily promotions/specials.
5. Offer local daily promotions/specials.(Both of these requirements specify customizability across both promotions and specials. Notice that requirement 1 also implies customized traffic information based on address. Based on all three of these requirements, the architect may consider customizability as an architecture characteristic. For example, an architecture style such as microkernel architecture supports customized behavior extremely well by defining a plug-in architecture. In this case, the default behavior appears in the core, and developers write the optional customized parts, based on location, via plug-ins. However, a traditional design can also accommodate this requirement via design patterns (such as Template Method). This conundrum is common in architecture and requires architects to constantly weight trade-offs between competing options. )
6. Accept payment online, in person, or upon delivery.(Online payments imply security, but nothing in this requirement suggests a particularly heightened level of security beyond what’s implicit.)
7. Sandwich shops are franchised, each with a different owner.(This requirement may impose cost restrictions on the architecture—the architect should check the feasibility (applying constraints like cost, time, and staff skill set) to see if a simple or sacrificial architecture is warranted.)
8. Parent company has near-future plans to expand overseas.(This requirement implies internationalization, or i18n.)
9. Corporate goal is to hire inexpensive labor to maximize profit.(This requirement suggests that usability will be important, but again is more concerned with design than architecture characteristics.)

### Implicit Characteristics
One implicit architecture characteristic the system might want to support is `availability`: making sure users can access the sandwich site. Closely related to availability is `reliability`: making sure the site stays up during interactions—no one wants to purchase from a site that continues dropping connections, forcing them to log in again.

`Security` appears as an implicit characteristic in every system: no one wants to create insecure software. However, it may be prioritized depending on criticality, which illustrates the interlocking nature of our definition. 

The last major architecture characteristic that Silicon Sandwiches needs to support encompasses several details from the requirements: `customizability`.

# 6.Measuring and Governing Architecture Characteristics
## Measuring Architecture Characteristics
### Operational Measures
Many architecture characteristics have obvious direct measurements, such as performance or scalability.

### Structural Measures
What about internal structural characteristics, such as well-defined modularity? Unfortunately, comprehensive metrics for internal code quality don’t yet exist.

### Process Measures
Some architecture characteristics intersect with software development processes. For example, `agility` often appears as a desirable feature. However, it is a composite architecture characteristic that architects may decompose into features such as `testability`, and `deployability`.

## Governance and Fitness Functions
### Governing Architecture Characteristics
Governance, derived from the Greek word kubernan (to steer) is an important responsibility of the architect role. As the name implies, the scope of architecture governance covers any aspect of the software development process that architects (including roles like enterprise architects) want to exert an influence upon.

Fortunately, increasingly sophisticated solutions exist to relieve this problem from architects, a good example of the incremental growth in capabilities within the software development ecosystem. The drive toward automation on software projects spawned by `Extreme Programming` created continuous integration, which led to further automation into operations, which we now call `DevOps`, continuing through to architectural governance. 

### Fitness Functions
`Architecture fitness function`:Any mechanism that provides an objective integrity assessment of some architecture characteristic or combination of architecture characteristics.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0602.png)

Figure 6-2. The mechanisms of fitness functions

# 7.Scope of Architecture Characteristics
## Coupling and Connascence
Many of the code-level coupling metrics, such as afferent and efferent coupling (described in “Structural Measures”), reveal details at a too fine-grained level for architectural analysis. In 1996, Meilir Page-Jones published a book titled What Every Programmer Should Know About Object Oriented Design (Dorset House) that included several new measures of coupling he named connascence, which is defined as follows:

- Connascence
  - Two components are connascent if a change in one would require the other to be modified in order to maintain the overall correctness of the system

He defined two types of connascence: `static`, discoverable via static code analysis, and `dynamic`, concerning runtime behavior.

For dynamic connascence, we define two types: `synchronous` and `asynchronous`. Synchronous calls between two distributed services have the caller wait for the response from the callee. On the other hand, asynchronous calls allow fire-and-forget semantics in event-driven architectures, allowing two different services to differ in operational architecture

## Architectural Quanta and Granularity
- Architecture quantum
  - An independently deployable artifact with high functional cohesion and synchronous connascence

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0701.png)

Figure 7-1. Adding quantum connascence to the unified diagram

# 8.Component-Based Thinking
## Component Scope
Components offer a language-specific mechanism to group artifacts together, often nesting them to create stratification.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0801.png)

Figure 8-1. Different varieties of components

Components also appear as `subsystems` or `layers` in architecture, as the deployable unit of work for many event processors. Another type of component, a `service`, tends to run in its own address space and communicates via low-level networking protocols like TCP/IP or higher-level formats like REST or message queues, forming stand-alone, deployable units in architectures like microservices.

## Architect Role
Generally the component is the lowest level of the software system an architect interacts directly with, with the exception of many of the code quality metrics discussed in Chapter 6 that affect code bases holistically.

### Architecture Partitioning
Here we discuss an important aspect of styles, the `top-level partitioning` in an architecture.

Consider the two types of architecture styles shown in Figure 8-3.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0803.png)

Figure 8-3. Two types of top-level architecture partitioning: layered and modular

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0804.png)

Figure 8-4. Two types of top-level partitioning in architecture

In Figure 8-4, the architect has partitioned the functionality of the system into `technical` capabilities: presentation, business rules, services, persistence, and so on. This way of organizing a code base certainly makes sense. All the persistence code resides in one layer in the architecture, making it easy for developers to find persistence-related code. Even though the basic concept of layered architecture predates it by decades, the Model-View-Controller design pattern matches with this architectural pattern, making it easy for developers to understand.

When using a layered architecture, it makes some sense to have all the backend developers sit together in one department, the DBAs in another, the presentation team in another, and so on. Because of `Conway’s law`, this makes some sense in those organizations.

The other architectural variation in Figure 8-4 represents domain partitioning, inspired by the Eric Evan book `Domain-Driven Design`, which is a modeling technique for decomposing complex software systems. In DDD, the architect identifies domains or workflows independent and decoupled from each other. The `microservices architecture` style (discussed in Chapter 17) is based on this philosophy.

One of the fundamental distinctions between different architecture patterns is **what type of top-level partitioning each supports, which we cover for each individual pattern**.

Architects using technical partitioning organize the components of the system by technical capabilities: presentation, business rules, persistence, and so on. Thus, one of the organizing principles of this architecture is `separation of technical concerns`. This in turn creates useful levels of decoupling: if the service layer is only connected to the persistence layer below and business rules layer above, then changes in persistence will only potentially affect those layers. This style of partitioning provides a decoupling technique, reducing rippling side effects on dependent components.

However, most realistic software systems require workflows that cut across technical capabilities. Consider the common business workflow of CatalogCheckout. The code to handle CatalogCheckout in the technically layered architecture appears in all the layers, as shown in Figure 8-5.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0805.png)

Figure 8-5. Where domains/workflows appear in technical- and domain-partitioned architectures

Neither of these styles is more correct than the other—refer to the First Law of Software Architecture.

## Developer Role
Developers typically take components, jointly designed with the architect role, and further subdivide them into classes, functions, or subcomponents.

## Component Identification Flow
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0808.png)

Figure 8-8. Component identification cycle

### Identifying Initial Components
Before any code exists for a software project, the architect must somehow determine what top-level components to begin with, based on what type of top-level partitioning they choose. Outside that, an architect has the freedom to make up whatever components they want, then map domain functionality to them to see where behavior should reside.

### Assign Requirements to Components
Once an architect has identified initial components, the next step aligns requirements (or user stories) to those components to see how well they fit. This may entail creating new components, consolidating existing ones, or breaking components apart because they have too much responsibility.

### Analyze Roles and Responsibilities
When assigning stories to components, the architect also looks at the roles and responsibilities elucidated during the requirements to make sure that the granularity matches. Thinking about both the roles and behaviors the application must support allows the architect to align the component and domain granularity.

### Analyze Architecture Characteristics
When assigning requirements to components, the architect should also look at the architecture characteristics discovered earlier in order to think about how they might impact component division and granularity.

### Restructure Components
Feedback is critical in software design. Thus, architects must continually iterate on their component design with developers.

## Component Granularity
Finding the proper granularity for components is one of an architect’s most difficult tasks. Too fine-grained a component design leads to too much communication between components to achieve results. Too coarse-grained components encourage high internal coupling, which leads to difficulties in deployability and testability, as well as modularity-related negative side effects.

## Component Design
### Discovering Components
While there is no one true way to ascertain components, a common anti-pattern lurks: the `entity trap`. Say that an architect is working on designing components for our kata Going, Going, Gone and ends up with a design resembling Figure 8-9.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0809.png)

Figure 8-9. Building an architecture as an object-relational mapping

In Figure 8-9, the architect has basically taken each entity identified in the requirements and made a Manager component based on that entity. This isn’t an architecture; it’s a component-relational mapping of a framework to a database. In other words, if a system only needs simple database CRUD operations (create, read, update, delete), then the architect can download a framework to create user interfaces directly from the database.

### Actor/Actions approach
The actor/actions approach is a popular way that architects use to map requirements to components. In this approach, originally defined by the Rational Unified Process, architects identify actors who perform activities with the application and the actions those actors may perform.

### Event storming
Event storming as a component discovery technique comes from domain-driven design (DDD) and shares popularity with microservices, also heavily influenced by DDD. In event storming, the architect assumes the project will use messages and/or events to communicate between the various components. To that end, the team tries to determine which events occur in the system based on requirements and identified roles, and build components around those event and message handlers.

### Workflow approach
The workflow approach models the components around workflows, much like event storming, but without the explicit constraints of building a message-based system. A workflow approach identifies the key roles, determines the kinds of workflows these roles engage in, and builds components around the identified activities.

# II.Architecture Styles
We define an `architecture style` as the overarching structure of how the user interface and backend source code are organized (such as within layers of a monolithic deployment or separately deployed services) and how that source code interacts with a datastore. `Architecture patterns`, on the other hand, are lower-level design structures that help form specific solutions within an architecture style (such as how to achieve high scalability or high performance within a set of operations or between sets of services).

# 9.Foundations
## Fundamental Patterns
### Big Ball of Mud
In modern terms, a `big ball of mud` might describe a simple scripting application with event handlers wired directly to database calls, with no real internal structure. Many trivial applications start like this then become unwieldy as they continue to grow.

In general, architects want to avoid this type of architecture at all costs.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0901.png)

Figure 9-1. A Big Ball of Mud architecture visualized from a real code base

### Unitary Architecture
When personal computers first appeared, much of the commercial development focused on single machines. As networking PCs became common, distributed systems (such as client/server) appeared.

### Client/Server
A fundamental style in architecture separates technical functionality between frontend and backend, called a `two-tier`, or `client/server`, architecture.

- Desktop + database server
- Browser + web server
- Three-tier
  - An architecture that became quite popular during the late 1990s was a three-tier architecture, which provided even more layers of separation. As tools like application servers became popular in Java and .NET, companies started building even more layers in their topology: a database tier using an industrial-strength database server, an application tier managed by an application server, frontend coded in generated HTML, and increasingly, JavaScript, as its capabilities expanded.
  - The three-tier architecture corresponded with network-level protocols such as Common Object Request Broker Architecture (CORBA) and Distributed Component Object Model (DCOM) that facilitated building distributed architectures.

## Monolithic Versus Distributed Architectures
In this book we will describe in detail the following architecture styles:

- Monolithic
  - Layered architecture (Chapter 10)
  - Pipeline architecture (Chapter 11)
  - Microkernel architecture (Chapter 12)
- Distributed
  - Service-based architecture (Chapter 13)
  - Event-driven architecture (Chapter 14)
  - Space-based architecture (Chapter 15)
  - Service-oriented architecture (Chapter 16)
  - Microservices architecture (Chapter 17)

The first group of issues facing all distributed architectures are described in [the fallacies of distributed computing](https://oreil.ly/fVAEY), first coined by L. Peter Deutsch and other colleagues from Sun Microsystems in 1994. A `fallacy` is something that is believed or assumed to be true but is not.

### Fallacy #1: The Network Is Reliable
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0902.png)

Figure 9-2. The network is not reliable

### Fallacy #2: Latency Is Zero
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0903.png)

Figure 9-3. Latency is not zero

### Fallacy #3: Bandwidth Is Infinite
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0904.png)

Figure 9-4. Bandwidth is not infinite

`Stamp coupling` can be resolved in the following ways:

- Create private RESTful API endpoints
- Use field selectors in the contract
- Use GraphQL to decouple contracts
- Use value-driven contracts with consumer-driven contracts (CDCs)
- Use internal messaging endpoints

### Fallacy #4: The Network Is Secure
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0905.png)

Figure 9-5. The network is not secure

### Fallacy #5: The Topology Never Changes
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0906.png)

Figure 9-6. The network topology always changes

### Fallacy #6: There Is Only One Administrator
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0907.png)

Figure 9-7. There are many network administrators, not just one

### Fallacy #7: Transport Cost Is Zero
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0908.png)

Figure 9-8. Remote access costs money

Distributed architectures cost significantly more than monolithic architectures, primarily due to increased needs for additional hardware, servers, gateways, firewalls, new subnets, proxies, and so on.

### Fallacy #8: The Network Is Homogeneous
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_0909.png)

Figure 9-9. The network is not homogeneous

### Other Distributed Considerations
#### Distributed logging
`Logging consolidation` tools such as Splunk help to consolidate information from various sources and systems together into one consolidated log and console, but these tools only scratch the surface of the complexities involved with distributed logging.

#### Distributed transactions
Standard commits and rollbacks executed from persistence frameworks leverage `ACID` (atomicity, consistency, isolation, durability) transactions to guarantee that the data is updated in a correct way to ensure high data consistency and integrity.

`BASE` transactions are used. BASE stands for (B)asic availability, (S)oft state, and (E)ventual consistency. BASE transactions are not a piece of software, but rather a technique. 

#### Contract maintenance and versioning
A `contract` is behavior and data that is agreed upon by both the client and the service. Contract maintenance is particularly difficult in distributed architectures, primarily due to decoupled services and systems owned by different teams and departments. 

# 10.Layered Architecture Style
## Topology
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1001.png)

Figure 10-1. Standard logical layers within the layered architecture style

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1002.png)

Figure 10-2. Physical topology (deployment) variants

This `separation of concerns` concept within the layered architecture style makes it easy to build effective roles and responsibility models within the architecture. **Components within a specific layer are limited in scope, dealing only with the logic that pertains to that layer**. For example, components in the presentation layer only handle presentation logic, whereas components residing in the business layer only handle business logic. This allows developers to leverage their particular technical expertise to focus on the technical aspects of the domain (such as presentation logic or persistence logic). **The trade-off of this benefit, however, is a lack of overall agility (the ability to respond quickly to change)**.

The layered architecture is a `technically partitioned` architecture (as opposed to a `domain-partitioned` architecture). Groups of components, rather than being grouped by domain (such as customer), are grouped by their technical role in the architecture (such as presentation or business). As a result, any particular business domain is spread throughout all of the layers of the architecture.

## Layers of Isolation
A `closed` layer means that as a request moves top-down from layer to layer, the request cannot skip any layers, but rather must go through the layer immediately below it to get to the next layer (see Figure 10-3).

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1003.png)

Figure 10-3. Closed layers within the layered architecture

Notice that in Figure 10-3 it would be much faster and easier for the presentation layer to access the database directly for simple retrieval requests, bypassing any unnecessary layers (what used to be known in the early 2000s as the `fast-lane reader pattern`). For this to happen, the business and persistence layers would have to be `open`, allowing requests to bypass other layers.

The `layers of isolation` concept means that changes made in one layer of the architecture generally don’t impact or affect components in other layers, providing the contracts between those layers remain unchanged. Each layer is independent of the other layers, thereby having little or no knowledge of the inner workings of other layers in the architecture.

If the presentation layer can directly access the persistence layer, then changes made to the persistence layer would impact both the business layer and the presentation layer, producing a very tightly coupled application with layer interdependencies between components. This type of architecture then becomes very brittle, as well as difficult and expensive to change.

## Adding Layers
While closed layers facilitate layers of isolation and therefore help isolate change within the architecture, there are times when it makes sense for certain layers to be open. For example, suppose there are shared objects within the business layer that contain common functionality for business components (such as date and string utility classes, auditing classes, logging classes, and so on). Suppose there is an architecture decision stating that the presentation layer is restricted from using these shared business objects. This constraint is illustrated in Figure 10-4, with the dotted line going from a presentation component to a shared business object in the business layer. This scenario is difficult to govern and control because architecturally the presentation layer has access to the business layer, and hence has access to the shared objects within that layer.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1004.png)

Figure 10-4. Shared objects within the business layer

One way to architecturally mandate this restriction is to add to the architecture a new services layer containing all of the shared business objects. Adding this new layer now architecturally restricts the presentation layer from accessing the shared business objects because the business layer is closed (see Figure 10-5). However, the new services layer must be marked as open; otherwise the business layer would be forced to go through the services layer to access the persistence layer. Marking the services layer as open allows the business layer to either access that layer (as indicated by the solid arrow), or bypass the layer and go to the next one down (as indicated by the dotted arrow in Figure 10-5).

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1005.png)

Figure 10-5. Adding a new services layer to the architecture

## Other Considerations
One thing to watch out for with the layered architecture is the architecture `sinkhole` anti-pattern. This anti-pattern occurs when requests move from layer to layer as simple pass-through processing with no business logic performed within each layer.

The 80-20 rule is usually a good practice to follow. For example, it is acceptable if only 20 percent of the requests are sinkholes. However, if 80 percent of the requests are sinkholes, it a good indicator that the layered architecture is not the correct architecture style for the problem domain.

## Why Use This Architecture Style
The layered architecture style is a good choice for small, simple applications or websites.

As applications using the layered architecture style grow, characteristics like maintainability, agility, testability, and deployability are adversely affected. For this reason, large applications and systems using the layered architecture might be better suited for other, more modular architecture styles.

## Architecture Characteristics Ratings
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1006.png)

# 11.Pipeline Architecture Style
## Topology
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1101.png)

Figure 11-1. Basic topology for pipeline architecture

### Pipes
`Pipes` in this architecture form the communication channel between filters. Each pipe is typically unidirectional and point-to-point (rather than broadcast) for performance reasons, accepting input from one source and always directing output to another.  The payload carried on the pipes may be any data format, but architects favor smaller amounts of data to enable high performance.

### Filters
`Filters` are self-contained, independent from other filters, and generally `stateless`.

Four types of filters exist within this architecture style:

- Producer
  - The starting point of a process, outbound only, sometimes called the source.
- Transformer
  - Accepts input, optionally performs a transformation on some or all of the data, then forwards it to the outbound pipe. Functional advocates will recognize this feature as `map`.
- Tester
  - Accepts input, tests one or more criteria, then optionally produces output, based on the test. Functional programmers will recognize this as similar to `reduce`.
- Consumer
  - The termination point for the pipeline flow. Consumers sometimes persist the final result of the pipeline process to a database, or they may display the final results on a user interface screen.

## Architecture Characteristics Ratings
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1103.png)

Figure 11-3. Pipeline architecture characteristics ratings

# 12.Microkernel Architecture Style
## Topology
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1201.png)

Figure 12-1. Basic components of the microkernel architecture style

### Core System
The `core system` is formally defined as the minimal functionality required to run the system. 

Removing the cyclomatic complexity of the core system and placing it into separate plug-in components allows for better extensibility and maintainability, as well as increased testability. For example, suppose an electronic device recycling application must perform specific custom assessment rules for each electronic device received. The Java code for this sort of processing might look as follows:

```java
public void assessDevice(String deviceID) {
    if (deviceID.equals("iPhone6s")) {      
        assessiPhone6s();   
    } else if (deviceID.equals("iPad1"))
        assessiPad1();   
    } else if (deviceID.equals("Galaxy5"))              
        assessGalaxy5();   
    } else ...      
        ...   
    }
}
```

With the microkernel architecture style, assessing an electronic device only requires the core system to locate and invoke the corresponding device plug-ins as illustrated in this revised source code:

```java
public void assessDevice(String deviceID) {	
    String plugin = pluginRegistry.get(deviceID);	
    Class<?> theClass = Class.forName(plugin);	
    Constructor<?> constructor = theClass.getConstructor();DevicePlugin devicePlugin = (DevicePlugin)constructor.newInstance();
    DevicePlugin.assess();
}
```

Depending on the size and complexity, the core system can be implemented as a layered architecture or a modular monolith (as illustrated in Figure 12-2).

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1202.png)

Figure 12-2. Variations of the microkernel architecture core system

As a matter of fact, a separate user interface can also be implemented as a microkernel architecture style. Figure 12-3 illustrates these presentation layer variants in relation to the core system.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1203.png)

Figure 12-3. User interface variants

### Plug-In Components
Plug-in components are `standalone`, `independent`  components that contain specialized processing, additional features, and custom code meant to enhance or extend the core system. Additionally, they can be used to isolate highly volatile code, creating better maintainability and testability within the application. Ideally, plug-in components should be independent of each other and have no dependencies between them.

The communication between the plug-in components and the core system is generally point-to-point, meaning the “pipe” that connects the plug-in to the core system is usually a method invocation or function call to the `entry-point` class of the plug-in component. In addition, the plug-in component can be either `compile-based` or `runtime-based`.

Point-to-point plug-in components can be implemented as shared libraries (such as a JAR, DLL, or Gem), package names in Java, or namespaces in C#.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1204.png)

Figure 12-4. Shared library plug-in implementation

Alternatively, an easier approach shown in Figure 12-5 is to implement each plug-in component as a separate namespace or package name within the same code base or IDE project.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1205.png)

Figure 12-5. Package or namespace plug-in implementation

Plug-in components do not always have to be point-to-point communication with the core system. Other alternatives exist, including using REST or messaging as a means to invoke plug-in functionality, with each plug-in being a standalone service (or maybe even a microservice implemented using a container). Although this may sound like a good way to increase overall scalability, note that this topology (illustrated in Figure 12-6) is still only a single architecture quantum due to the monolithic core system.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1206.png)

Figure 12-6. Remote plug-in access using RES

It is not a common practice for plug-in components to connect directly to a centrally shared database. Rather, the core system takes on this responsibility, passing whatever data is needed into each plug-in. The primary reason for this practice is `decoupling`.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1207.png)

Figure 12-7. Plug-in components can own their own data store

## Registry
The core system needs to know about which plug-in modules are available and how to get to them. One common way of implementing this is through a plug-in registry. This registry contains information about each plug-in module, including things like its name, data contract, and remote access protocol details (depending on how the plug-in is connected to the core system).

Using the electronics recycling example, the following Java code implements a simple registry within the core system, showing a point-to-point entry, a messaging entry, and a RESTful entry example for assessing an iPhone 6S device:

```java
Map<String, String> registry = new HashMap<String, String>();
static {  
    //point-to-point access example  
    registry.put("iPhone6s", "Iphone6sPlugin");  
    
    //messaging example  
    registry.put("iPhone6s", "iphone6s.queue");  
    
    //restful example  
    registry.put("iPhone6s", "https://atlas:443/assess/iphone6s");
}
```

## Contracts
The contracts between the plug-in components and the core system are usually standard across a domain of plug-in components and include behavior, input data, and output data returned from the plug-in component.

Plug-in contracts can be implemented in XML, JSON, or even objects passed back and forth between the plug-in and the core system.

## Architecture Characteristics Ratings
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1208.png)

Figure 12-8. Microkernel architecture characteristics ratings

# 13.Service-Based Architecture Style
## Topology
The basic topology of service-based architecture follows a distributed macro layered structure consisting of a separately deployed user interface, separately deployed remote coarse-grained services, and a monolithic database. This basic topology is illustrated in Figure 13-1.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1301.png)

Figure 13-1. Basic topology of the service-based architecture style

Services within this architecture style are typically coarse-grained “portions of an application” (usually called `domain services`) that are independent and separately deployed.

While REST is typically used to access services from the user interface, messaging, remote procedure call (RPC), or even SOAP could be used as well.

## Topology Variants
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1302.png)

Figure 13-2. User interface variants

Similarly, opportunities may exist to break apart a single monolithic database into separate databases, even going as far as domain-scoped databases matching each domain service (similar to microservices).

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1303.png)

Figure 13-3. Database variants

Finally, it is also possible to add an `API layer` consisting of a reverse proxy or gateway between the user interface and services, as shown in Figure 13-4. This is a good practice when exposing domain service functionality to external systems or when consolidating shared cross-cutting concerns and moving them outside of the user interface (such as metrics, security, auditing requirements, and service discovery).

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1304.png)

Figure 13-4. Adding an API layer between the user interface and domain services

## Service Design and Granularity
Because domain services in a service-based architecture are generally coarse-grained, each domain service is typically designed using a layered architecture style consisting of an API facade layer, a business layer, and a persistence layer. Another popular design approach is to domain partition each domain service using sub-domains similar to the modular monolith architecture style. Each of these design approaches is illustrated in Figure 13-5.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1305.png)

Figure 13-5. Domain service design variants

In the `microservices` architecture style, this would likely involve the orchestration of many separately deployed remote single-purpose services to complete the request. This difference between internal class-level orchestration and external service orchestration points to one of the many significant differences between service-based architecture and microservices in terms of granularity.

Because domain services are coarse-grained, regular `ACID` (atomicity, consistency, isolation, durability) database transactions involving database commits and rollbacks are used to ensure database integrity within a single domain service. Highly distributed architectures like microservices, on the other hand, usually have fine-grained services and use a distributed transaction technique known as `BASE` transactions (basic availability, soft state, eventual consistency) transactions that rely on eventual consistency and hence do not support the same level of database integrity as ACID transactions in a service-based architecture.

## Database Partitioning
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1306.png)

Figure 13-6. Using a single shared library for database entity objects

One way to mitigate the impact and risk of database changes is to logically partition the database and manifest the logical partitioning through federated shared libraries. Notice in Figure 13-7 that the database is logically partitioned into five separate domains (common, customer, invoicing, order, and tracking). Also notice that there are five corresponding shared libraries used by the domain services matching the logical partitions in the database.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1307.png)

Figure 13-7. Using multiple shared libraries for database entity objects

## Architecture Characteristics Ratings
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1309.png)

Figure 13-9. Service-based architecture characteristics ratings

In the electronics recycling example, the system contains two quanta, as illustrated in Figure 13-10: one for the customer-facing portion of the application containing a separate customer user interface, database, and set of services (Quoting and Item Status); and one for the internal operations of receiving, assessing, and recycling the electronic device.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1310.png)

Figure 13-10. Separate quanta in a service-based architecture

## When to Use This Architecture Style
Service-based architecture is also a natural fit when doing domain-driven design. Because services are coarse-grained and domain-scoped, each domain fits nicely into a separately deployed domain service.

Maintaining and coordinating database transactions is always an issue with distributed architectures in that they typically rely on eventual consistency rather than traditional ACID (atomicity, consistency, isolation, and durability) transactions. However, service-based architecture preserves ACID transactions better than any other distributed architecture due to the coarse-grained nature of the domain services.

# 14.Event-Driven Architecture Style
Most applications follow what is called a `request-based` model (illustrated in Figure 14-1). In this model, requests made to the system to perform some sort of action are send to a `request orchestrator`. The request orchestrator is typically a user interface, but it can also be implemented through an API layer or enterprise service bus. The role of the request orchestrator is to deterministically and synchronously direct the request to various `request processors`. The request processors handle the request, either retrieving or updating information in a database.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1401.png)

Figure 14-1. Request-based model

## Topology
There are two primary topologies within event-driven architecture: the `mediator topology` and the `broker topology`.

The mediator topology is commonly used when you require control over the workflow of an event process, whereas the broker topology is used when you require a high degree of responsiveness and dynamic control over the processing of an event.

## Broker Topology
The broker topology differs from the mediator topology in that there is no central event mediator. Rather, the message flow is distributed across the event processor components in a chain-like broadcasting fashion through a lightweight message broker (such as RabbitMQ, ActiveMQ, HornetQ, and so on). 

The `initiating event` is the initial event that starts the entire event flow, whether it be a simple event like placing a bid in an online auction or more complex events in a health benefits system like changing a job or getting married. The initiating event is sent to an event channel in the `event broker` for processing. Since there is no mediator component in the broker topology managing and controlling the event, a single `event processor` accepts the initiating event from the event broker and begins the processing of that event. The event processor that accepted the initiating event performs a specific task associated with the processing of that event, then asynchronously advertises what it did to the rest of the system by creating what is called a `processing event`. This processing event is then asynchronously sent to the event broker for further processing, if needed. Other event processors listen to the processing event, react to that event by doing something, then advertise through a new processing event what they did. This process continues until no one is interested in what a final event processor did. Figure 14-2 illustrates this event processing flow.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1402.png)

Figure 14-2. Broker topology

It is always a good practice within the broker topology for each event processor to advertise what it did to the rest of the system, regardless of whether or not any other event processor cares about what that action was. This practice provides architectural extensibility if additional functionality is required for the processing of that event. For example, suppose as part of a complex event process, as illustrated in Figure 14-3, an email is generated and sent to a customer notifying them of a particular action taken. The Notification event processor would generate and send the email, then advertise that action to the rest of the system through a new processing event sent to a topic. However, in this case, no other event processors are listening for events on that topic, and as such the message simply goes away.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1403.png)

Figure 14-3. Notification event is sent but ignored

This is a good example of `architectural extensibility`. While it may seem like a waste of resources sending messages that are ignored, it is not. Suppose a new requirement comes along to analyze emails that have been sent to customers. This new event processor can be added to the overall system with minimal effort because the email information is available via the email topic to the new analyzer without having to add any additional infrastructure or apply any changes to other event processors.

Table 14-1. Trade-offs of the broker topology

Advantages | Disadvantages
-----------|--------------
Highly decoupled event processors | Workflow control
High scalability | Error handling
High responsiveness | Recoverability
High performance | Restart capabilities
High fault tolerance | Data inconsistency

## Mediator Topology
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1405.png)

Figure 14-5. Mediator topology

Table 14-2. Trade-offs of the mediator topology

Advantages | Disadvantages
-----------|--------------
Workflow control | More coupling of event processors
Error handling | Lower scalability
Recoverability | Lower performance
Restart capabilities | Lower fault tolerance
Better data consistency | Modeling complex workflows

## Asynchronous Capabilities
The event-driven architecture style offers a unique characteristic over other architecture styles in that it relies solely on asynchronous communication for both fire-and-forget processing (no response required) as well as request/reply processing (response required from the event consumer). Asynchronous communication can be a powerful technique for increasing the overall responsiveness of a system.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1413.png)

Figure 14-13. Synchronous versus asynchronous communication

## Error Handling
The workflow event pattern of reactive architecture is one way of addressing the issues associated with error handling in an asynchronous workflow. This pattern is a reactive architecture pattern that addresses both resiliency and responsiveness. In other words, the system can be resilient in terms of error handling without an impact to responsiveness.

The workflow event pattern leverages delegation, containment, and repair through the use of a `workflow delegate`, as illustrated in Figure 14-14.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1414.png)

Figure 14-14. Workflow event pattern of reactive architecture

## Preventing Data Loss
Data loss is always a primary concern when dealing with asynchronous communications. Unfortunately, there are many places for data loss to occur within an event-driven architecture. By data loss we mean a message getting dropped or never making it to its final destination. Fortunately, there are basic out-of-the-box techniques that can be leveraged to prevent data loss when using asynchronous messaging.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1416.png)

Figure 14-16. Where data loss can happen within an event-driven architecture

- Issue 1 (the message never makes it to the queue) is easily solved by leveraging persisted message queues, along with something called `synchronous send`. Persisted message queues support what is known as guaranteed delivery. 
- Issue 2 (Event Processor B de-queues the next available message and crashes before it can process the event) can also be solved using a basic technique of messaging called `client acknowledge mode`. By default, when a message is de-queued, it is immediately removed from the queue (something called auto acknowledge mode). Client acknowledge mode keeps the message in the queue and attaches the client ID to the message so that no other consumers can read the message. 
- Issue 3 (Event Processor B is unable to persist the message to the database due to some data error) is addressed through leveraging ACID (atomicity, consistency, isolation, durability) transactions via a database commit. Once the database commit happens, the data is guaranteed to be persisted in the database. Leveraging something called `last participant support` (LPS) removes the message from the persisted queue by acknowledging that processing has been completed and that the message has been persisted. 

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1417.png)

Figure 14-17. Preventing data loss within an event-driven architecture

## Broadcast Capabilities
One of the other unique characteristics of event-driven architecture is the capability to broadcast events without knowledge of who (if anyone) is receiving the message and what they do with it. This technique, which is illustrated in Figure 14-18, shows that when a producer publishes a message, that same message is received by multiple subscribers.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1418.png)

Figure 14-18. Broadcasting events to other event processors

## Request-Reply
In event-driven architecture, synchronous communication is accomplished through `request-reply` messaging (sometimes referred to as pseudosynchronous communications). Each event channel within request-reply messaging consists of two queues: a request queue and a reply queue. 

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1419.png)

Figure 14-19. Request-reply message processing

## Choosing Between Request-Based and Event-Based
We recommend choosing the request-based model for well-structured, data-driven requests (such as retrieving customer profile data) when certainty and control over the workflow is needed. We recommend choosing the event-based model for flexible, action-based events that require high levels of responsiveness and scale, with complex and dynamic user processing.

Table 14-3. Trade-offs of the event-driven model

Advantages over request-based |  Trade-offs
---|---
Better response to dynamic user content | Only supports eventual consistency
Better scalability and elasticity | Less control over processing flow
Better agility and change management| Less certainty over outcome of event flow
Better adaptability and extensibility | Difficult to test and debug
Better responsiveness and performanceBetter real-time decision making | -
Better reaction to situational awareness | -

## Architecture Characteristics Ratings
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1422.png)

Figure 14-22. Event-driven architecture characteristics ratings

# 15.Space-Based Architecture Style
Most web-based business applications follow the same general request flow: a request from a browser hits the web server, then an application server, then finally the database server. While this pattern works great for a small set of users, bottlenecks start appearing as the user load increases, first at the web-server layer, then at the application-server layer, and finally at the database-server layer. The usual response to bottlenecks based on an increase in user load is to scale out the web servers. This is relatively easy and inexpensive, and it sometimes works to address the bottleneck issues. However, in most cases of high user load, scaling out the web-server layer just moves the bottleneck down to the application server. Scaling application servers can be more complex and expensive than web servers and usually just moves the bottleneck down to the database server, which is even more difficult and expensive to scale. Even if you can scale the database, what you eventually end up with is a triangle-shaped topology, with the widest part of the triangle being the web servers (easiest to scale) and the smallest part being the database (hardest to scale), as illustrated in Figure 15-1.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1501.png)

Figure 15-1. Scalability limits within a traditional web-based topology

## General Topology
Space-based architecture gets its name from the concept of `tuple space`, the technique of using multiple parallel processors communicating through shared memory. High scalability, high elasticity, and high performance are achieved by removing the central database as a synchronous constraint in the system and instead leveraging replicated in-memory data grids. Application data is kept in-memory and replicated among all the active processing units. When a processing unit updates data, it asynchronously sends that data to the database, usually via messaging with persistent queues. Processing units start up and shut down dynamically as user load increases and decreases, thereby addressing variable scalability.

There are several architecture components that make up a space-based architecture: a `processing unit` containing the application code, `virtualized middleware` used to manage and coordinate the processing units, `data pumps` to asynchronously send updated data to the database, `data writers` that perform the updates from the data pumps, and `data readers` that read database data and deliver it to processing units upon startup.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1502.png)

Figure 15-2. Space-based architecture basic topology

### Processing Unit
The processing unit (illustrated in Figure 15-3) contains the application logic (or portions of the application logic). This usually includes web-based components as well as backend business logic.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1503.png)

Figure 15-3. Processing unit

### Virtualized Middleware
The virtualized middleware handles the infrastructure concerns within the architecture that control various aspects of data synchronization and request handling. The components that make up the virtualized middleware include a `messaging grid`, `data grid`, `processing grid`, and `deployment manager`.

#### Messaging grid
The messaging grid, shown in Figure 15-4, manages input request and session state. When a request comes into the virtualized middleware, the messaging grid component determines which active processing components are available to receive the request and forwards the request to one of those processing units. The complexity of the messaging grid can range from a simple round-robin algorithm to a more complex next-available algorithm that keeps track of which request is being processed by which processing unit. This component is usually implemented using a typical web server with load-balancing capabilities (such as HA Proxy and Nginx).

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1504.png)

Figure 15-4. Messaging grid

#### Data grid
The data grid component is perhaps the most important and crucial component in this architecture style. In most modern implementations the data grid is implemented solely within the processing units as a replicated cache. However, for those replicated caching implementations that require an external controller, or when using a distributed cache, this functionality would reside in both the processing units as well as in the data grid component within the virtualized middleware. Since the messaging grid can forward a request to any of the processing units available, it is essential that each processing unit contains exactly the same data in its in-memory data grid. Although Figure 15-5 shows a synchronous data replication between processing units, in reality this is done asynchronously and very quickly, usually completing the data synchronization in less than 100 milliseconds.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1505.png)

Figure 15-5. Data grid

Data replication within the processing units also allows service instances to come up and down without having to read data from the database, providing there is at least one instance containing the named replicated cache.

#### Processing grid
The processing grid, illustrated in Figure 15-6, is an optional component within the virtualized middleware that manages orchestrated request processing when there are multiple processing units involved in a single business request. If a request comes in that requires coordination between processing unit types (e.g., an order processing unit and a payment processing unit), it is the processing grid that mediates and orchestrates the request between those two processing units.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1506.png)

Figure 15-6. Processing grid

#### Deployment manager
The deployment manager component manages the dynamic startup and shutdown of processing unit instances based on load conditions. This component continually monitors response times and user loads, starts up new processing units when load increases, and shuts down processing units when the load decreases. It is a critical component to achieving variable scalability (elasticity) needs within an application.

#### Data Pumps
A data pump is a way of sending data to another processor which then updates data in a database.

Data pumps are usually implemented using messaging, as shown in Figure 15-7. 

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1507.png)

Figure 15-7. Data pump used to send data to a database

#### Data Writers
The data writer component accepts messages from a data pump and updates the database with the information contained in the message of the data pump (see Figure 15-7). Data writers can be implemented as services, applications, or data hubs (such as Ab Initio). The granularity of the data writers can vary based on the scope of the data pumps and processing units.

A domain-based data writer contains all of the necessary database logic to handle all the updates within a particular domain (such as customer), regardless of the number of data pumps it is accepting.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1508.png)

Figure 15-8. Domain-based data writer

Alternatively, each class of processing unit can have its own dedicated data writer component, as illustrated in Figure 15-9. In this model the data writer is dedicated to each corresponding data pump and contains only the database processing logic for that particular processing unit (such as Wallet).

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1509.png)

Figure 15-9. Dedicated data writers for each data pump

#### Data Readers
Whereas data writers take on the responsibility for updating the database, data readers take on the responsibility for reading data from the database and sending it to the processing units via a reverse data pump. In space-based architecture, data readers are only invoked under one of three situations: a crash of all processing unit instances of the same named cache, a redeployment of all processing units within the same named cache, or retrieving archive data not contained in the replicated cache.

In the event where all instances come down (due to a system-wide crash or redeployment of all instances), data must be read from the database (something that is generally avoided in space-based architecture). 

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1510.png)

Figure 15-10. Data reader with reverse data pump

## Data Collisions
When using replicated caching in an active/active state where updates can occur to any service instance containing the same named cache, there is the possibility of a `data collision` due to replication latency. 

## Cloud Versus On-Premises Implementations
A powerful feature of this architecture style (as illustrated in Figure 15-11) is to deploy applications via processing units and virtualized middleware in managed cloud-based environments while keeping the physical databases and corresponding data on-prem.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1511.png)

Figure 15-11. Hybrid cloud-based and on-prem topology

## Replicated Versus Distributed Caching
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1512.png)

Figure 15-12. Replicated caching between processing units

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1513.png)

Figure 15-13. Distributed caching between processing units

Table 15-1. Distributed versus replicated caching

Decision criteria | Replicated cache | Distributed cache
------------------|------------------|------------------
Optimization | Performance | Consistency
Cache size | Small (<100 MB) | Large (>500 MB)
Type of data | Relatively static | Highly dynamic
Update frequency | Relatively low | High update rate
Fault tolerance | High | Low

## Near-Cache Considerations
A near-cache is a type of caching hybrid model bridging in-memory data grids with a distributed cache. In this model (illustrated in Figure 15-14) the distributed cache is referred to as the full backing cache, and each in-memory data grid contained within each processing unit is referred to as the front cache. The front cache always contains a smaller subset of the full backing cache, and it leverages an eviction policy to remove older items so that newer ones can be added. The front cache can be what is known as a most recently used (MRU) cache containing the most recently used items or a most frequently used (MFU) cache containing the most frequently used items. Alternatively, a random replacement eviction policy can be used in the front cache so that items are removed in a random manner when space is needed to add a new item. Random replacement (RR) is a good eviction policy when there is no clear analysis of the data with regard to keeping either the latest used versus the most frequently used.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1514.png)

Figure 15-14. Near-cache topology

## Architecture Characteristics Ratings
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1515.png)

Figure 15-15. Space-based architecture characteristics ratings

# 16.Orchestration-Driven Service-Oriented Architecture
## Topology
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1601.png)

Figure 16-1. Topology of orchestration-driven service-oriented architecture

## Taxonomy
### Business Services
Business services sit at the top of this architecture and provide the entry point. 

These service definitions contained no code—just input, output, and sometimes schema information. They were usually defined by business users, hence the name business services.

### Enterprise Services
The enterprise services contain fine-grained, shared implementations. Typically, a team of developers is tasked with building atomic behavior around particular business domains: CreateCustomer, CalculateQuote, and so on. These services are the building blocks that make up the coarse-grained business services, tied together via the orchestration engine.

This separation of responsibility flows from the reuse goal in this architecture.

### Application Services
Not all services in the architecture require the same level of granularity or reuse as the enterprise services. Application services are one-off, single-implementation services.

### Infrastructure Services
Infrastructure services supply the operational concerns, such as monitoring, logging, authentication, and authorization. These services tend to be concrete implementations, owned by a shared infrastructure team that works closely with operations.

### Orchestration Engine
The orchestration engine forms the heart of this distributed architecture, stitching together the business service implementations using orchestration, including features like transactional coordination and message transformation.

The orchestration engine defines the relationship between the business and enterprise services, how they map together, and where transaction boundaries lie. It also acts as an integration hub, allowing architects to integrate custom code with package and legacy software systems.

### Message Flow
All requests go through the orchestration engine—it is the location within this architecture where logic resides. Thus, message flow goes through the engine even for internal calls, as shown in Figure 16-2.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1602.png)

Figure 16-2. Message flow with service-oriented architecture

## Reuse…and Coupling
A major goal of this architecture is reuse at the service level—the ability to gradually build business behavior that can be incrementally reused over time. Architects in this architecture were instructed to find reuse opportunities as aggressively as possible. 

## Architecture Characteristics Ratings
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1605.png)

Figure 16-5. Ratings for service-oriented architecture

# 17.Microservices Architecture
## Topology
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1701.png)

Figure 17-1. The topology of the microservices architecture style

## Distributed
Microservices form a distributed architecture: each service runs in its own process, which originally implied a physical computer but quickly evolved to virtual machines and containers.

## Bounded Context
The driving philosophy of microservices is the notion of bounded context: each service models a domain or workflow. Thus, each service includes everything necessary to operate within the application, including classes, other subcomponents, and database schemas. 

Microservices take the concept of a domain-partitioned architecture to the extreme. Each service is meant to represent a domain or subdomain; in many ways, microservices is the physical embodiment of the logical concepts in domain-driven design.

### Granularity
Architects struggle to find the correct granularity for services in microservices, and often make the mistake of making their services too small, which requires them to build communication links back between the services to do useful work.

### Data Isolation
Another requirement of microservices, driven by the bounded context concept, is data isolation. Many other architecture styles use a single database for persistence. However, microservices tries to avoid all kinds of coupling, including shared schemas and databases used as integration points.

## API Layer
While an API layer may be used for variety of things, it should not be used as a mediator or orchestration tool if the architect wants to stay true to the underlying philosophy of this architecture: all interesting logic in this architecture should occur inside a bounded context, and putting orchestration or other logic in a mediator violates that rule. This also illustrates the difference between technical and domain partitioning in architecture: **architects typically use mediators in technically partitioned architectures, whereas microservices is firmly domain partitioned**.

## Operational Reuse
One of the philosophies in the traditional service-oriented architecture was to reuse as much functionality as possible, domain and operational alike. In microservices, architects try to split these two concerns.

Once a team has built several microservices, they realize that each has common elements that benefit from similarity. For example, if an organization allows each service team to implement monitoring themselves, how can they ensure that each team does so? And how do they handle concerns like upgrades? Does it become the responsibility of each team to handle upgrading to the new version of the monitoring tool, and how long will that take?

The `sidecar` pattern offers a solution to this problem, illustrated in Figure 17-2.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1702.png)

Figure 17-2. The sidecar pattern in microservices

Once teams know that each service includes a common sidecar, they can build a `service mesh`, allowing unified control across the architecture for concerns like logging and monitoring. The common sidecar components connect to form a consistent operational interface across all microservices, as shown in Figure 17-3.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1703.png)

Figure 17-3. The service plane connects the sidecars in a service mesh

The service mesh itself forms a console that allows developers holistic access to services, which is shown in Figure 17-4.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1704.png)

Figure 17-4. The service mesh forms a holistic view of the operational aspect of microservices

Architects use `service discovery` as a way to build elasticity into microservices architectures. Rather than invoke a single service, a request goes through a service discovery tool, which can monitor the number and frequency of requests, as well as spin up new instances of services to handle scale or elasticity concerns. Architects often include service discovery in the service mesh, making it part of every microservice. The `API layer` is often used to host service discovery, allowing a single place for user interfaces or other calling systems to find and create services in an elastic, consistent way.

## Frontends
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1705.png)

Figure 17-5. Microservices architecture with a monolithic user interface

The second option for user interfaces uses microfrontends, shown in Figure 17-6.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1706.png)

Figure 17-6. Microfrontend pattern in microservices

## Communication
Microservices architectures typically utilize `protocol-aware heterogeneous interoperability`. We’ll break down that term for you:

- Protocol-aware
  - Because microservices usually don’t include a centralized integration hub to avoid operational coupling, each service should know how to call other services. Thus, architects commonly standardize on how particular services call each other: a certain level of REST, message queues, and so on. That means that services must know (or discover) which protocol to use to call other services.
- Heterogeneous
  - Because microservices is a distributed architecture, each service may be written in a different technology stack. Heterogeneous suggests that microservices fully supports polyglot environments, where different services use different platforms.
- Interoperability
  - While architects in microservices try to discourage transactional method calls, services commonly call other services via the network to collaborate and send/receive information.

### Choreography and Orchestration
`Choreography` utilizes the same communication style as a broker event-driven architecture. In other words, no central coordinator exists in this architecture, respecting the bounded context philosophy. Thus, architects find it natural to implement decoupled events between services.

`Domain/architecture isomorphism` is one key characteristic that architects should look for when assessing how appropriate an architecture style is for a particular problem.

In choreography, each service calls other services as needed, without a central mediator. For example, consider the  scenario shown in Figure 17-7.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1707.png)

Figure 17-7. Using choreography in microservices to manage coordination

Because microservices architectures don’t include a global mediator like other service-oriented architectures, if an architect needs to coordinate across several services, they can create their own localized mediator, as shown in Figure 17-8.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1708.png)

Figure 17-8. Using orchestration in microservices

Consider an example with a more complex workflow, shown in Figure 17-9.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1709.png)

Figure 17-9. Using choreography for a complex business process

In Figure 17-9, the first service called must coordinate across a wide variety of other services, basically acting as a mediator in addition to its other domain responsibilities. This pattern is called the `front controller` pattern, where a nominally choreographed service becomes a more complex mediator for some problem.

Alternatively, an architect may choose to use `orchestration` for complex business processes, illustrated in Figure 17-10.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1710.png)

Figure 17-10. Using orchestration for a complex business process

### Transactions and Sagas
A popular distributed transactional pattern in microservices is the `saga pattern`, illustrated in Figure 17-11.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1711.png)

Figure 17-11. The saga pattern in microservices architecture

In an error condition, the mediator must ensure that no part of the transaction succeeds if one part fails. Consider the situation shown in Figure 17-12.

![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1712.png)

Figure 17-12. Saga pattern compensating transactions for error conditions

This style of transactional coordination is called a `compensating transaction framework`. Developers implement this pattern by usually having each request from the mediator enter a `pending` state until the mediator indicates overall success. 

## Architecture Characteristics Ratings
![](https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/assets/fosa_1713.png)

Figure 17-13. Ratings for microservices

# III.Techniques and Soft Skills
# 19.Architecture Decisions










































































































