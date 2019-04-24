https://www.w3.org/TR/json-ld/

<!-- TOC -->

- [Terminology](#terminology)
  - [Data Model Overview](#data-model-overview)
  - [Syntax Tokens and Keywords](#syntax-tokens-and-keywords)
- [Basic Concepts](#basic-concepts)
  - [The Context](#the-context)
  - [IRIs](#iris)
  - [Node Identifiers](#node-identifiers)
  - [Specifying the Type](#specifying-the-type)
- [Advanced Concepts](#advanced-concepts)
  - [Base IRI](#base-iri)
  - [Default Vocabulary](#default-vocabulary)
  - [Compact IRIs](#compact-iris)
  - [Typed Values](#typed-values)
  - [Type Coercion](#type-coercion)
  - [Embedding](#embedding)
  - [Advanced Context Usage](#advanced-context-usage)
  - [String Internationalization](#string-internationalization)
  - [IRI Expansion within a Context](#iri-expansion-within-a-context)
  - [Sets and Lists](#sets-and-lists)
  - [Reverse Properties](#reverse-properties)
  - [Named Graphs](#named-graphs)
  - [Identifying Blank Nodes](#identifying-blank-nodes)
  - [Aliasing Keywords](#aliasing-keywords)
  - [Expanded Document Form](#expanded-document-form)
  - [Compacted Document Form](#compacted-document-form)
  - [Flattened Document Form](#flattened-document-form)

<!-- /TOC -->

## Terminology
### Data Model Overview
- A `JSON-LD document` serializes a [generalized RDF Dataset][1] [[RDF11-CONCEPTS][2]], which is a collection of [graphs][14] that comprises exactly one [default graph][16] and zero or more [named graphs][17].
- The `default graph` does not have a name and may be empty.
- Each `named graph` is a pair consisting of an IRI or blank node identifier (the graph name) and a graph. Whenever practical, the graph name should be an IRI.
- A `graph` is a labeled directed graph, i.e., a set of nodes connected by edges.
- Every `edge` has a direction associated with it and is labeled with an IRI or a blank node identifier. Within the JSON-LD syntax these edge labels are called `properties`. Whenever practical, an edge should be labeled with an IRI.
- Every `node` is an IRI, a blank node, a JSON-LD value, or a list.
- A node having an outgoing edge must be an IRI or a blank node.
- A graph must not contain unconnected nodes, i.e., nodes which are not connected by an edge to any other node.
- An `IRI` (Internationalized Resource Identifier) is a string that conforms to the syntax defined in [[RFC3987][3]]. IRIs used within a graph should return a Linked Data document describing the resource denoted by that IRI when being dereferenced.
- A `blank node` is a node which is neither an IRI, nor a JSON-LD value, nor a list. A blank node may be identified using a blank node identifier.
- A `blank node identifier` is a string that can be used as an identifier for a blank node within the scope of a JSON-LD document. Blank node identifiers begin with _:.
- A `JSON-LD value` is a typed value, a string (which is interpreted as typed value with type _xsd:string_), a number (numbers with a non-zero fractional part, i.e., the result of a modulo‑1 operation, are interpreted as typed values with type _xsd:double_, all other numbers are interpreted as typed values with type _xsd:integer_), true or false (which are interpreted as typed values with type _xsd:boolean_), or a language-tagged string.
- A `typed value` consists of a value, which is a string, and a type, which is an IRI.
- A `language-tagged string` consists of a string and a non-empty language tag as defined by [[BCP47][4]]. The language tag must be well-formed according to section [2.2.9 Classes of Conformance][5] of [[BCP47][4]].
- A `list` is a sequence of zero or more IRIs, blank nodes, and JSON-LD values. Lists are interpreted as RDF list structures [[RDF11-MT][6]].

![1](https://www.w3.org/TR/json-ld/linked-data-graph.png)

Figure 1: An illustration of the data model.

### Syntax Tokens and Keywords
- `@context`: Used to define the short-hand names that are used throughout a JSON-LD document. These short-hand names are called [terms][7] and help developers to express specific identifiers in a compact manner.
- `@id`: Used to uniquely identify _things_ that are being described in the document with [IRIs][8] or [blank node identifiers][9].
- `@value`: Used to specify the data that is associated with a particular [property][10] in the graph.
- `@language`: Used to specify the language for a particular string value or the default language of a JSON-LD document.
- `@type`: Used to set the data type of a [node][11] or [typed value][12]. 
- `@container`: Used to set the default container type for a [terms][7].
- `@list`: Used to express an ordered set of data.
- `@set`: Used to express an unordered set of data and to ensure that values are always represented as arrays. 
- `@reverse`: Used to express reverse properties.
- `@index`: Used to specify that a container is used to index information and that processing should continue deeper into a JSON data structure.
- `@base`: Used to set the base [IRIs][8] against which [relative IRIs][13] are resolved.
- `@vocab`: Used to expand properties and values in `@type` with a common prefix IRI.
- `@graph`: Used to express a [graph][14].
- `:`: The separator for JSON keys and values that use [compact IRIs][15].

## Basic Concepts
EXAMPLE 1: Sample JSON document

```json
{
  "name": "Manu Sporny",
  "homepage": "http://manu.sporny.org/",
  "image": "http://manu.sporny.org/images/manu.png"
}
```

EXAMPLE 2: Sample JSON-LD document using full IRIs instead of terms

```json
{
  "http://schema.org/name": "Manu Sporny",
  "http://schema.org/url": { "@id": "http://manu.sporny.org/" },  ← The '@id' keyword means 'This value is an identifier that is an IRI'
  "http://schema.org/image": { "@id": "http://manu.sporny.org/images/manu.png" }
}
```

### The Context
Simply speaking, a `context` is used to map terms to IRIs. Terms are case sensitive and any valid string that is not a reserved JSON-LD keyword can be used as a term.

EXAMPLE 3: Context for the sample document in the previous section

```json
{
  "@context":
  {
    "name": "http://schema.org/name",  ← This means that 'name' is shorthand for 'http://schema.org/name' 
    "image": {
      "@id": "http://schema.org/image",  ← This means that 'image' is shorthand for 'http://schema.org/image' 
      "@type": "@id"  ← This means that a string value associated with 'image' should be interpreted as an identifier that is an IRI 
    },
    "homepage": {
      "@id": "http://schema.org/url",  ← This means that 'homepage' is shorthand for 'http://schema.org/url' 
      "@type": "@id"  ← This means that a string value associated with 'homepage' should be interpreted as an identifier that is an IRI 
    }
  }
}
```

EXAMPLE 4: Referencing a JSON-LD context

```json
{
  "@context": "http://json-ld.org/contexts/person.jsonld",
  "name": "Manu Sporny",
  "homepage": "http://manu.sporny.org/",
  "image": "http://manu.sporny.org/images/manu.png"
}
```

EXAMPLE 5: In-line context definition

```json
{
  "@context":
  {
    "name": "http://schema.org/name",
    "image": {
      "@id": "http://schema.org/image",
      "@type": "@id"
    },
    "homepage": {
      "@id": "http://schema.org/url",
      "@type": "@id"
    }
  },
  "name": "Manu Sporny",
  "homepage": "http://manu.sporny.org/",
  "image": "http://manu.sporny.org/images/manu.png"
}
```

### IRIs
EXAMPLE 6: Values of @id are interpreted as IRI

```json
{
...
  "homepage": { "@id": "http://example.com/" }
...
}
```

EXAMPLE 7: IRIs can be relative

```json
{
...
  "homepage": { "@id": "../" }
...
}
```

EXAMPLE 8: IRI as a key

```json
{
...
  "http://schema.org/name": "Manu Sporny",
...
}
```

EXAMPLE 9: Term expansion from context definition

```json
{
  "@context":
  {
    "name": "http://schema.org/name"
  },
  "name": "Manu Sporny",
  "status": "trollin'"
}
```

JSON keys that do not expand to an IRI, such as status in the example above, are not Linked Data and thus ignored when processed.

If type coercion rules are specified in the @context for a particular term or property IRI, an IRI is generated:

EXAMPLE 10: Type coercion

```json
{
  "@context":
  {
    ...
    "homepage":
    {
      "@id": "http://schema.org/url",
      "@type": "@id"
    }
    ...
  }
...
  "homepage": "http://manu.sporny.org/",
...
}
```

### Node Identifiers
In JSON-LD, a node is identified using the @id keyword:

EXAMPLE 11: Identifying a node

```json
{
  "@context":
  {
    ...
    "name": "http://schema.org/name"
  },
  "@id": "http://me.markus-lanthaler.com/",
  "name": "Markus Lanthaler",
  ...
}
```

### Specifying the Type
The type of a particular node can be specified using the @type keyword. 

EXAMPLE 12: Specifying the type for a node

```json
{
...
  "@id": "http://example.org/places#BrewEats",
  "@type": "http://schema.org/Restaurant",
...
}
```

EXAMPLE 13: Specifying multiple types for a node

```json
{
...
  "@id": "http://example.org/places#BrewEats",
  "@type": [ "http://schema.org/Restaurant", "http://schema.org/Brewery" ],
...
}
```

EXAMPLE 14: Using a term to specify the type

```json
{
  "@context": {
    ...
    "Restaurant": "http://schema.org/Restaurant", 
    "Brewery": "http://schema.org/Brewery"
  }
  "@id": "http://example.org/places#BrewEats",
  "@type": [ "Restaurant", "Brewery" ],
  ...
}
```

## Advanced Concepts
### Base IRI
EXAMPLE 15: Use a relative IRI as node identifier

```json
{
  "@context": {
    "label": "http://www.w3.org/2000/01/rdf-schema#label"
  },
  "@id": "",
  "label": "Just a simple document"
}
```

This document uses an empty @id, which resolves to the document base. However, if the document is moved to a different location, the IRI would change. To prevent this without having to use an absolute IRI, a context may define an @base mapping, to overwrite the base IRI for the document.

EXAMPLE 16: Setting the document base in a document

```json
{
  "@context": {
    "@base": "http://example.com/document.jsonld"
  },
  "@id": "",
  "label": "Just a simple document"
}
```

### Default Vocabulary
EXAMPLE 17: Using a common vocabulary prefix

```json
{
  "@context": {
    "@vocab": "http://schema.org/"
  }
  "@id": "http://example.org/places#BrewEats",
  "@type": "Restaurant",
  "name": "Brew Eats"
  ...
}
```

If @vocab is used but certain keys in an object should not be expanded using the vocabulary IRI, a term can be explicitly set to null in the context. 

EXAMPLE 18: Using the null keyword to ignore data

```json
{
  "@context":
  {
     "@vocab": "http://schema.org/",
     "databaseId": null
  },
    "@id": "http://example.org/places#BrewEats",
    "@type": "Restaurant",
    "name": "Brew Eats",
    "databaseId": "23987520"
}
```

### Compact IRIs
EXAMPLE 19: Prefix expansion

```json
{
  "@context":
  {
    "foaf": "http://xmlns.com/foaf/0.1/"
...
  },
  "@type": "foaf:Person"
  "foaf:name": "Dave Longley",
...
}
```

In the example above, foaf:name expands to the IRI http://xmlns.com/foaf/0.1/name and foaf:Person expands to http://xmlns.com/foaf/0.1/Person.

EXAMPLE 20: Using vocabularies

```json
{
  "@context":
  {
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "foaf": "http://xmlns.com/foaf/0.1/",
    "foaf:homepage": { "@type": "@id" },
    "picture": { "@id": "foaf:depiction", "@type": "@id" }
  },
  "@id": "http://me.markus-lanthaler.com/",
  "@type": "foaf:Person",
  "foaf:name": "Markus Lanthaler",
  "foaf:homepage": "http://www.markus-lanthaler.com/",
  "picture": "http://twitter.com/account/profile_image/markuslanthaler"
}
```

### Typed Values
The first example uses the @type keyword to associate a type with a particular term in the @context:

EXAMPLE 21: Expanded term definition with type coercion

```json
{
  "@context":
  {
    "modified":
    {
      "@id": "http://purl.org/dc/terms/modified",
      "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
    }
  },
...
  "@id": "http://example.com/docs/1",
  "modified": "2010-05-29T14:17:39+02:00",
...
}
```

Subject | Property | Value | Value Type
--------|----------|-------|-----------
http://example.com/docs/1 | http://purl.org/dc/terms/modified | 2010-05-29T14:17:39+02:00 | http://www.w3.org/2001/XMLSchema#dateTime

The second example uses the expanded form of setting the type information in the body of a JSON-LD document:

EXAMPLE 22: Expanded value with type

```json
{
  "@context":
  {
    "modified":
    {
      "@id": "http://purl.org/dc/terms/modified"
    }
  },
...
  "modified":
  {
    "@value": "2010-05-29T14:17:39+02:00",
    "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  }
...
}
```

A `node type` specifies the type of thing that is being described, like a person, place, event, or web page. A `value type` specifies the data type of a particular value, such as an integer, a floating point number, or a date.

EXAMPLE 23: Example demonstrating the context-sensitivity for @type

```json
{
...
  "@id": "http://example.org/posts#TripToWestVirginia",
  "@type": "http://schema.org/BlogPosting",  ← This is a node type
  "modified":
  {
    "@value": "2010-05-29T14:17:39+02:00",
    "@type": "http://www.w3.org/2001/XMLSchema#dateTime"  ← This is a value type
  }
...
}
```

Subject | Property | Value | Value Type
--------|----------|-------|-----------
http://example.org/posts#TripToWestVirginia | http://www.w3.org/1999/02/22-rdf-syntax-ns#type | http://schema.org/BlogPosting | -
http://example.org/posts#TripToWestVirginia | http://purl.org/dc/terms/modified | 2010-05-29T14:17:39+02:00 | http://www.w3.org/2001/XMLSchema#dateTime

### Type Coercion
Type coercion allows someone deploying JSON-LD to coerce the incoming or outgoing values to the proper data type based on a mapping of data type IRIs to terms. 

EXAMPLE 24: Expanded term definition with types

```json
{
  "@context":
  {
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "name": "http://xmlns.com/foaf/0.1/name",
    "age":
    {
      "@id": "http://xmlns.com/foaf/0.1/age",
      "@type": "xsd:integer"
    },
    "homepage":
    {
      "@id": "http://xmlns.com/foaf/0.1/homepage",
      "@type": "@id"
    }
  },
  "@id": "http://example.com/people#john",
  "name": "John Smith",
  "age": "41",
  "homepage":
  [
    "http://personal.example.org/",
    "http://work.example.com/jsmith/"
  ]
}
```

Subject | Property | Value | Value Type
--------|----------|-------|-----------
http://example.com/people#john | http://xmlns.com/foaf/0.1/name | John Smith |  
http://example.com/people#john | http://xmlns.com/foaf/0.1/age | 41 | http://www.w3.org/2001/XMLSchema#integer
http://example.com/people#john | http://xmlns.com/foaf/0.1/homepage | http://personal.example.org/,http://work.example.com/jsmith/ | IRI

Terms may also be defined using absolute IRIs or compact IRIs. 

EXAMPLE 25: Term definitions using compact and absolute IRIs

```json
{
  "@context":
  {
    "foaf": "http://xmlns.com/foaf/0.1/",
    "foaf:age":
    {
      "@id": "http://xmlns.com/foaf/0.1/age",
      "@type": "xsd:integer"
    },
    "http://xmlns.com/foaf/0.1/homepage":
    {
      "@type": "@id"
    }
  },
  "foaf:name": "John Smith",
  "foaf:age": "41",
  "http://xmlns.com/foaf/0.1/homepage":
  [
    "http://personal.example.org/",
    "http://work.example.com/jsmith/"
  ]
}
```

### Embedding
Embedding is a JSON-LD feature that allows an author to use node objects as property values. This is a commonly used mechanism for creating a parent-child relationship between two nodes.

EXAMPLE 26: Embedding a node object as property value of another node object

```json
{
...
  "name": "Manu Sporny",
  "knows":
  {
    "@type": "Person",
    "name": "Gregg Kellogg",
  }
...
}
```

### Advanced Context Usage
EXAMPLE 27: Using multiple contexts

```json
[
  {
    "@context": "http://example.org/contexts/person.jsonld",
    "name": "Manu Sporny",
    "homepage": "http://manu.sporny.org/",
    "depiction": "http://twitter.com/account/profile_image/manusporny"
  },
  {
    "@context": "http://example.org/contexts/place.jsonld",
    "name": "The Empire State Building",
    "description": "The Empire State Building is a 102-story landmark in New York City.",
    "geo": {
      "latitude": "40.75",
      "longitude": "73.98"
    }
  }
]
```

Duplicate context terms are overridden using a most-recently-defined-wins mechanism.

EXAMPLE 28: Scoped contexts within node objects

```json
{
  "@context":
  {
    "name": "http://example.com/person#name,
    "details": "http://example.com/person#details"
  }",
  "name": "Markus Lanthaler",
  ...
  "details":
  {
    "@context":
    {
      "name": "http://example.com/organization#name"
    },
    "name": "Graz University of Technology"
  }
}
```

EXAMPLE 29: Combining external and local contexts

```json
{
  "@context": [
    "http://json-ld.org/contexts/person.jsonld",
    {
      "pic": "http://xmlns.com/foaf/0.1/depiction"
    }
  ],
  "name": "Manu Sporny",
  "homepage": "http://manu.sporny.org/",
  "pic": "http://twitter.com/account/profile_image/manusporny"
}
```

### String Internationalization
First, it is possible to define a default language for a JSON-LD document by setting the @language key in the context:

EXAMPLE 31: Setting the default language of a JSON-LD document

```json
{
  "@context":
  {
    ...
    "@language": "ja"
  },
  "name": "花澄",
  "occupation": "科学者"
}
```

The example above would associate the ja language code with the two strings 花澄 and 科学者. Languages codes are defined in [[BCP47][4]]. The default language applies to all string values that are not type coerced.

To clear the default language for a subtree, @language can be set to null in a local context as follows:

EXAMPLE 32: Clearing default language

```json
{
  "@context": {
    ...
    "@language": "ja"
  },
  "name": "花澄",
  "details": {
    "@context": {
      "@language": null
    },
    "occupation": "Ninja"
  }
}
```

Second, it is possible to associate a language with a specific term using an expanded term definition:

EXAMPLE 33: Expanded term definition with language

```json
{
  "@context": {
    ...
    "ex": "http://example.com/vocab/",
    "@language": "ja",
    "name": { "@id": "ex:name", "@language": null },
    "occupation": { "@id": "ex:occupation" },
    "occupation_en": { "@id": "ex:occupation", "@language": "en" },
    "occupation_cs": { "@id": "ex:occupation", "@language": "cs" }
  },
  "name": "Yagyū Muneyoshi",
  "occupation": "忍者",
  "occupation_en": "Ninja",
  "occupation_cs": "Nindža",
  ...
}
```

EXAMPLE 34: Language map expressing a property in three languages

```json
{
  "@context":
  {
    ...
    "occupation": { "@id": "ex:occupation", "@container": "@language" }
  },
  "name": "Yagyū Muneyoshi",
  "occupation":
  {
    "ja": "忍者",
    "en": "Ninja",
    "cs": "Nindža"
  }
  ...
}
```

Third, it is possible to override the default language by using a value object:

EXAMPLE 35: Overriding default language using an expanded value

```json
{
  "@context": {
    ...
    "@language": "ja"
  },
  "name": "花澄",
  "occupation": {
    "@value": "Scientist",
    "@language": "en"
  }
}
```

This makes it possible to specify a plain string by omitting the @language tag or setting it to null when expressing it using a value object:

```json
{
  "@context": {
    ...
    "@language": "ja"
  },
  "name": {
    "@value": "Frank"
  },
  "occupation": {
    "@value": "Ninja",
    "@language": "en"
  },
  "speciality": "手裏剣"
}
```

### IRI Expansion within a Context
It is common to use the xsd namespace when defining typed values:

EXAMPLE 37: IRI expansion within a context

```json
{
  "@context":
  {
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "name": "http://xmlns.com/foaf/0.1/name",
    "age":
    {
      "@id": "http://xmlns.com/foaf/0.1/age",
      "@type": "xsd:integer"
    },
    "homepage":
    {
      "@id": "http://xmlns.com/foaf/0.1/homepage",
      "@type": "@id"
    }
  },
  ...
}
```

Terms may also be used when defining the IRI of another term:

EXAMPLE 38: Using a term to define the IRI of another term within a context

```json
{
  "@context":
  {
    "foaf": "http://xmlns.com/foaf/0.1/",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "name": "foaf:name",
    "age":
    {
      "@id": "foaf:age",
      "@type": "xsd:integer"
    },
    "homepage":
    {
      "@id": "foaf:homepage",
      "@type": "@id"
    }
  },
  ...
}
```

Compact IRIs and IRIs may be used on the left-hand side of a term definition.

EXAMPLE 39: Using a compact IRI as a term

```json
{
  "@context":
  {
    "foaf": "http://xmlns.com/foaf/0.1/",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "name": "foaf:name",
    "foaf:age":
    {
      "@type": "xsd:integer"
    },
    "foaf:homepage":
    {
      "@type": "@id"
    }
  },
  ...
}
```

Absolute IRIs may also be used in the key position in a context:

EXAMPLE 40: Associating context definitions with absolute IRIs

```json
{
  "@context":
  {
    "foaf": "http://xmlns.com/foaf/0.1/",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "name": "foaf:name",
    "foaf:age":
    {
      "@id": "foaf:age",
      "@type": "xsd:integer"
    },
    "http://xmlns.com/foaf/0.1/homepage":
    {
      "@type": "@id"
    }
  },
  ...
}
```

EXAMPLE 41: Illegal circular definition of terms within a context

```json
{
  "@context":
  {
    "term1": "term2:foo",
    "term2": "term1:bar"
  },
  ...
}
```

### Sets and Lists
EXAMPLE 42: Multiple values with no inherent order

```json
{
...
  "@id": "http://example.org/people#joebob",
  "nick": [ "joe", "bob", "JB" ],
...
}
```

Subject | Property | Value
--------|----------|------
http://example.org/people#joebob | http://xmlns.com/foaf/0.1/nick | joe
http://example.org/people#joebob | http://xmlns.com/foaf/0.1/nick | bob
http://example.org/people#joebob | http://xmlns.com/foaf/0.1/nick | JB

EXAMPLE 43: Using an expanded form to set multiple values

```json
{
  "@id": "http://example.org/articles/8",
  "dc:title": 
  [
    {
      "@value": "Das Kapital",
      "@language": "de"
    },
    {
      "@value": "Capital",
      "@language": "en"
    }
  ]
}
```

Subject | Property | Value | Language
--------|----------|-------|---------
http://example.org/articles/8 | http://purl.org/dc/terms/title | Das Kapital | de
http://example.org/articles/8 | http://purl.org/dc/terms/title | Capital | en

EXAMPLE 44: An ordered collection of values in JSON-LD

```json
{
...
  "@id": "http://example.org/people#joebob",
  "foaf:nick":
  {
    "@list": [ "joe", "bob", "jaybee" ]
  },
...
}
```

EXAMPLE 45: Specifying that a collection is ordered in the context

```json
{
  "@context":
  {
    ...
    "nick":
    {
      "@id": "http://xmlns.com/foaf/0.1/nick",
      "@container": "@list"
    }
  },
...
  "@id": "http://example.org/people#joebob",
  "nick": [ "joe", "bob", "jaybee" ],
...
}
```

### Reverse Properties
EXAMPLE 46: A document with children linking to their parent

```json
[
  {
    "@id": "#homer",
    "http://example.com/vocab#name": "Homer"
  },
  {
    "@id": "#bart",
    "http://example.com/vocab#name": "Bart",
    "http://example.com/vocab#parent": { "@id": "#homer" }
  },
  {
    "@id": "#lisa",
    "http://example.com/vocab#name": "Lisa",
    "http://example.com/vocab#parent": { "@id": "#homer" }
  }
]
```

EXAMPLE 47: A person and its children using a reverse property

```json
{
  "@id": "#homer",
  "http://example.com/vocab#name": "Homer",
  "@reverse": {
    "http://example.com/vocab#parent": [
      {
        "@id": "#bart",
        "http://example.com/vocab#name": "Bart"
      },
      {
        "@id": "#lisa",
        "http://example.com/vocab#name": "Lisa"
      }
    ]
  }
}
```

EXAMPLE 48: Using @reverse to define reverse properties

```json
{
  "@context": {
    "name": "http://example.com/vocab#name",
    "children": { "@reverse": "http://example.com/vocab#parent" }
  },
  "@id": "#homer",
  "name": "Homer",
  "children": [
    {
      "@id": "#bart",
      "name": "Bart"
    },
    {
      "@id": "#lisa",
      "name": "Lisa"
    }
  ]
}
```

### Named Graphs
At times, it is necessary to make statements about a graph itself, rather than just a single node. This can be done by grouping a set of nodes using the @graph keyword. A developer may also name data expressed using the @graph keyword by pairing it with an @id keyword as shown in the following example:

EXAMPLE 49: Identifying and making statements about a graph

```json
{
  "@context": {
    "generatedAt": {
      "@id": "http://www.w3.org/ns/prov#generatedAtTime",
      "@type": "http://www.w3.org/2001/XMLSchema#date"
    },
    "Person": "http://xmlns.com/foaf/0.1/Person",
    "name": "http://xmlns.com/foaf/0.1/name",
    "knows": "http://xmlns.com/foaf/0.1/knows"
  },
  "@id": "http://example.org/graphs/73",
  "generatedAt": "2012-04-09",
  "@graph":
  [
    {
      "@id": "http://manu.sporny.org/about#manu",
      "@type": "Person",
      "name": "Manu Sporny",
      "knows": "http://greggkellogg.net/foaf#me"
    },
    {
      "@id": "http://greggkellogg.net/foaf#me",
      "@type": "Person",
      "name": "Gregg Kellogg",
      "knows": "http://manu.sporny.org/about#manu"
    }
  ]
}
```

Graph | Subject | Property | Value | Value Type
------|---------|----------|-------|-----------
-  | http://example.org/graphs/73 | http://www.w3.org/ns/prov#generatedAtTime | 2012-04-09 | http://www.w3.org/2001/XMLSchema#date
http://example.org/graphs/73 | http://manu.sporny.org/about#manu | http://www.w3.org/2001/XMLSchema#type | http://xmlns.com/foaf/0.1/Person | -
http://example.org/graphs/73 | http://manu.sporny.org/about#manu | http://xmlns.com/foaf/0.1/name | Manu Sporny | -
http://example.org/graphs/73 | http://manu.sporny.org/about#manu | http://xmlns.com/foaf/0.1/knows | http://greggkellogg.net/foaf#me | -
http://example.org/graphs/73 | http://greggkellogg.net/foaf#me | http://www.w3.org/2001/XMLSchema#type | http://xmlns.com/foaf/0.1/Person | -
http://example.org/graphs/73 | http://greggkellogg.net/foaf#me | http://xmlns.com/foaf/0.1/name | Gregg Kellogg | -
http://example.org/graphs/73 | http://greggkellogg.net/foaf#me | http://xmlns.com/foaf/0.1/knows | http://manu.sporny.org/about#manu | -

EXAMPLE 50: Using @graph to explicitly express the default graph

```json
{
  "@context": ...,
  "@graph":
  [
    {
      "@id": "http://manu.sporny.org/about#manu",
      "@type": "foaf:Person",
      "name": "Manu Sporny",
      "knows": "http://greggkellogg.net/foaf#me"
    },
    {
      "@id": "http://greggkellogg.net/foaf#me",
      "@type": "foaf:Person",
      "name": "Gregg Kellogg",
      "knows": "http://manu.sporny.org/about#manu"
    }
  ]
}
```

EXAMPLE 51: Context needs to be duplicated if @graph is not used

```json
[
  {
    "@context": ...,
    "@id": "http://manu.sporny.org/about#manu",
    "@type": "foaf:Person",
    "name": "Manu Sporny",
    "knows": "http://greggkellogg.net/foaf#me"
  },
  {
    "@context": ...,
    "@id": "http://greggkellogg.net/foaf#me",
    "@type": "foaf:Person",
    "name": "Gregg Kellogg",
    "knows": "http://manu.sporny.org/about#manu"
  }
]
```

### Identifying Blank Nodes
EXAMPLE 52: Specifying a local blank node identifier

```json
{
   ...
   "@id": "_:n1",
   "name": "Secret Agent 1",
   "knows":
     {
       "name": "Secret Agent 2",
       "knows": { "@id": "_:n1" }
     }
}
```

### Aliasing Keywords
EXAMPLE 53: Aliasing keywords

```json
{
  "@context":
  {
     "url": "@id",
     "a": "@type",
     "name": "http://xmlns.com/foaf/0.1/name"
  },
  "url": "http://example.com/about#gregg",
  "a": "http://xmlns.com/foaf/0.1/Person",
  "name": "Gregg Kellogg"
}
```

### Expanded Document Form
EXAMPLE 55: Sample JSON-LD document

```json
{
   "@context":
   {
      "name": "http://xmlns.com/foaf/0.1/name",
      "homepage": {
        "@id": "http://xmlns.com/foaf/0.1/homepage",
        "@type": "@id"
      }
   },
   "name": "Manu Sporny",
   "homepage": "http://manu.sporny.org/"
}
```

EXAMPLE 56: Expanded form for the previous example

```json
[
  {
    "http://xmlns.com/foaf/0.1/name": [
      { "@value": "Manu Sporny" }
    ],
    "http://xmlns.com/foaf/0.1/homepage": [
      { "@id": "http://manu.sporny.org/" }
    ]
  }
]
```

### Compacted Document Form
EXAMPLE 57: Sample expanded JSON-LD document

```json
[
  {
    "http://xmlns.com/foaf/0.1/name": [ "Manu Sporny" ],
    "http://xmlns.com/foaf/0.1/homepage": [
      {
       "@id": "http://manu.sporny.org/"
      }
    ]
  }
]
```

EXAMPLE 58: Sample context

```json
{
  "@context": {
    "name": "http://xmlns.com/foaf/0.1/name",
    "homepage": {
      "@id": "http://xmlns.com/foaf/0.1/homepage",
      "@type": "@id"
    }
  }
}
```

EXAMPLE 59: Compact form of the sample document once sample context has been applied

```json
{
  "@context": {
    "name": "http://xmlns.com/foaf/0.1/name",
    "homepage": {
      "@id": "http://xmlns.com/foaf/0.1/homepage",
      "@type": "@id"
    }
  },
  "name": "Manu Sporny",
  "homepage": "http://manu.sporny.org/"
}
```

### Flattened Document Form
EXAMPLE 60: Sample JSON-LD document

```json
{
  "@context": {
    "name": "http://xmlns.com/foaf/0.1/name",
    "knows": "http://xmlns.com/foaf/0.1/knows"
  },
  "@id": "http://me.markus-lanthaler.com/",
  "name": "Markus Lanthaler",
  "knows": [
    {
      "@id": "http://manu.sporny.org/about#manu",
      "name": "Manu Sporny"
    },
    {
      "name": "Dave Longley"
    }
  ]
}
```

EXAMPLE 61: Flattened and compacted form for the previous example

```json
{
  "@context": {
    "name": "http://xmlns.com/foaf/0.1/name",
    "knows": "http://xmlns.com/foaf/0.1/knows"
  },
  "@graph": [
    {
      "@id": "_:b0",
      "name": "Dave Longley"
    },
    {
      "@id": "http://manu.sporny.org/about#manu",
      "name": "Manu Sporny"
    },
    {
      "@id": "http://me.markus-lanthaler.com/",
      "name": "Markus Lanthaler",
      "knows": [
        { "@id": "http://manu.sporny.org/about#manu" },
        { "@id": "_:b0" }
      ]
    }
  ]
}
```

[2]: https://www.w3.org/TR/json-ld/#bib-RDF11-CONCEPTS
[3]: https://www.w3.org/TR/json-ld/#bib-RFC3987
[4]: https://www.w3.org/TR/json-ld/#bib-BCP47
[5]: http://tools.ietf.org/html/bcp47#section-2.2.9
[6]: https://www.w3.org/TR/json-ld/#bib-RDF11-MT

[1]: http://www.w3.org/TR/rdf11-concepts/#dfn-generalized-rdf-dataset
[7]: https://www.w3.org/TR/json-ld/#dfn-term
[10]:https://www.w3.org/TR/json-ld/#dfn-property
[11]:https://www.w3.org/TR/json-ld/#dfn-node
[12]:https://www.w3.org/TR/json-ld/#dfn-typed-value

[8]: https://www.w3.org/TR/json-ld/#dfn-iri
[9]: https://www.w3.org/TR/json-ld/#dfn-blank-node-identifier
[13]:https://www.w3.org/TR/json-ld/#dfn-relative-iri
[15]:https://www.w3.org/TR/json-ld/#dfn-compact-iri

[14]:https://www.w3.org/TR/json-ld/#dfn-graph
[16]:https://www.w3.org/TR/rdf11-concepts/#dfn-default-graph
[17]:https://www.w3.org/TR/rdf11-concepts/#dfn-named-graph