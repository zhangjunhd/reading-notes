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





































































































































