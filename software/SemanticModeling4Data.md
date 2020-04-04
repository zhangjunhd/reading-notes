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
    - [Mapping and Interlinking Relations](#mapping-and-interlinking-relations)
    - [Documentation Elements](#documentation-elements)
      - [Definitions and examples](#definitions-and-examples)
      - [Scope and Usage](#scope-and-usage)
      - [History and Provenance](#history-and-provenance)
- [3.Semantic and Linguistic Phenomena](#3semantic-and-linguistic-phenomena)
  - [Ambiguity](#ambiguity)
  - [Uncertainty](#uncertainty)
  - [Vagueness](#vagueness)
  - [Generality and Specificity](#generality-and-specificity)
  - [Symmetry, Inversion and Transitivity](#symmetry-inversion-and-transitivity)
  - [Closed and Open World Assumptions](#closed-and-open-world-assumptions)
  - [Semantic Change](#semantic-change)
- [4.Semantic Model Quality](#4semantic-model-quality)
  - [Semantic Accuracy](#semantic-accuracy)
  - [Completeness](#completeness)
  - [Consistency](#consistency)
  - [Conciseness](#conciseness)
  - [Timeliness](#timeliness)
  - [Relevancy](#relevancy)
  - [Understandability](#understandability)
  - [Trustworthiness](#trustworthiness)
  - [Availability, Versatility and Performance](#availability-versatility-and-performance)

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
If two modeling elements have semantically close meanings then their relation is characterized as “semantic relatedness”, “semantic similarity” or even “semantic distance”.

### Mapping and Interlinking Relations
OWL provides the relation “owl:sameAs” to denote that two individual entities between different models have the same meaning.

Also, for interlinking between classes, OWL offers the relation “owl:equivalentClass” which however has a big difference from “owl:sameAs”: the equivalence it expresses is extensional, i.e., two classes are equivalent if they always have the same instances.

SKOS, provides five different relations for the same purpose:

- “skos:exactMatch”: Given two entities in different models, it indicates a high degree of confidence that the two entities can be used interchangeably across a wide range of applications.
- “skos:closeMatch”: Given two entities in different models, indicates that the entities are sufficiently similar that they can be used interchangeably in some applications.
- “skos:broadMatch”: Given two entities in different models, it states that one entity’s meaning is broader than the other’s
- “skos:narrowMatch”: Given two entities in different models, it states that one entity’s meaning is narrower than the other’s.
- “skos:relatedMatch”: Given two entities in different models, it states that the two entities are semantically related, though not in a narrower or broader way.

### Documentation Elements
#### Definitions and examples
In general, natural language definitions come into four main flavours:

- `Extensional definitions` formulate an element’s meaning by specifying its extension, that is, every object that falls under its definition. For example, an extensional definition of the class “European Country” might be given by listing all of the countries that are located in Europe, or by giving some other means of recognizing the members of the corresponding class.
- `Intensional definition`s give the meaning of an element by specifying necessary and sufficient conditions for when the element should be used. For example, an intensional definition of the class “Bachelor” is “unmarried man”. This definition is valid because being an unmarried man is both a necessary condition and a sufficient condition for being a bachelor.
- `Definitions by genus and difference` give the meaning of an element by first stating the broad category it belongs to and then distinguishing it by specific properties. As an example consider the definition of “miniskirt” as “a skirt with a hemline above the knee”.
- `Ostensive definitions` give the meaning of an element by pointing out examples. This type of definition is often used where the term is difficult to define verbally, either because the words will not be understood (as with children and new speakers of a language) or because of the nature of the term (such as colors or sensations).

In RDF(S) and OWL, definitions and examples are usually expressed via the “rdfs:comment” attribute, while in SKOS there are dedicated elements for this purpose (“skos:definition” and skos:example”).

#### Scope and Usage
Cases when this may be needed include:

- The element may have other meanings which have been deliberately excluded from the model.
- The element may not be applicable in a particular context. For example, the profession of “Licence Plate Obscurer” exists only in Iran, so it makes no sense to have it as an entity in a model applied in the United States.
- The element (or even the whole model) may have been optimized for a particular task or application (e.g., for semantic search) that makes it less useful or even inappropriate for other tasks.

#### History and Provenance
Provenance elements are used to track the development of entities, relations and other modeling elements over time, by representing information about changes (who, when, what), versions, compatibility, etc.

# 3.Semantic and Linguistic Phenomena
## Ambiguity
`Ambiguity` is the situation that arises when a piece of information can be interpreted in more than one plausible ways.

In general, in human language and communication, we observe the following types of ambiguity:

- `Phonological ambiguity`: This ambiguity arises when there is more than one way to compose a set of sounds into words. For example, “ice cream” and “I scream” sound more or less the same.
- `Syntactic ambiguity`: This ambiguity arises when a sentence can have two or more different meanings because of its structure. For example, the sentence “John ate the cookies on the couch”, could mean either that there were some cookies on a couch and John ate them, or that John ate some cookies while sitting on a couch.
- `Anaphoric ambiguity`: This ambiguity arises when a phrase or word refers to something previously mentioned, but there is more than one possibility. For example, in the sentence “Margaret invited Susan for a visit, and she gave her a good lunch”, the pronoun “she” may refer to Margaret or Susan.
- `Term-level semantic ambiguity`: This ambiguity is also known as lexical ambiguity and arises when a term (single-word or compound) can have more than one meanings. For example, similarly to the aforementioned “Tripoli”, the term “Kashmir” may refer to the song by the band Led Zeppelin or to the geographical region in India and Pakistan.
- `Sentence-level semantic ambiguity`: This ambiguity arises when even after the syntax and the meanings of the individual words in a sentence have been resolved, the sentence can still be interpreted in more than one ways. For example, the sentence “John and Jane are married” can mean either that John and Jane are married to each other or that they are both married but to different people.

## Uncertainty
In a semantic model, uncertainty can be manifested in two ways, an `explicit` one and an `implicit`. Explicit uncertainty we have when the statement contains keywords like “probably”, “might”, “perhaps”, “apparently” etc., that clearly communicate the lack of absolute certainty.

The latter usually happens when we have legitimate reasons not to completely trust the source or the acquisition method of the statement.

## Vagueness
`Vagueness` is manifested through predicates that admit borderline cases [Hyde, 2008] [Shapiro, 2006], namely cases where **it is unclear whether or not the predicate applies**. For example, some people are borderline tall: not clearly tall and not clearly not tall. Alternatively, vagueness is related to **the absence of sharp boundaries**. For example, on a scale of heights, there appears to be no sharp boundary between the tall people and the rest. Therefore, two equivalent ways of drawing the distinction between vague and non-vague predicates are to say that (i) vague predicates can possibly have borderline cases while crisp predicates do not or that (ii) vague predicates lack sharp boundaries.

Table 3-1. Vague and Crisp Adjectives

Vague | Crisp
------|------
Abnormal: not normal, not typical or usual or regular or conforming to a norm. | Compound: composed of more than one part.
Impenitent: impervious to moral persuasion | Biweekly: occurring every two weeks.
Notorious: known widely and usually unfavorably. | Irregular: falling below the manufacturer’s standard.
Aroused: emotionally aroused. | Outermost: situated at the farthest possible.
Yellowish: of the color intermediate between green and orange in the color spectrum, of something resembling the color of an egg yolk. | Unfeathered: having no feathers.

In the relevant literature, two basic kinds of vagueness are identified: `degree-vagueness` (or quantitative) and `combinatory vagueness` (or qualitative) [Hyde, 2008]. A predicate has degree-vagueness if the existence of borderline cases stems from the lack (or at least the apparent lack) of precise boundaries between application and non-application of the predicate along some dimension. For example, “Bald” fails to draw any sharp boundaries along the dimension of hair quantity and “Tall” along the dimension of height. Of course it might be that a predicate has degree-vagueness in more than one dimensions (e.g., “Red” can be vague along the dimensions of brightness and saturation).

On the other hand, a predicate has combinatory vagueness if there is a variety of conditions all of which have something to do with the application of the predicate, yet it is not possible to make any sharp discrimination between those combinations which are sufficient and/or necessary for application and those which are not. A classical example of this type is “Religion” as there are certain features that all religions share (e.g., beliefs in supernatural beings, ritual acts etc.), yet it is not clear which of these features are able to classify something as a religion.

It is important that you don’t confuse `vagueness` with the phenomena of `inexactness`, `ambiguity` and `uncertainty`. 
- For example, stating that someone is between 170 and 180 cm is an inexact statement but it is not vague as its limits of application are precise. 
- Similarly, the truth of an uncertain statement, such as “Tomorrow the temperature might rise to 27 degrees”, cannot be determined due to lack of adequate information about it, not because the measurement of temperature lacks sharp boundaries. 
- Finally, the truth of a statement might not be determinable due to the ambiguity of some term (e.g., in statement “Yesterday we went to the bank” the term bank is ambiguous), yet again this does not make the statement vague.

Moreover, vagueness is `context dependent` as the interpretaton of a vague predicate may vary depending on the context it is being applied. For example, a person can be tall with respect to the average population height and not tall with respect to professional basketball players. Similarly, a person can be wealthy with respect to its local community but poor with respect to his/her boss.

Table 3-2. Vague and Non-Vague Relations in CiTO

Vague Relations | Crisp Relations
----------------|---------------
plagiarizes: A property indicating that the author of the citing entity plagiarizes the cited entity, by including textualor other elements from the cited entity without formal acknowledgement of their source | sharesAuthorInstitutionWith: he citing entity cites the cited entity as one that provides an authoritative description ordefinition of the subject under discussion.
citesAsAuthority: The citing entity cites the citedentity as one that provides an authoritative description ordefinition of the subject under discussion. | providesDataFor: The cited entity presents data that are usedin work described in the citing entity.
speculatesOn: The citing entity speculates onsomething within or related to the cited entity, without firmevidence. | retracts: The citing entity constitutes a formal retraction of the cited entity. 
supports: The citing entity provides intellectual orfactual support for statements, ideas or conclusions presented inthe cited entity. | includesExcerptFrom: The citing entityincludes one or more excerpts from the cited entity.
refutes: The citing entity refutes statements, ideasor conclusions presented in the cited entity. | citesAsSourceDocument: The citing entity cites the cited entity as being the entity from which the citing entity is derived, or about which the citing entity contains metadata.

## Generality and Specificity
`Generality` and `specificity` can be best understood when looking at a taxonomy of entities. For example, in the taxonomy of Figure 3-1, the concept of “Fruit” is more specific than the concept of “Food” but less specific than “Banana”. In other words, generality increases as we move up a taxonomy and decreases in the other direction, hence highly specific entities tend to be located in the low levels of a taxonomy. The inverse, however, is not always true; just because an entity is more general than another it doesn’t mean that it can be automatically be modeled as an ancestor of it in a taxonomy.

![](https://learning.oreilly.com/library/view/semantic-modeling-for/9781492054269/assets/FoodTaxonomy.png)

Figure 3-1. An example food taxonomy

A common mistake is to call an entity `ambiguous` just because it is very general. For example, if I tell you that I am an engineer then you will most likely ask me what kind of an engineer I am (e.g., a civil engineer or a software engineer). But even if I don’t give you that information, you will still get to know that I am “a person who uses scientific knowledge to solve practical problems”, as Wordnet suggests. In other words, highly general terms are not necessarily ambiguous.

## Symmetry, Inversion and Transitivity
- When an entity A is related to entity B via a `symmetric` relation R, then we can infer that B is related to A via the same relation. For example, if “John is a cousin of Jane”, then “Jane is also a cousin of John”. 
- When a relation R is `transitive` then if R links entity A to entity B, and entity B to entity C, then it also links A to C. For example, if “Paris is located in France” and “France is located in Europe”, then it’s also the case that “Paris is located in Europe”.
- We say that a relation R1 is the `inverse` of a relation R2 if for every entity A related to entity B through R1 we can infer that B is related to A via R2. For example, if “John is the brother of Jane” then “Jane is the sister of John”.

## Closed and Open World Assumptions
The `closed-world assumption` (CWA) states that if for a given statement we don’t know whether it’s true or not in our model, then we can infer that it’s false.

On the other hand, the `open-world assumption` (OWA) states that if for a given statement we don’t know whether it’s true or not in our model, then we simply cannot draw any conclusion about its validity.

## Semantic Change
Semantic change typically occurs due to linguistic, psychological and socio-cultural forces (see [Grzega, 2004] for a more detailed analysis) and, according to [Bloomfield, 1933] and [Blank, 1999], can take several forms:

- `Specialization`: The new meaning is narrower than the original one. For example “skyline” used to skyline refer to any horizon, but now in the United States it mostly denotes a horizon decorated by skyscrapers.
- `Generalization`: The new meaning is more general than the original one. A common example of that are are many specific brand names that end up being used for the general product or action, such as “hoover” for cleaning with a vacuum cleaner or “google” for searching in the web.
- `Metaphor`: Change based on similarity. For example, “broadcast” originally meant “to cast seeds out” but with the advent of radio and television it was extended to indicate the transmission of audio and video signals.
- `Metonymy`: Change based on contiguity between concepts (e.g., horn“animal horn” meaning “musical instrument”.
- `Synecdoche`: Change based on whole-part relation. The convention of using capital cities to represent countries or their governments is an example of this.
- `Hyperbole`: Change from weaker to stronger meaning (e.g., “torment” meaning “slaughter”)
- `Meiosis`: Change from stronger to weaker meaning (e.g., “strike with thunder” meaning “surprise strongly”).
- `Auto-antonymy`: Change of a word’s sense and concept to the complementary opposite (e.g., the word cleave can mean “to cut apart” or “to bind together”).
- `Folk-etymology`: Semantic change based on the similarity of names, e.g., the French term “contredanse” originates from the English “country dance”.
- `Antiphrasis`: Semantic change based on a contrastive aspect of the concepts (e.g., “perfect lady” in the sense of “prostitute”).

# 4.Semantic Model Quality
## Semantic Accuracy
Semantic accuracy is defined as the degree to which the semantic assertions of a model are accepted to be true. 

Now, there are several reasons why a semantic model may contain wrong assertions:

- Inaccuracy of automatic information extraction methods
- Inaccuracy of the data source from which assertions are extracted
- Misunderstanding of modeling elements’ semantics and intended usage
- Lack of domain knowledge and expertise
- Vagueness

The typical way to measure your model’s accuracy is to give a sample of its statements to one or more human judges and ask them to decide if they are true or false.

- The typical way to measure your model’s accuracy is to give a sample of its statements to one or more human judges and ask them to decide if they are true or false. 
- To accelerate this purely manual approach to measuring accuracy, researchers have developed methods for automatically detecting potential accuracy errors in semantic models. One group of such methods involves using statistical techniques to detect outliers, namely elements that due to low frequency, low inter-connectivity, or other characteristics, are likely to be wrong [Bizer, 2009] [Feeney, 2014] [Paulheim, 2014].
- A second group of methods uses reasoning to detect assertions that violate logical consinstency rules and axioms that we have already defined in the model [Nakashole, 2011] [Carlson, 2010] [Lehmann, 2010]. 

## Completeness
Completeness of a semantic model can be defined as the degree to which elements that should be contained in the model are indeed there.

In the relevant literature, a distinction is usually made between `schema completeness` and `population completeness`. The first refers to the degree to which the model defines all the necessary classes, relations, attributes and axioms, while the second implies the completeness of individual entities (class instances), relation assertions and attribute values.

Now, there are several reasons why a semantic model may be incomplete:

- Size and Complexity
- Inaccuracy of automatic information extraction methods
- Lack of appropriate data sources to extract the model from
- Vagueness
- Domain volatility and dynamics

To measure the completeness of a semantic model we practically need to compare the content it currently has with the content it should ideally have. In other words, we need a `gold standard` that can tell us at any given time how close we are at completing our model. In practice, gold standards are extremely hard to find (especially for population completeness), so instead we usually use `partial gold standards` or `silver standards`.

A partial gold standard contains a subset of the knowledge the model needs to contain. For example, in [Färber, 2017] the authors created a partial gold standard with 41 classes and 22 relations for 5 domains (People, Media, Organizations, Geography, and Biology) in order to measure and compare the completeness of DBpedia, YAGO and other publicly available semantic models. Similarly, at Textkernel, we used ESCO as a partial golden standard to get an idea of the coverage of our Knowledge Graph. Obviously, such an approach cannot tell you whether your model is complete but it can reveal incompletenesses.

A silver standard is also a subset of the knowledge the model needs to contain but, contrary to a gold standard, it’s (knowingly) not completely accurate. Instead, it is assumed to have a reasonable level of quality that can be useful for detecting incomplete aspects of the model. For example, in [Paulheim, 2013] the authors estimated that DBpedia misses at least 2.7 million entity typing statements, by comparing it to Yago, an also not fully accurate model.

Apart from using standards, completeness can also be evaluated by employing `reasoning` or simple heuristics.

## Consistency
Consistency means that a semantic model is free of logical or semantic contradictions.

## Conciseness
Conciseness in a semantic model is the degree to which the model does not contain redundant elements. 

Now, there are several reasons why a model can be inconcise:

- Uncoordinated modeling from multiple parties with inadequate governance
- Optimizing for different applications at the same time
- “Temporary” elements or hacks that haven’t been removed
- Legacy elements not having been removed

## Timeliness
Timeliness in a semantic model can be defined as the degree to which the model contains elements that reflect the current version of the world.

## Relevancy
A semantic model is relevant when its structure and content are useful and important for a given task or application. Vice versa, a model has low relevancy if, no matter how accurate or complete it looks to be with respect to our domain, we still cannot easily or effectively use it for the particular task(s) we need it.

## Understandability
Understandability or comprehensibility of a semantic model is the ease with which human consumers can understand and utilize the model’s elements, without misunderstanding or doubting their meaning.

## Trustworthiness
Trustworthiness of a semantic model refers to the perception and confidence in the quality of the model by its users. This (inevitably subjective) perception is definitely related to other quality dimensions like correctness, completeness or relevancy, yet you can have a model that is in reality less accurate than another and still being regarded as more trustworthy. The reason is that trust is not merely a technical concept but has social and psychological dimensions that cannot be easily expressed by a mathematical formula.

## Availability, Versatility and Performance
Availability is the extent and to which the model (or part of it) is present, obtainable and ready for use, while versatility refers to the different ways and forms the model can be accessed. DBpedia, for example, is continuously available online in multiple ways, including a SPARQL endpoint and a Triple Pattern Fragments interface. Similarly, ESCO is is available both as via a web service API and downloadable RDF files.

Performance, in turn, has to do with the efficiency and scalability with which we can access and use the model in our application (querying, reasoning or other operations). 























































































































































































































