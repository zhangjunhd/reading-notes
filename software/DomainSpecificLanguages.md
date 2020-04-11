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


































































































































































































