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













































































































































































































































