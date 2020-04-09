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

















































