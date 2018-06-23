# Understanding Computation
![cover](https://img3.doubanio.com/view/subject/l/public/s26742101.jpg)

    作者: Tom Stuart 
    出版社: O'Reilly Media
    副标题: From Simple Machines to Impossible Programs
    出版年: 2013-6-3
    页数: 332
    定价: USD 39.99
    装帧: Paperback
    ISBN: 9781449329273

- [豆瓣链接](https://book.douban.com/subject/19992840/)
- [safaribooksonline](https://www.safaribooksonline.com/library/view/understanding-computation/9781449330071/)

# Part I. Programs and Machines
To create an environment where this familiar sort of computation can occur, we need three basic ingredients:

- A `machine` capable of performing the computation
- A `language` for writing instructions that the machine can understand
- A `program` written in that language, describing the exact computation that the machine should perform

## Chapter 2. The Meaning of Programs
### The Meaning of “Meaning”
In linguistics, `semantics` is the study of the connection between words and their    meanings.  Semantics is concerned with how these concrete signifiers relate to their abstract meanings, as well as the fundamental nature of the abstract meanings themselves.

In computer science, the field of `formal    semantics` is concerned with finding ways of nailing down the elusive meanings of programs and using them to discover or prove interesting things about programming languages. Formal semantics has a wide spectrum of uses, from concrete applications like specifying new languages and devising compiler optimizations, to more abstract ones like constructing mathematical proofs of the correctness of programs.

### Syntax
Every programming language comes with a collection of rules that describe what    kind of character strings may be considered valid programs in that language; these rules specify the language’s `syntax`.

Reading programs requires a `parser`: a program that can read a character string representing a program, check it against the syntax rules   to make sure it’s valid, and turn it into a structured representation of that program suitable for further processing.

A parser should read a string like y = x + 1 and turn it into an `abstract syntax tree` (`AST`), a representation of the source code that discards incidental detail like  whitespace and focuses on the hierarchical structure of the program.

Syntax is only concerned with the surface appearance of programs, not with their meanings.

### Operational Semantics
This is the basis of `operational semantics`, a way of capturing the meaning of a programming language by defining rules for how its programs execute on some kind of device. This device is often an `abstract machine`: an imaginary, idealized computer that is designed for the specific purpose of explaining how the language’s programs will execute. Different kinds of programming language will usually require different designs of abstract machine in order to neatly capture their runtime behavior.

#### Small-Step Semantics
So, how can we design an abstract machine and use it to specify the operational semantics of a programming language? One way is to imagine a machine that evaluates a program by operating on its syntax directly, repeatedly `reducing` it in small steps, with each      step bringing the program closer to its final result, whatever that turns out to mean.

In this chapter, we’re going to explore the semantics of a toy programming language—let’s call it Simple. The mathematical description of Simple’s small-step semantics looks like this:

![](https://www.safaribooksonline.com/library/view/understanding-computation/9781449330071/httpatomoreillycomsourceoreillyimages1690688.png)

Mathematically speaking, this is a set of `inference rules` that defines a reduction relation on Simple’s abstract syntax trees.

Let’s wrap up that code and state  together in a class and call it a virtual machine:

#### Big-Step Semantics
We’ve now seen what `small-step operational semantics` looks like: we design an abstract machine that maintains some execution state, then define reduction rules that specify how each kind of program construct can make incremental progress toward being fully evaluated. In particular, small-step semantics **has a mostly iterative flavor**,   requiring the abstract machine to repeatedly perform reduction steps (the Ruby while loop in Machine#run) that are themselves constructed to produce as output the same kind of information that they require as input, making them suitable for this kind of repeated application.

The small-step approach has the advantage of slicing up the complex business of executing an entire program into smaller pieces that are easier to explain and analyze, but        it does feel a bit indirect: instead of explaining how a whole program construct works, we just show how it can be reduced slightly. Why can’t we explain a statement more directly, by telling a complete story about how its execution works? Well, we can, and that’s the basis of `big-step semantics`.

The idea of big-step semantics is to specify how to get from an expression or statement straight to its result. This necessarily      involves thinking about program **execution as a recursive rather than an iterative process**: big-step semantics says that, to evaluate a large expression, we evaluate all of its smaller subexpressions and then combine their results to get our final answer.

### Denotational Semantics
This style of semantics doesn’t directly address the question of executing a program at all. Instead, it concerns itself with leveraging the established meaning of another language—one that is lower-level, more formal, or at least better understood than the language being described—in order to explain a new one.

`Denotational semantics` is necessarily a more abstract approach than operational, because it just replaces one language with another instead of turning a language into real behavior.

































