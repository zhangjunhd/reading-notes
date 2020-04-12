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




































