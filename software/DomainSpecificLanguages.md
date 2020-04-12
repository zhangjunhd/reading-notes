![]()



- [oreilly](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/)

---

- [I.Narratives](#inarratives)
- [1. An Introductory Example](#1-an-introductory-example)
  - [1.1 Gothic Security](#11-gothic-security)
    - [1.1.1 Miss Grant’s Controller](#111-miss-grants-controller)
  - [1.2 The State Machine Model](#12-the-state-machine-model)
  - [1.3 Programming Miss Grant’s Controller](#13-programming-miss-grants-controller)
  - [1.4 Languages and Semantic Model](#14-languages-and-semantic-model)
  - [1.5 Using Code Generation](#15-using-code-generation)
- [2.Using Domain-Specific Languages](#2using-domain-specific-languages)
  - [2.1 Defining Domain-Specific Languages](#21-defining-domain-specific-languages)
    - [2.1.1 Boundaries of DSLs](#211-boundaries-of-dsls)
  - [2.2 Why Use a DSL?](#22-why-use-a-dsl)
    - [2.2.1 Improving Development Productivity](#221-improving-development-productivity)
    - [2.2.2 Communication with Domain Experts](#222-communication-with-domain-experts)
    - [2.2.3 Change in Execution Context](#223-change-in-execution-context)
    - [2.2.4 Alternative Computational Model](#224-alternative-computational-model)
  - [2.3 Problems with DSLs](#23-problems-with-dsls)
    - [2.3.1 Language Cacophony](#231-language-cacophony)
    - [2.3.2 Cost of Building](#232-cost-of-building)
    - [2.3.3 Ghetto Language](#233-ghetto-language)
    - [2.3.4 Blinkered Abstraction](#234-blinkered-abstraction)
- [3.Implementing DSLs](#3implementing-dsls)
  - [3.1 Architecture of DSL Processing](#31-architecture-of-dsl-processing)
  - [3.2 The Workings of a Parser](#32-the-workings-of-a-parser)
  - [3.3 Grammars, Syntax, and Semantics](#33-grammars-syntax-and-semantics)
  - [3.4 Parsing Data](#34-parsing-data)
- [4.Implementing an Internal DSL](#4implementing-an-internal-dsl)
  - [4.1 Fluent and Command-Query APIs](#41-fluent-and-command-query-apis)
  - [4.2 The Need for a Parsing Layer](#42-the-need-for-a-parsing-layer)

# I.Narratives
# 1. An Introductory Example
## 1.1 Gothic Security
### 1.1.1 Miss Grant’s Controller
![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/intro_basic.jpg)

Figure 1.1 State diagram for Miss Grant’s secret compartment

## 1.2 The State Machine Model
When working in Java, the natural way to do this is through a `Domain Model` [Fowler PoEAA] of a state machine.

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/intro_statemodel.jpg)

Figure 1.2 Class diagram of the state machine framework

I keep them as separate classes (with a superclass) as they play different roles in the controller code.

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/p0006_01.jpg)

The state class keeps track of the commands that it will send and its outbound transitions.

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/p0006_02.jpg)

The state machine holds on to its start state.

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/p0007_01.jpg)

Then, any other states in the machine are those reachable from this state.

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/p0007_02.jpg)

To handle reset events, I keep a list of them on the state machine.

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/p0008_01.jpg)

I don’t need to have a separate structure for reset events like this. I could handle this by simply declaring extra transitions on the state machine like this:

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/p0008_02.jpg)

The controller has a handle method that takes the event code it receives from the device.

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/p0008_03.jpg)

## 1.3 Programming Miss Grant’s Controller
Now that I’ve implemented the state machine model, I can program Miss Grant’s controller like this:

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/p0009_01.jpg)

Essentially, it is the separation of common code from variable code. We structure the common code in a set of components that we then configure for different purposes.

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/intro_multipleconfig.jpg)

Figure 1.3 A single library used with multiple configurations

Here is another way of representing that configuration code:

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/p0011_01.jpg)

Here’s another version of the configuration code:

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/p0012_01.jpg)

This language is a domain-specific language that shares many of the characteristics of DSLs. Now look at this code.

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/p0014_01.jpg)

It’s a bit noisier than the custom language earlier, but still pretty clear. Readers whose language likings are similar to mine will probably recognize it as Ruby. 

An `external DSL` is a domain-specific language represented in a separate language to the main programming language it’s working with. This language may use a custom syntax, or it may follow the syntax of another representation such as XML. An `internal DSL` is a DSL represented within the syntax of a general-purpose language. It’s a stylized use of that language for a domain-specific purpose.

You may also hear the term `embedded DSL` as a synonym for internal DSL.

Now think again about the original Java configuration code. Is this a DSL? I would argue that it isn’t. Does this mean you can’t do an internal DSL in Java? How about this:

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/p0015_01.jpg)

It’s formatted oddly, and uses some unusual programming conventions, but it is valid Java. This I would call a DSL; although it’s more messy than the Ruby DSL, it still has that declarative flow that a DSL needs.

Another term you may come across for an internal DSL is a `fluent interface`. This term emphasizes the fact that an internal DSL is really just a particular kind of API, designed with this elusive quality of fluency. Given this distinction, it’s useful to have a name for a nonfluent API—I’ll use the `term command-query API`.

## 1.4 Languages and Semantic Model
If you’re used to using Domain Models [Fowler PoEAA], for the moment you can think of a Semantic Model as very close to the same thing.

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/semanticmodel_sketch.jpg)

Figure 1.4 Parsing a DSL populates a Semantic Model.

One opinion I’ve formed is that the Semantic Model is a vital part of a well-designed DSL. In the wild you’ll find some DSLs use a Semantic Model and some do not, but I’m very much of the opinion that you should almost always use a Semantic Model.

## 1.5 Using Code Generation
In my discussion so far, I process the DSL to populate the Semantic Model and then execute the Semantic Model to provide the behavior that I want from the controller. This approach is what’s known in language circles as `interpretation`. When we interpret some text, we parse it and immediately produce the result that we want from the program.

In the language world, the alternative to interpretation is `compilation`. With compilation, we parse some program text and produce an intermediate output, which is then separately processed to provide the behavior we desire. In the context of DSLs, the compilation approach is usually referred to as `code generation`.

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/intro_interpreted.jpg)

Figure 1.5 An interpreter parses the text and produces its result in a single process.

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/intro_compiled.jpg)

Figure 1.6 A compiler parses the text and produces some intermediate code which is then packaged into another process for execution.

# 2.Using Domain-Specific Languages
## 2.1 Defining Domain-Specific Languages
`Domain-specific language` (noun): a computer programming language of limited expressiveness focused on a particular domain.

### 2.1.1 Boundaries of DSLs
I’ll start with internal DSLs.Mike Roberts suggested to me that a command-query API defines the vocabulary of the abstraction, whereas an internal DSL adds a grammar.

A common way of documenting a class with a command-query API is to list all the methods it has. The methods of an internal DSL often only make sense in the context of a larger expression in the DSL.

As a result, an internal DSL should have the feel of putting together whole sentences, rather than a sequence of disconnected commands. This is the basis for calling these kinds of APIs fluent interfaces.

With external DSLs, the boundary is with general-purpose programming languages. Languages can have a domain focus but still be general-purpose languages.

A more obvious DSL is regular expressions. Here, the domain focus (matching text) is coupled with limited features—just enough to make text matching easy. One common indicator of a DSL is that it isn’t `Turing-complete`.

## 2.2 Why Use a DSL?
### 2.2.1 Improving Development Productivity
The heart of the appeal of a DSL is that it provides a means to more clearly communicate the intent of a part of a system.

The model alone provides a considerable improvement in productivity. It avoids duplication by gathering together common code; above all, it provides an abstraction to think about the problem that makes it easier to specify what’s going on in an understandable way. A DSL enhances this by providing a more expressive form to read and manipulate that abstraction. A DSL can help people learn how to use an API since it shifts focus to how different API methods should be combined together.

### 2.2.2 Communication with Domain Experts
When people talk about DSLs in this context, it’s often along the lines of “Now we can get rid of programmers and have business people specify the rules themselves.” I call this argument the `COBOL fallacy`—since that was the expectation with COBOL.

Despite the COBOL fallacy, I do think DSLs can improve communication. It’s not that domain experts will write the DSLs themselves; but they can read them and thus understand what the system thinks it’s doing. By being able to read DSL code, domain experts can spot mistakes. They can also talk more effectively to the programmers who do write the rules, perhaps by writing some rough drafts that can be refined into proper DSL rules.

### 2.2.3 Change in Execution Context
Using a DSL like this can often make up for limitations in a host language, allowing us to express things in a comfortable DSL and then generate code for the actual execution environment to use.

A model can facilitate this kind of shift. Once you have a model, it’s easy to either execute it directly or generate code from it. Models can be also be populated from a forms-style interface as well as a DSL. A DSL has a couple of advantages over using forms. DSLs are often better than forms at representing complicated logic.

### 2.2.4 Alternative Computational Model
Mainstream programming is pretty much all done using an `imperative` model of computation. Imperative computation has become popular because it’s relatively easy to understand and easy to apply to lots of problems. However, it isn’t always the best choice.

You often hear such `nonimperative` approaches referred to as `declarative programming`. The notion is that these styles allow you to declare `what` should happen, rather than work through the imperative statements that describe `how` the behavior works.

## 2.3 Problems with DSLs
### 2.3.1 Language Cacophony
The most common objection I hear to DSLs is what I call the `language cacophony problem`: the concern that languages are hard to learn, so using many languages will be much more complicated than using a single one.

### 2.3.2 Cost of Building
Even if a DSL might help, sometimes it would just be too much effort to build and maintain for the marginal benefit.

### 2.3.3 Ghetto Language
The ghetto language problem is a contrast to the language cacophony problem. Here, we have a company that’s built a lot of its systems on an in-house language which is not used anywhere else. This makes it difficult for them to find new staff and to keep up with technological changes.

### 2.3.4 Blinkered Abstraction
The usefulness of a DSL is that it provides an abstraction that you can use to think about a subject area. Such an abstraction is really valuable; it allows you to express the behavior of a domain much more easily than if you think in terms of lower-level constructs.

With a blinkered abstraction, you spend more effort on fitting the world into your abstraction than the other way around. You see this when you come across something that doesn’t fit in with the abstraction—and you burn time trying to make it fit, instead of changing the abstraction to easily absorb the new behavior.

# 3.Implementing DSLs
## 3.1 Architecture of DSL Processing
![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/implementingdsl_overview.jpg)

Figure 3.1 The overall architecture of DSL processing that I usually prefer

## 3.2 The Workings of a Parser
So the differences between internal and external DSLs lie entirely in parsing, and indeed there are many differences in detail between the two. 

In the external syntax, it looked something like this:

```
events
    doorClosed D1CL
    drawerOpened D2OP
end
```

We can take a similar view in the Ruby internal DSL.

```ruby
event :doorClosed "D1CL"
event :drawerOpened "D2OP"
```

Whenever you look at a script like this, you can imagine that script as a hierarchy; such a hierarchy is called a `syntax tree` (or parse tree).

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/implementingdsl_astvssemanticmodel.jpg)

Figure 3.2 A syntax tree and a semantic model are usually different representations of a DSL script.

## 3.3 Grammars, Syntax, and Semantics
A `grammar` is a set of rules which describe how a stream of text is turned into a `syntax tree`.

## 3.4 Parsing Data
Let’s take a fragment of a state machine example:

```
commands
    unlockDoor D1CL
end

state idle
    actions {unlockDoor}
end
```

Here we see a common situation: A command is defined in one part of the language and referred to somewhere else. When the command is referred to as part of the state’s actions, we’re on a different branch of the syntax tree from where the command was defined. If the only representation of the syntax tree is on the call stack, then the command definition has disappeared by now. As a result, we need to store the command object for later use so we can resolve the reference in the action clause.

In order to do this, we use a `Symbol Table`, which is essentially a dictionary whose key is the identifier unlockDoor and whose value is an object that represents the command in our parse. When we process the text unlockDoor D1UL, we create an object to hold that data and stash it in the Symbol Table under the key unlockDoor. The object we stash may be the semantic model object for a command, or it could be an intermediate object that’s local to the syntax tree. Later, when we process actions {unlockDoor}, we look up that object using the Symbol Table to capture the relationship between the state and its actions. **A Symbol Table is thus a crucial tool for making the cross-references**. 

![](https://learning.oreilly.com/library/view/domain-specific-languages/9780132107549/graphics/implementingdsl_symboltable.jpg)

Figure 3.3 Parsing creates both a parse tree and a symbol table.

# 4.Implementing an Internal DSL
## 4.1 Fluent and Command-Query APIs
For many people, the central pattern of a fluent interface is that of `Method Chaining`. A normal API might have code like this:

```java
Processor p = new Processor(2, 2500, Processor.Type.i386);
Disk d1 = new Disk(150, Disk.UNKNOWN_SPEED, null);
Disk d2 = new Disk(75, 7200, Disk.Interface.SATA);
return new Computer(p, d1, d2);
```

With Method Chaining, we can express the same thing with:

```
computer()
    .processor()
        .core(2)
        .speed(2500)
        .i386()
    .disk()
        .size(150)
    .disk()
        .size(75)
        .speed(7200)
        .sata()
    .end()
```

Here is the same thing using a sequence of method call statements, which I call a `Function Sequence`:

```java
computer();
    processor();
        core(2);
        speed(2500);
        i386();
    disk();
        size(150);
    disk();
        size(75);
        speed(7200);
        sata();
```

## 4.2 The Need for a Parsing Layer



































































































