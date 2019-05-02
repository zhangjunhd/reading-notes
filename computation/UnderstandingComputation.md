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

The small-step approach has the advantage of slicing up the complex business of executing an entire program into smaller pieces that are easier to explain and analyze, but it does feel a bit indirect: instead of explaining how a whole program construct works, we just show how it can be reduced slightly. Why can’t we explain a statement more directly, by telling a complete story about how its execution works? Well, we can, and that’s the basis of `big-step semantics`.

The idea of big-step semantics is to specify how to get from an expression or statement straight to its result. This necessarily      involves thinking about program **execution as a recursive rather than an iterative process**: big-step semantics says that, to evaluate a large expression, we evaluate all of its smaller subexpressions and then combine their results to get our final answer.

### Denotational Semantics
This style of semantics doesn’t directly address the question of executing a program at all. Instead, it concerns itself with leveraging the established meaning of another language—one that is lower-level, more formal, or at least better understood than the language being described—in order to explain a new one.

`Denotational semantics` is necessarily a more abstract approach than operational, because it just replaces one language with another instead of turning a language into real behavior.

### Formal Semantics in Practice
The branch of mathematics called `domain theory` was developed specifically to provide definitions and objects that are useful for denotational semantics, allowing a model of computation based on [fixed points][1] of [monotonic functions][2] on [partially ordered sets][3]. Programs can be understood by “compiling” them into mathematical functions, and the techniques of domain theory can be used to prove interesting properties of these functions.

`Small-step semantics` is also known as `structural operational semantics` and `transition semantics`; `big-step semantics` is more often called `natural semantics` or `relational semantics`; and `denotational semantics` is also called `fixed-point semantics` or `mathematical semantics`.

Other styles of formal semantics are available. One alternative is `axiomatic semantics`, which describes the meaning of a statement by making assertions about the state of the abstract machine before and after that statement executes: if one assertion (the precondition) is initially true before the statement is executed,      then the other assertion (the postcondition) will be true afterward. Axiomatic semantics is useful for verifying the correctness of programs: as statements are plugged together to make larger programs, their corresponding assertions can be plugged together to make larger assertions, with the goal of showing that an overall assertion about a program matches up with its intended specification.

## Chapter 3. The Simplest Computers
### Deterministic Finite Automata
A `finite state machine`, also known as a `finite automaton`, is a drastically simplified model of a computer that throws out all of these features in exchange for being easy to understand, easy to reason about, and easy to implement in hardware or software.

#### States, Rules, and Input
It’s a little machine with a handful of possible `states` and the ability to keep track of which one of those states it’s currently in—think of it as a computer with enough RAM to store a single value.

Instead of a general-purpose CPU for executing arbitrary programs, each finite automaton has a hardcoded collection of `rules` that determine how it should move from one state to another in response to input. The automaton starts in one particular state and reads individual characters from its `input` stream, following a rule each time it reads a character.

