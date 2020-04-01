![cover](https://img1.doubanio.com/view/subject/s/public/s33606827.jpg)

    作者: Panos Alexopoulos
    出版社: O'Reilly Media, Inc.
    副标题: Avoiding Pitfalls and Breaking Dilemmas
    出版年: 2020-11-17
    页数: 355
    定价: USD 49.99
    装帧: Paperback
    ISBN: 9781492054252

- [豆瓣链接](https://book.douban.com/subject/34973915/)
- [oreilly](https://learning.oreilly.com/library/view/semantic-modeling-for/9781492054269/ch02.html)

---

- [2.Semantic Modeling Elements](#2semantic-modeling-elements)
  - [General Elements](#general-elements)
    - [Entities](#entities)
    - [Relations](#relations)
    - [Classes](#classes)
    - [Attributes](#attributes)
    - [Complex Axioms, Restrictions and Rules](#complex-axioms-restrictions-and-rules)
    - [Terms](#terms)
  - [Common Specific Elements](#common-specific-elements)
    - [Lexicalization and Synonymy](#lexicalization-and-synonymy)
    - [Instantiation](#instantiation)
    - [Meaning inclusion and class subsumption](#meaning-inclusion-and-class-subsumption)
    - [Part-Whole relations](#part-whole-relations)
    - [Semantic Relatedness](#semantic-relatedness)

# 2.Semantic Modeling Elements
## General Elements
### Entities
Without being too philosophical, an `entity` is something that may exist concretely or abstractly, outside or within our mind.

-  An entity is `concrete` when it has a physical manifestation by which it can be sensed and identified. A particular person, organization, document or event are all examples of concrete entities. In philosophy and metaphysics concrete entities are known as `particulars` and their key characteristic is that they can exist over time but they can only be in one place at a time, i.e., they are “non-repeatable” entities. Linguistically, concrete entities are described via proper nouns.
-  An `abstract` entity, on the other hand, does not exist on a particular time or place but rather as an idea, category or concept.

Table 2-1. Concrete and Abstract Entities

Concrete | Abstract
---------|---------
Stairway to Heaven | Rock Music
The 2018 Champions League Final Game | Football
Barack Obama | Politician
C++ | Object-oriented programming
The Iliad | Poem
Empire State Building | Architecture
Socrates’s Trial | Justice
Volkswagen AG | Car Manufacturing

An entity is a first-class citizen in a `semantic model` and should be unique and unambiguous within it. The same entity may have multiple names, and the same name may refer to multiple entities, yet an entity’s meaning is unique. This is what the **“Things not Strings”** slogan of Google’s Knowledge Graph is all about, namely that the search engine can actually interpret the meaning behind keywords.

### Relations
A `relation` expresses a particular way two or more entities can be related to one another.

Terminology-wise, things can get pretty confusing when talking about relations.

- If you have worked with Relational Databases you will know that the term “relation” is equivalent to a set of tuples (or table).
- If you are a Semantic Web expert, you will know that in RDF(S) relations are called “properties”, and in OWL “object properties”.
- In Description Logics, relations are known as “Roles”.

### Classes
`Classes` are abstract entities that may serve as semantic types of other entities, concrete or abstract. For example, the entity “Song” can be used as a type of the entity “Stairway to Heaven”.

**The only criterion that matters when determining if an abstract entity can be a class is whether there are other entities that can be instances of it**. If you can’t find any (convincing) instances, then it’s pretty likely that it’s not a class. Table 2-2 juxtaposes abstract entities for which I am personally certain that can be classes, and entities for which I have a hard time finding instances.

Table 2-2. Clear and doubtful class entities:

Clear classes | Doubtful classes
--------------|-----------------
Supreme Court | Judge Justice
Song | Music
Football Game | Football
Politician | Communism
Marketing Software | Advertising
Programming Language | Machine Learning

### Attributes
An `entity` attribute is used to represent a characteristic of an entity that we cannot (or choose not to) represent as a relation with another entity, and instead we use literal values (i.e., numbers, strings, dates etc.). We usually use an attribute to represent:

- Characteristics with values that don’t make much sense as distinct entities (e.g., age, height, weight, salary, etc).
- Characteristics not really related to the domain but useful for administration or other purposes (e.g., the person who added the entity in the model or the method used for its discovery).

In RDF(S) entity attributes are called “properties” (so there is no distinction between them and relations!) and in OWL “datatype properties”.

In some modeling frameworks and languages, like E-R models and property graphs, the definition of relation attributes is directly supported, whereas in others, like RDF and OWL, you can only do it in an indirect way.

### Complex Axioms, Restrictions and Rules
`Reasoning`, namely the derivation of facts that are not explicitly expressed in the model.

For example, in both Entity-Relationship and OWL models, we can define cardinality restrictions about relations, namely the minimum and maximum number of objects and subjects they can have (e.g., the relation “wasBornIn” can link an entity of type “Person” to exactly one entity of type “Location”). Also in OWL, we are able to define a class by specifying the range of the relation objects of another class (e.g., we can define the class “Parent” as the set of entities that are instances of the class “Person” and are related to at least one other instance of the same class via the relation “hasChild”). And if we use the Semantic Web Rule Language (SWRL)  we can define a rule that says that if a person A is the parent of person B, and person C is the brother of person A, then C is the uncle of B.

### Terms
A `term` is a string of characters (word or phrase) that can be used to lexically describe an entity, a relation, an attribute or any other modeling element.

## Common Specific Elements
### Lexicalization and Synonymy
A `lexicalization` relation relates an element (entity, relation, attribute etc.) to one or more terms that can be used to express it in natural language. These terms are practically either `synonyms` or `lexical variants` to each other.

Two terms are `synonyms` when their meanings are regarded as the same or nearly the same in a wide range of contexts.

Table 2-4. Types of Synonyms

Type | Examples
-----|---------
Synonyms of different linguistic origin | cats / felines, freedom / liberty, sodium / natrium, sweat / perspiration.
Popular and scientific name synonyms | aspirin / acetylsalicylic acid, gulls / Laridae, salt / sodium chloride
Generic and trade name synonyms | petroleum jelly / Vaseline, photocopies / Xeroxes, refrigerators / Frigidaires, tissues / Kleenex
Variant names for emergent concepts | hovercraft / air cushion vehicle
Current or favored terms replacing outdated or deprecated terms | poliomyelitis / infantile paralysis, developing countries / underdeveloped countries
Slang or jargon synonyms | helicopters / whirlybirds, psychiatrists / shrinks
Dialectical variants | elevators / lifts, subways / undergrounds

Table 2-5. Types of Lexical Variants in English

Type | Examples
-----|---------
Direct v.s. inverted order | radar antennas / antennas, radar
Orthographic variants | Romania / Rumania / Roumania, ground water / ground-water / groundwater
Stem variants | pediatrics / paediatrics
Irregular plurals | mice / mouse
Full name and abbreviation variants | International Federation for Documentation / FID, pi mesons / pions, polyvinyl chloride / PVC

- In RDF(S) and OWL, lexicalization is facilitated via the “rdfs:label” relation that relates a modeling element with a string-language pair called lexical label.
- In SKOS, the modeler is able to make a distinction between the “preferred”, “alternative” and “hidden” lexical labels for any given element.
- In Wordnet, the words belonging to a synset are found using the “lemma” relation whereas in the worlds of (non-SKOS) taxonomies, thesauri and controlled vocabularies (see the ANSI/NISO Z39-19 or ISO 25964 standards) terms with the same meaning are designated as “preferred terms” and “non-preferred terms”. The former are also called “descriptors” and the latter “alternate descriptors”.

### Instantiation
The `instantiation` relation relates an entity to one or more classes it is an instance of.

- In RDF(S) and OWL, this relation is known as “rdf:type”. 
- In taxonomie, instantiation is just another hierarchical relation, indicated by the abbreviation BTI (standing for “Broader term (instance)”) or NTI (standing for “Narrower term (instance)”).

### Meaning inclusion and class subsumption
A `meaning inclusion` relation between two modeling elements (entity, relation or attribute) indicates that the meaning of the one is included in the meaning of the other. For example, the meaning of the entity “screwdriver” is included in that of “tool” in the sense that a screwdriver is a specific kind of tool. In Linguistics, the meaning inclusion relation is known as `hyponymy`/`hypernymy` where hypernym is the more generic element and hyponym the more specific.

When the meaning inclusion is applied to classes, then it is also called `“class subsumption”` or `“subclassing”` and has the following logical implication: If class A a subclass of class B then all entities that instantiate A are also instances of B. Thus, for example, if we say that “Football Game” is a subclass of “Sports Event” then a reasoner will infer that the 2019 Champions League Final is also an instance of “Sports Event”. Similarly if the meaning inclusion is about relations, or attributes then it has the logical implication that if relation A is subsumed by relation B then all entities related via A are also related via B.

- Class and relation subsumption are typically found in ontology languages like RDF(S) and OWL where are known as “rdfs:subClassOf” and “rdfs:subPropertyOf” respectively.

### Part-Whole relations
- `Component-Integral Object`: This relation models the relation between components and the objects they belong to. For example, “A brain is part of a human”, “A wheel is part of a car”, “A handle is part of a cup”, etc.
- `Member-Collection`: This relation is similar to the the component-integral relation but with the difference that the parts are not required to perform a particular function or possess a particular position with respect to each other and to their wholes. For example, “A person is part of a crowd”, “A judge is part of a judgement committee”, etc.
- `Portion-Mass`: This parthood relation applies when the parts and the whole are similar to each other and to the whole which they comprise. For example, “An ice-cream scoop is part of an ice-cream”, “A meter is part of a kilometer”, etc.
- `Stuff-Object`: This is a relation that is most often expressed using the “is partly” expression. For example, “This building is partly steel”, “Table salt is partly Natrium”, etc.
- `Feature-Activity`: This is a relation that designates the features or phases of activities and processes. For example, “Testing is part of Software Development”, “Thesis writing is part of getting a PhD”, etc.
- `Place-Area`: This is the relation between areas and places or locations within them. For example, “Yosemite National Park is part of California”, “Manhattan is part of New York City”, etc.

### Semantic Relatedness























