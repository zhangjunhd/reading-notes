# Rule-based query answering method for a knowledge base of economic crimes

- [Rule-based query answering method for a knowledge base of economic crimes](#rule-based-query-answering-method-for-a-knowledge-base-of-economic-crimes)
  - [2.Preliminaries](#2preliminaries)
    - [2.1 Theoretical Background](#21-theoretical-background)
      - [2.1.1 First-order Logic](#211-first-order-logic)
        - [2.1.1.1 Syntax](#2111-syntax)
        - [2.1.1.2 Semantics](#2112-semantics)
      - [2.1.2 Datalog as a First-order Rule Language](#212-datalog-as-a-first-order-rule-language)
        - [2.1.2.1 Syntax](#2121-syntax)

## 2.Preliminaries
### 2.1 Theoretical Background
#### 2.1.1 First-order Logic
##### 2.1.1.1 Syntax
- Definition 2.1 (`Alphabet`). An alphabet of the first-order logic consists of the following symbols:
  - A set of constants: a, b, c, ...
  - A set of variables: ?x, ?y, ?z, ...
  - A set of function symbols: f, g, ..., where each function symbol has assigned arity (a natural number).
  - A set of predicate symbols: p,q,..., where each predicate symbol has as- signed arity (a natural number).
  - A set of logical connectives: ¬ (negation), ∧ (conjunction), ∨ (disjunction), → (implication) and ↔ (material equivalence).
  - Two quantifiers: ∃ (existential) and ∀ (universal).
  - A set of punctuation symbols: ‘(’, ‘)’ and ‘,’.

A symbol of arity 1 is called a unary symbol; a symbol of arity 2 is called a binary symbol; a symbol of arity n is called n-ary symbol. The arity of a symbol may be 0. Such symbols are constants.

- Definition 2.2 (`Term`). A term is defined as follows:
  1. A variable is a term.
  2. A constant is a term.
  3. If f is an n-ary function symbol with arity n and t1, t2, ..., tn are terms, then f(t1, t2, ..., tn) is a term.
- Definition 2.3 (`Ground term`). A term which does not contain any variables is called a ground term.
- Definition 2.4 (`Atom`). Let p be a predicate symbol with arity n. Let t1, t2, ..., tn be terms, then p(t1, t2, ..., tn) is an atom (or atomic formula). An atom which does not contain any variables is called a ground atom.
- Definition 2.5 (`Well-formed Formula`). A well formed formula (or just formula) is defined as follows:
  1. An atom is a formula.
  2. If B and H are formulae then:
      - ¬B is a formula
      - B∧H is a formula
      - B∨H is a formula
      - B→H is a formula
      - B≡H is a formula
  3. If B is a formula and x is a variable, then (∃xH) and (∀xH) are formulae.
- Definition 2.6 (Scope of Variables). If x is a variable and H is a formula then the scope of x in ∃xH and of ∀x in ∀xH is H. Combinations of ∃x and ∀x bind every occurrence of x in their scope. An occurrence of a variable which is not bound is called free.
- Definition 2.7 (Open and Closed Formula). A formula is open if it has free vari- ables. If a formula has no free variables then it is closed.
- Definition 2.8 (Literal). Let H be an atom. Then ¬H and H are called literals, whereas H is called positive literal, while ¬H is called negative literal.
- Definition 2.9 (`First-order Language`). A First-order language is defined over an alphabet and consists of the set of all well-formed formulae that can be constructed from the symbols of the alphabet. A FOL language is called function-free if it does not contain any function symbol (a set of functions symbols is an empty set).

##### 2.1.1.2 Semantics
Informally, the semantics of the first-order logic language is defined by attributing meaning (or truth values) to well-formed formulae (sentences). The sentences are mapped to some statements about a given domain through a process known as `interpretation`. If an interpretation gives the `true` value to a sentence then it is said to `satisfy` the sentence. Such an interpretation is called a `model` for the sentence.

- Definition 2.10 (`Interpretation`). An interpretation I consists of the following:
    1. A non-empty set $△^I$ called the universe of I or the domain of the interpretation. The members of $△^I$ are called individuals of I.
    2. An interpretation function $·^I$ , which assigns elements of the alphabet to $△^I$ satisfying the following conditions:
        - Each constant c is mapped to an element $c^I \in △^I$
        - Each function symbol f of arity n is mapped to a function: 
          - $$f^I :(△^I)^n \to △^I$$
        - Each predicate symbol p of arity n is mapped to a function: 
          - $$p^I :(△^I)^n \to \{true,false\}$$
- Definition 2.11 (`Assignment`).
    1. Variable Assignment. A variable assignment is a mapping function σ, which assigns an element $c \in △^I$ to every variable x from a set of variables $\bar{X}$:
       - $σ : \bar{X} \to △^I$
    1. Term Assignment. The term assignment w.r.t. σ of the term $t \in △^I$ is defined as:
        - Each variable assignment is given according to σ,
        - Each constant assignment is given according to I,
        - If $t^′_1, t^′_2, ..., t^′_n$ are term assignments of $t_1, t_2, ..., t_n$ and $f^′$ is the assignment of the function symbol f with arity n according to I, then $f^′(t^′_1,t^′_2,...,t^′_n) \in △^I$ is the term assignment of $f(t_1,t_2,...,t_n)$.










#### 2.1.2 Datalog as a First-order Rule Language
Characteristic of Datalog as a rule language is a feature called `recursion` which allows the result of a rule can to be used as one of the rule’s premises. Datalog uses the `closed world semantics` which also occurs in relational databases. It means that facts that cannot be proven are considered false.

##### 2.1.2.1 Syntax