![](https://www.safaribooksonline.com/library/view/understanding-computation/9781449330071/httpatomoreillycomsourceoreillyimages1690690.png)

The two circles represent the automaton’s two states, 1 and 2, and the arrow coming from nowhere shows that the automaton always starts in state 1, its `start state`.

#### Output
![](https://www.safaribooksonline.com/library/view/understanding-computation/9781449330071/httpatomoreillycomsourceoreillyimages1690692.png)

These special states are usually called `accept states`, which suggests the idea of a machine accepting or rejecting certain sequences of inputs.

#### Determinism
Significantly, this kind of automaton is `deterministic`: whatever state it’s currently in, and whichever character it reads, it’s always absolutely certain which state it will end up in.

### Nondeterministic Finite Automata
#### Nondeterminism
![](https://www.safaribooksonline.com/library/view/understanding-computation/9781449330071/httpatomoreillycomsourceoreillyimages1690698.png)

This state machine, a `nondeterministic finite automaton (NFA)`, no longer has exactly one execution path for each sequence of inputs. When it’s in state 1 and reads b as input, it’s possible for it to follow a rule that keeps it in state 1, but it’s also possible for it to follow a different rule that takes it into state 2 instead.

A DFA’s next state is always completely determined by its current state and its input, but an NFA sometimes has more than one possibility for which state to move into next, and sometimes none at all.

#### Free Moves
These are rules that the machine may spontaneously follow without reading any input, and they help here because they give the NFA an initial choice between two separate groups of states:

![](https://www.safaribooksonline.com/library/view/understanding-computation/9781449330071/httpatomoreillycomsourceoreillyimages1690704.png.jpg)

The `free moves` are shown by the dotted unlabeled arrows from state 1 to states 2 and 4. This machine can still accept the string 'aaaa' by spontaneously moving into state 2, and then moving between states 2 and 3 as it reads the input, and likewise for 'aaaaaaaaa' if it begins with a free move into state 4. Now, though, there is no way for it to accept the string 'aaaaa': in any possible execution, it must begin by committing to a free move into either state 2 or state 4, and once it’s gone one way, there’s no route back again. Once it’s in state 2, it can only accept a string whose length is a multiple  2, and likewise once it’s in state 4, it can only accept a string whose length is a multiple of 3.

### Regular Expressions
`Regular expressions` provide a language for writing textual patterns against which strings may be matched.

As we’ll see, it’s possible to convert any regular expression into an equivalent NFA—every string matched by the regular expression is accepted by the NFA, and vice versa—and then match a string by feeding it to a simulation of that NFA to see whether it gets accepted.

### Equivalence
Well, it turns out that it’s possible to convert any nondeterministic finite automaton into a deterministic one that accepts exactly the same strings.

The only real difference between these two examples is that the DFA simulation moves from one current state to another, whereas the NFA simulation moves from **one current set of possible states** to another.

The DFA will have a state to represent    each set of possible states of the NFA, and the rules between these DFA states will correspond to the ways in which a deterministic simulation of the NFA can move between its sets of possible states.

Let’s try doing the conversion for a specific NFA. Take this one:

![](https://www.safaribooksonline.com/library/view/understanding-computation/9781449330071/httpatomoreillycomsourceoreillyimages1690722.png)

By thinking through the behavior of a simulation of the NFA, we’ve begun to construct a state machine for that simulation:

![](https://www.safaribooksonline.com/library/view/understanding-computation/9781449330071/httpatomoreillycomsourceoreillyimages1690724.png)

## Chapter 4. Just Add Power
### Deterministic Pushdown Automata
A finite state machine with a built-in stack is called a `pushdown automaton (PDA)`, and when that machine’s rules are deterministic, we call it a `deterministic pushdown automaton (DPDA)`.

Choosing a special character to mark the bottom of the stack—the dollar sign, `$`.It’s easy enough to rewrite the balanced-bracket DPDA’s rules in this format:

- When in state 1 and an opening bracket is read, pop the character `$`, push the characters `b$`, and move into state 2.
- When in state 2 and an opening bracket is read, pop the character b, push the characters bb, and stay in state 2.
- When in state 2 and a closing bracket is read, pop the character b, push no characters, and stay in state 2.
- When in state 2 (without reading any character), pop the character `$`, push the character `$`, and move into state 1.

![](https://www.safaribooksonline.com/library/view/understanding-computation/9781449330071/httpatomoreillycomsourceoreillyimages1690730.png)

### Nondeterministic Pushdown Automata
Unsurprisingly, a pushdown automaton without determinism constraints is called a `nondeterministic pushdown automaton`. Here’s one for recognizing palindromes with an even number of letters:

![](https://www.safaribooksonline.com/library/view/understanding-computation/9781449330071/httpatomoreillycomsourceoreillyimages1690738.png)

#### Nonequivalence
But wait: we saw in Equivalence that nondeterministic machines without a stack are exactly equivalent in power to deterministic ones.

The NFA-to-DFA trick only works because we can use a single DFA state to represent many possible NFA states. To simulate an NFA, we only need to keep track of what states it could currently be in, then pick a different set of possible states each time we read an input character, and a DFA can easily do that job if we give it the right rules.

But that trick doesn’t work for PDAs: we can’t usefully represent multiple NPDA configurations as a single DPDA configuration. The problem, unsurprisingly, is the stack. An NPDA simulation needs to know all the characters that could currently be on top of the stack, and it must be able to pop and push several of the simulated stacks simultaneously. There’s no way to combine all the possible stacks into a      single stack so that a DPDA can still see all the topmost characters and access every possible stack individually.

So unfortunately, our NPDA simulation does not behave like a DPDA, and there isn’t an NPDA-to-DPDA algorithm. The unmarked palindrome problem is an example of a job where an NPDA can do something that a DPDA can’t, so **nondeterministic pushdown automata really do have more power than deterministic ones**.

### Parsing with Pushdown Automata
A more traditional approach is to break the parsing process apart into two separate stages:

- `Lexical analysis`:Read a raw string of characters and turn it into a sequence of `tokens`. Each token represents an individual building block of program syntax, like “variable name,” “opening bracket,” or “while keyword.” A lexical analyzer uses a          language-specific set of rules called a `lexical grammar` to decide which sequences of characters should produce which tokens. This stage deals with messy character-level details like variable-naming rules, comments, and whitespace, leaving a clean sequence of tokens for the next stage to consume.
- `Syntactic analysis`:Read a sequence of tokens and decide whether they represent a valid program according to the `syntactic grammar` of the language being parsed. If the program is valid, the syntactic analyzer may produce additional information about its structure (e.g., a parse tree).

### How Much Power?
The main consequence of having a stack is the ability to recognize certain languages that finite automata aren’t capable of recognizing, like palindromes and strings of balanced brackets. The unlimited storage provided by a stack lets a PDA remember arbitrary amounts of information during a computation and refer back to it later.

## Chapter 5. The Ultimate Machine
### Deterministic Turing Machines
A finite state machine with access to an infinitely long tape is called a `Turing machine (TM)`. That name usually refers to a machine with deterministic rules, but we can also call it a `deterministic Turing machine (DTM)` to be completely unambiguous.

#### Rules
This unified rule format has five parts:

- The current state of the machine
- The character that must appear at the tape head’s current position
- The next state of the machine
- The character to write at the tape head’s current position
- The direction (left or right) in which to move the head after writing to the            tape

#### Determinism
A Turing machine’s next action is chosen according to its current state and the        character currently underneath its tape head, so a deterministic machine can only have one rule for each combination of state and character—the “no contradictions” rule—in order to prevent any ambiguity over what its next action will be.

### Nondeterministic Turing Machines
Just as with finite automata, a deterministic Turing machine can simulate a nondeterministic one. The simulation works by using the tape to store a queue of suitably encoded Turing machine configurations, each one containing a possible current state and tape of the simulated machine.

### Maximum Power
In fact, any attempt to upgrade the specification of Turing machines to make them more powerful is doomed to failure, because they’re already capable of simulating any potential enhancement.

- Internal Storage
- Subroutines
- Multiple Tapes
- Multidimensional Tape

### General-Purpose Machines
By reimplementing Tape, TMRule, DTMRulebook, and DTM as Turing machine rules, we are able to design a machine that can simulate any other DTM by reading its rules, accept states, and initial configuration from the tape and stepping through its execution, essentially acting as a Turing machine rulebook interpreter. A machine that does this is called a `universal Turing machine (UTM)`.

[1]: http://en.wikipedia.org/wiki/Fixed_point_(mathematics)
[2]: http://en.wikipedia.org/wiki/Monotonic_function
[3]:http://en.wikipedia.org/wiki/Partially_ordered_set