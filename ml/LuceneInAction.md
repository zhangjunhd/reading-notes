![cover](https://img3.doubanio.com/view/subject/l/public/s5616050.jpg)

    作者: Michael McCandless / Erik Hatcher / Otis Gospodnetic
    出版社: Manning Publications
    副标题: Covers Apache Lucene 3.0
    出版年: 2010-7-28
    页数: 475
    定价: USD 49.99
    装帧: Paperback
    ISBN: 9781933988177

[豆瓣链接](https://book.douban.com/subject/3726306/)

- [Meet Lucene](#meet-lucene)
  - [WHAT IS LUCENE?](#what-is-lucene)
  - [LUCENE AND THE COMPONENTS OF A SEARCH APPLICATION](#lucene-and-the-components-of-a-search-application)
    - [Components for indexing](#components-for-indexing)
    - [Components for searching](#components-for-searching)
    - [The rest of the search application](#the-rest-of-the-search-application)
  - [LUCENE IN ACTION: A SAMPLE APPLICATION](#lucene-in-action-a-sample-application)
    - [Creating an index](#creating-an-index)
    - [Searching an index](#searching-an-index)
  - [UNDERSTANDING THE CORE INDEXING CLASSES](#understanding-the-core-indexing-classes)
    - [IndexWriter](#indexwriter)
    - [Directory](#directory)
    - [Analyzer](#analyzer)
    - [Document](#document)
    - [Field](#field)
  - [UNDERSTANDING THE CORE SEARCHING CLASSES](#understanding-the-core-searching-classes)
    - [IndexSearcher](#indexsearcher)
    - [Term](#term)
    - [Query](#query)
    - [TermQuery](#termquery)
    - [TopDocs](#topdocs)
- [Building a search index](#building-a-search-index)
  - [HOW LUCENE MODELS CONTENT](#how-lucene-models-content)
    - [Documents and fields](#documents-and-fields)
    - [Flexible schema](#flexible-schema)
    - [Denormalization](#denormalization)
  - [UNDERSTANDING THE INDEXING PROCESS](#understanding-the-indexing-process)
  - [BASIC INDEX OPERATIONS](#basic-index-operations)
    - [Adding documents to an index](#adding-documents-to-an-index)
    - [Deleting documents from an index](#deleting-documents-from-an-index)
    - [Updating documents in the index](#updating-documents-in-the-index)
  - [FIELD OPTIONS](#field-options)
    - [Field options for indexing](#field-options-for-indexing)
    - [Field options for storing fields](#field-options-for-storing-fields)
    - [Field options for term vectors](#field-options-for-term-vectors)
    - [Reader, TokenStream, and byte[] field values](#reader-tokenstream-and-byte-field-values)
    - [Field option combinations](#field-option-combinations)
    - [Field options for sorting](#field-options-for-sorting)
    - [Multivalued fields](#multivalued-fields)
  - [BOOSTING DOCUMENTS AND FIELDS](#boosting-documents-and-fields)
    - [Boosting documents](#boosting-documents)
    - [Boosting fields](#boosting-fields)
    - [Norms](#norms)
  - [INDEXING NUMBERS, DATES, AND TIMES](#indexing-numbers-dates-and-times)
    - [Indexing numbers](#indexing-numbers)
    - [Indexing dates and times](#indexing-dates-and-times)
  - [FIELD TRUNCATION](#field-truncation)
  - [NEAR-REAL-TIME SEARCH](#near-real-time-search)
  - [OPTIMIZING AN INDEX](#optimizing-an-index)
  - [OTHER DIRECTORY IMPLEMENTATIONS](#other-directory-implementations)
  - [CONCURRENCY, THREAD SAFETY, AND LOCKING ISSUES](#concurrency-thread-safety-and-locking-issues)
    - [Thread and multi-JVM safety](#thread-and-multi-jvm-safety)
    - [Accessing an index over a remote file system](#accessing-an-index-over-a-remote-file-system)
    - [Index locking](#index-locking)
- [Index File Formats](#index-file-formats)
  - [Definitions](#definitions)
  - [Types of Fields](#types-of-fields)
  - [Segments](#segments)
  - [Document Numbers](#document-numbers)
  - [Overview](#overview)
  - [File Naming](#file-naming)
- [Adding search to your application](#adding-search-to-your-application)
  - [IMPLEMENTING A SIMPLE SEARCH FEATURE](#implementing-a-simple-search-feature)
    - [Searching for a specific term](#searching-for-a-specific-term)
    - [Parsing a user-entered query expression: QueryParser](#parsing-a-user-entered-query-expression-queryparser)
  - [USING INDEXSEARCHER](#using-indexsearcher)
    - [Creating an IndexSearcher](#creating-an-indexsearcher)
    - [Performing searches](#performing-searches)
    - [Working with TopDocs](#working-with-topdocs)
    - [Paging through results](#paging-through-results)
    - [Near-real-time search](#near-real-time-search)
  - [UNDERSTANDING LUCENE SCORING](#understanding-lucene-scoring)
    - [How Lucene scores](#how-lucene-scores)
    - [Using explain() to understand hit scoring](#using-explain-to-understand-hit-scoring)
  - [LUCENE’S DIVERSE QUERIES](#lucenes-diverse-queries)
    - [Searching by term: TermQuery](#searching-by-term-termquery)
    - [Searching within a term range: TermRangeQuery](#searching-within-a-term-range-termrangequery)
    - [Searching within a numeric range: NumericRangeQuery](#searching-within-a-numeric-range-numericrangequery)
    - [Searching on a string: PrefixQuery](#searching-on-a-string-prefixquery)
    - [Combining queries: BooleanQuery](#combining-queries-booleanquery)
    - [Searching by phrase: PhraseQuery](#searching-by-phrase-phrasequery)
    - [Searching by wildcard: WildcardQuery](#searching-by-wildcard-wildcardquery)
    - [Searching for similar terms: FuzzyQuery](#searching-for-similar-terms-fuzzyquery)
    - [Matching all documents: MatchAllDocsQuery](#matching-all-documents-matchalldocsquery)
  - [PARSING QUERY EXPRESSIONS: QUERYPARSER](#parsing-query-expressions-queryparser)
    - [Query.toString](#querytostring)
    - [TermQuery](#termquery-1)
    - [Term range searches](#term-range-searches)
    - [Numeric and date range searches](#numeric-and-date-range-searches)
    - [Prefix and wildcard queries](#prefix-and-wildcard-queries)
    - [Boolean operators](#boolean-operators)
    - [Phrase queries](#phrase-queries)
    - [Fuzzy queries](#fuzzy-queries)
    - [MatchAllDocsQuery](#matchalldocsquery)
    - [Grouping](#grouping)
    - [Setting the boost for a subquery](#setting-the-boost-for-a-subquery)
- [Lucene’s analysis process](#lucenes-analysis-process)
  - [USING ANALYZERS](#using-analyzers)
    - [Indexing analysis](#indexing-analysis)
    - [QueryParser analysis](#queryparser-analysis)
    - [Parsing vs. analysis: when an analyzer isn’t appropriate](#parsing-vs-analysis-when-an-analyzer-isnt-appropriate)
  - [WHAT’S INSIDE AN ANALYZER?](#whats-inside-an-analyzer)
    - [What’s in a token?](#whats-in-a-token)
    - [TokenStream uncensored](#tokenstream-uncensored)
    - [Visualizing analyzers](#visualizing-analyzers)
  - [USING THE BUILT-IN ANALYZERS](#using-the-built-in-analyzers)
  - [SOUNDS-LIKE QUERYING](#sounds-like-querying)
  - [SYNONYMS, ALIASES, AND WORDS THAT MEAN THE SAME](#synonyms-aliases-and-words-that-mean-the-same)
    - [Creating SynonymAnalyzer](#creating-synonymanalyzer)
    - [Visualizing token positions](#visualizing-token-positions)
  - [STEMMING ANALYSIS](#stemming-analysis)
    - [StopFilter leaves holes](#stopfilter-leaves-holes)
    - [Combining stemming and stop-word removal](#combining-stemming-and-stop-word-removal)

# Meet Lucene
##  WHAT IS LUCENE?
Lucene is a high-performance, scalable `information retrieval` (`IR`) library. `IR` refers to the process of searching for documents, information within documents, or metadata about documents.

## LUCENE AND THE COMPONENTS OF A SEARCH APPLICATION
Figure 1.4. Typical components of search application; the shaded components show which parts Lucene handles.

![1.4](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/01fig03a.jpg)

### Components for indexing
- `Acquire Content`:which involves using a crawler or spider, gathers and scopes the content that needs to be indexed.
- `Build Document`:Once you have the raw content that needs to be indexed, you must translate the content into the `units` (usually called `documents`) used by the search engine. The document typically consists of several separately named fields with values, such as `title`, `body`, `abstract`, `author`, and `url`.
- `Analyze Document`:No search engine indexes text directly: rather, the text must be broken into a series of individual atomic elements called `tokens`.
- `Index Document`:During the indexing step, the document is added to the index.

### Components for searching
- `Search User Interface`:The user interface is what users actually see, in the web browser, desktop application, or mobile device, when they interact with your search application.
- `Build Query`
  - You must then translate the request into the search engine’s `Query` object. We call this the `Build Query` step.
  - Lucene provides a powerful package, called `QueryParser`, to process the user’s text into a query object according to a common search syntax.
- `Search Query`
  - Search Query is the process of consulting the search index and retrieving the documents matching the Query, sorted in the requested sort order.
  - There are three common theoretical models of search:
    - `Pure Boolean model`— Documents either match or don’t match the provided query, and no scoring is done. In this model there are no relevance scores associated with matching documents, and the matching documents are unordered; a query simply identifies a subset of the overall corpus as matching the query.
    - `Vector space model`— Both queries and documents are modeled as vectors in a high dimensional space, where each unique term is a dimension. Relevance, or similarity, between a query and a document is computed by a vector distance measure between these vectors.
    - `Probabilistic model`— In this model, you compute the probability that a document is a good match to a query using a full probabilistic approach.
- `Render Results`:Once you have the raw set of documents that match the query, sorted in the right order, you then render them to the user in an intuitive, consumable manner.

### The rest of the search application
- `Administration Interface`:tune the size of the RAM buffer, how many segments to merge at once, how often to commit changes, or when to optimize and purge deletes from the index.
- `Analytics Interface`:Lucene-specific metrics that could feed the analytics interface include:
  - How often which kinds of queries (single term, phrase, Boolean queries, etc.) are run
  - Queries that hit low relevance
  - Queries where the user didn’t click on any results (if your application tracks click-throughs)
  - How often users are sorting by specified fields instead of relevance
  - The breakdown of Lucene’s search time
- `Scaling`:There are two dimensions to scaling: **net amount of content**, and **net query throughput**.

## LUCENE IN ACTION: A SAMPLE APPLICATION
### Creating an index
Listing 1.1 shows the Indexer command-line program, originally written for Erik’s introductory Lucene article on java.net. It takes two arguments:

- A path to a directory where we store the Lucene index
- A path to a directory that contains the files we want to index

Listing 1.1. Indexer, which indexes .txt files

![l1.1](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/ch01ex01-0.jpg)

Go ahead and type ant Indexer, and you should see output like this:

```
% ant Indexer

Index *.txt files in a directory into a Lucene index.
Use the Searcher target to search this index.

Indexer is covered in the "Meet Lucene" chapter.

Press return to continue...

Directory for new Lucene index: [indexes/MeetLucene]

Directory with .txt files to index: [src/lia/meetlucene/data]

Overwrite indexes/MeetLucene? (y, n) y
Running lia.meetlucene.Indexer...
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/apache1.0.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/apache1.1.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/apache2.0.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/cpl1.0.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/epl1.0.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/freebsd.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/gpl1.0.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/gpl2.0.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/gpl3.0.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/lgpl2.1.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/lgpl3.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/lpgl2.0.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/mit.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/mozilla1.1.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/
 mozilla_eula_firefox3.txt
Indexing /Users/mike/lia2e/src/lia/meetlucene/data/
 mozilla_eula_thunderbird2.txt
Indexing 16 files took 757 milliseconds

BUILD SUCCESSFUL
```

### Searching an index
The Searcher program, originally written for Erik’s introductory Lucene article on java.net, complements Indexer and provides command-line searching capability. Listing 1.2 shows Searcher in its entirety. It takes two command-line arguments:

- The path to the index created with Indexer
- A query to use to search the index

Listing 1.2. Searcher, which searches a Lucene index

![l1.2](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/ch01ex02-0.jpg)

Let’s run Searcher and find documents in our index using the query ‘patent’

```
% ant Searcher

Search an index built using Indexer.
Searcher is described in the "Meet Lucene" chapter.

Press return to continue...

Directory of existing Lucene index built by
 Indexer:  [indexes/MeetLucene]

Query:  [patent]

Running lia.meetlucene.Searcher...
Found 8 document(s) (in 11 milliseconds) that
 matched query 'patent':
/Users/mike/lia2e/src/lia/meetlucene/data/cpl1.0.txt
/Users/mike/lia2e/src/lia/meetlucene/data/mozilla1.1.txt
/Users/mike/lia2e/src/lia/meetlucene/data/epl1.0.txt
/Users/mike/lia2e/src/lia/meetlucene/data/gpl3.0.txt
/Users/mike/lia2e/src/lia/meetlucene/data/apache2.0.txt
/Users/mike/lia2e/src/lia/meetlucene/data/lpgl2.0.txt
/Users/mike/lia2e/src/lia/meetlucene/data/gpl2.0.txt
/Users/mike/lia2e/src/lia/meetlucene/data/lgpl2.1.txt

BUILD SUCCESSFUL
Total time: 4 seconds
```

## UNDERSTANDING THE CORE INDEXING CLASSES
As you saw in our Indexer class, you need the following classes to perform the simplest indexing procedure:

- IndexWriter
- Directory
- Analyzer
- Document
- Field

Figure 1.5. Classes used when indexing documents with Lucene

![1.5](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/01fig05.jpg)

### IndexWriter
`IndexWriter` is the central component of the indexing process. This class creates a new index or opens an existing one, and adds, removes, or updates documents in the index. Think of IndexWriter as an object that gives you write access to the index but doesn’t let you read or search it. IndexWriter needs somewhere to store its index, and that’s what Directory is for.

### Directory
The `Directory` class represents the location of a Lucene index. It’s an abstract class that allows its subclasses to store the index as they see fit. In our Indexer example, we used FSDirectory.open to get a suitable concrete FSDirectory implementation that stores real files in a directory on the file system, and passed that in turn to IndexWriter’s constructor.

### Analyzer
Before text is indexed, it’s passed through an `analyzer`. The analyzer, specified in the IndexWriter constructor, is in charge of extracting those tokens out of text that should be indexed and eliminating the rest. Analyzer is an abstract class, but Lucene comes with several implementations of it.

- Some of them deal with skipping `stop words` (frequently used words that don’t help distinguish one document from the other, such as a, an, the, in, and on);
- some deal with conversion of tokens to lowercase letters, so that searches aren’t case sensitive;
- and so on.

### Document
The `Document` class represents a collection of fields. Think of it as a virtual document—a chunk of data, such as a web page, an email message, or a text file—that you want to make retrievable at a later time.

### Field
Each document in an index contains one or more named `fields`, embodied in a class called Field. Each field has a name and corresponding value, and a bunch of options, described in section 2.4, that control precisely how Lucene will index the field’s value.

## UNDERSTANDING THE CORE SEARCHING CLASSES
The basic search interface that Lucene provides is as straightforward as the one for indexing. Only a few classes are needed to perform the basic search operation:

- IndexSearcher
- Term
- Query
- TermQuery
- TopDocs

### IndexSearcher
`IndexSearcher` is to searching what IndexWriter is to indexing: the central link to the index that exposes several search methods. You can think of IndexSearcher as a class that opens an index in a read-only mode. It requires a Directory instance, holding the previously created index, and then offers a number of search methods, some of which are implemented in its abstract parent class Searcher; the simplest takes a Query object and an int topN count as parameters and returns a TopDocs object. A typical use of this method looks like this:

```java
Directory dir = FSDirectory.open(new File("/tmp/index"));
IndexSearcher searcher = new IndexSearcher(dir);
Query q = new TermQuery(new Term("contents", "lucene"));
TopDocs hits = searcher.search(q, 10);
searcher.close();
```

### Term
A `Term` is the basic unit for searching. Similar to the Field object, it consists of a pair of string elements: the name of the field and the word (text value) of that field.

During searching, you may construct Term objects and use them together with TermQuery:

```java
Query q = new TermQuery(new Term("contents", "lucene"));
TopDocs hits = searcher.search(q, 10);
```

### Query
Lucene comes with a number of concrete `Query` subclasses. So far in this chapter we’ve mentioned only the most basic Lucene Query: TermQuery. Other Query types are BooleanQuery, PhraseQuery, PrefixQuery, PhrasePrefixQuery, TermRangeQuery, NumericRangeQuery, FilteredQuery, and SpanQuery.

### TermQuery
`TermQuery` is the most basic type of query supported by Lucene, and it’s one of the primitive query types. It’s used for matching documents that contain fields with specific values, as you’ve seen in the last few paragraphs.

### TopDocs
The `TopDocs` class is a simple container of pointers to the top N ranked search results—documents that match a given query. For each of the top N results, TopDocs records the int docID (which you can use to retrieve the document) as well as the float score.

# Building a search index
## HOW LUCENE MODELS CONTENT
### Documents and fields
At a high level, there are three things Lucene can do with each field:

- The value may be indexed (or not).
- If it’s indexed, the field may also optionally store term vectors, which are collectively a miniature inverted index for that one field, allowing you to retrieve all of its tokens.
- Separately, the field’s value may be stored, meaning a verbatim copy of the unanalyzed value is written away in the index so that it can later be retrieved. This is useful for fields you’d like to present unchanged to the user, such as the document’s title or abstract.

### Flexible schema
Unlike a database, Lucene has no notion of a fixed global schema.

The second major difference between Lucene and databases is that Lucene requires you to flatten, or denormalize, your content when you index it.

### Denormalization
Lucene documents are flat. Such recursion and joins must be denormalized when creating your documents.

## UNDERSTANDING THE INDEXING PROCESS
Figure 2.1. Indexing with Lucene breaks down into three main operations: extracting text from source documents, analyzing it, and saving it to the index.

![2.1](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/02fig01.jpg)

- Extracting text and creating the document
- Analysis
- Adding to the index

Figure 2.2. Segmented structure of a Lucene inverted index

![2.2](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/02fig02.jpg)

## BASIC INDEX OPERATIONS
### Adding documents to an index
There are two methods for adding documents:

- addDocument(Document)—Adds the document using the default analyzer, which you specified when creating the IndexWriter, for tokenization.
- addDocument(Document, Analyzer)—Adds the document using the provided analyzer for tokenization. But be careful! In order for searches to work correctly, you need the analyzer used at search time to “match” the tokens produced by the analyzers at indexing time.

Listing 2.1. Adding documents to an index

![l2.1](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/ch02ex01-0.jpg)
![l2.1](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/ch02ex01-1.jpg)

In the getWriter method, we create the IndexWriter with three arguments:

- `Directory`, where the index is stored.
- The analyzer to use when indexing tokenized fields.
- MaxFieldLength.UNLIMITED, a required argument that tells IndexWriter to index all tokens in the document.

```java
public static int hitCount(IndexSearcher searcher, Query query)
 throws IOException {
  return searcher.search(query, 1).totalHits;
}
```

This method runs the search and returns the total number of hits that matched.

### Deleting documents from an index
IndexWriter provides various methods to remove documents from an index:

- deleteDocuments(Term) deletes all documents containing the provided term.
- deleteDocuments(Term[]) deletes all documents containing any of the terms in the provided array.
- deleteDocuments(Query) deletes all documents matching the provided query.
- deleteDocuments(Query[]) deletes all documents matching any of the queries in the provided array.
- deleteAll() deletes all documents in the index. This is exactly the same as closing the writer and opening a new writer with create=true, without having to close your writer.

Listing 2.2. Deleting documents from an index

![l2.2](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/041fig01_alt.jpg)

- maxDoc() returns the total number of deleted or undeleted documents in the index,
- numDocs() returns only the number of undeleted documents.

### Updating documents in the index
IndexWriter provides two convenience methods to replace a document in the index:

- updateDocument(Term, Document) first deletes all documents containing the provided term and then adds the new document using the writer’s default analyzer.
- updateDocument(Term, Document, Analyzer) does the same but uses the provided analyzer instead of the writer’s default analyzer.

Listing 2.3. Updating indexed Documents

![l2.3](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/043fig01_alt.jpg)

## FIELD OPTIONS
### Field options for indexing
The options for indexing (Field.Index.*) control how the text in the field will be made searchable via the inverted index. Here are the choices:

- `Index.ANALYZED`—Use the analyzer to break the field’s value into a stream of separate tokens and make each token searchable. This option is useful for normal text fields (body, title, abstract, etc.).
- `Index.NOT_ANALYZED`—Do index the field, but don’t analyze the String value. Instead, treat the Field’s entire value as a single token and make that token searchable. This option is useful for fields that you’d like to search on but that shouldn’t be broken up, such as URLs, file system paths, dates, personal names, Social Security numbers, and telephone numbers. This option is especially useful for enabling “exact match” searching.
- `Index.ANALYZED_NO_NORMS`—A variant of `Index.ANALYZED` that doesn’t store norms information in the index. Norms record index-time boost information in the index but can be memory consuming when you’re searching.
- `Index.NOT_ANALYZED_NO_NORMS`—Just like Index.NOT_ANALYZED, but also doesn’t store norms. This option is frequently used to save index space and memory usage during searching, because single-token fields don’t need the norms information unless they’re boosted.
- `Index.NO`—Don’t make this field’s value available for searching.

### Field options for storing fields
The options for stored fields (Field.Store.*) determine whether the field’s exact value should be stored away so that you can later retrieve it during searching:

- Store.YES —Stores the value. When the value is stored, the original String in its entirety is recorded in the index and may be retrieved by an IndexReader. This option is useful for fields that you’d like to use when displaying the search results (such as a URL, title, or database primary key). Try not to store very large fields, if index size is a concern, as stored fields consume space in the index.
- Store.NO —Doesn’t store the value. This option is often used along with Index.ANALYZED to index a large text field that doesn’t need to be retrieved in its original form, such as bodies of web pages, or any other type of text document.

### Field options for term vectors
Term vectors are a mix between an indexed field and a stored field. They’re similar to a stored field because you can quickly retrieve all term vector fields for a given document: term vectors are keyed first by document ID. But then, they’re keyed secondarily by term, meaning they store a miniature inverted index for that one document. Unlike a stored field, where the original String content is stored verbatim, term vectors store the actual separate terms that were produced by the analyzer, allowing you to retrieve all terms for each field, and the frequency of their occurrence within the document, sorted in lexicographic order.

You can choose separately whether these details are also stored in your term vectors by passing these constants as the fourth argument to the Field constructor:

- TermVector.YES—Records the unique terms that occurred, and their counts, in each document, but doesn’t store any positions or offsets information
- TermVector.WITH_POSITIONS—Records the unique terms and their counts, and also the positions of each occurrence of every term, but no offsets
- TermVector.WITH_OFFSETS—Records the unique terms and their counts, with the offsets (start and end character position) of each occurrence of every term, but no positions
- TermVector.WITH_POSITIONS_OFFSETS—Stores unique terms and their counts, along with positions and offsets
- TermVector.NO—Doesn’t store any term vector information

### Reader, TokenStream, and byte[] field values
There are a few other constructors for the Field object that allow you to use values other than String:

- Field(String name, Reader value, TermVector termVector) uses a Reader instead of a String to represent the value. In this case, the value can’t be stored (the option is hardwired to Store.NO) and is always analyzed and indexed (Index.ANALYZED). This can be useful when holding the full String in memory might be too costly or inconvenient—for example, for very large values.
- Field(String name, Reader value), like the previous value, uses a Reader instead of a String to represent the value but defaults termVector to TermVector.NO.
- Field(String name, TokenStream tokenStream, TermVector termVector) allows you to preanalyze the field value into a TokenStream. Likewise, such fields aren’t stored and are always analyzed and indexed.
- Field(String name, TokenStream tokenStream), like the previous value, allows you to preanalyze the field value into a TokenStream but defaults termVector to TermVector.NO.
- Field(String name, byte[] value, Store store) is used to store a binary field. Such fields are never indexed (Index.NO) and have no term vectors (TermVector.NO). The store argument must be Store.YES.
- Field(String name, byte[] value, int offset, int length, Store store), like the previous value, indexes a binary field but allows you to reference a sub-slice of the bytes starting at offset and running for length bytes.

### Field option combinations
Table 2.1. A summary of various field characteristics, showing you how fields are created, along with common usage examples

| Index | Store | TermVector | Example usage |
| --- | --- | --- | --- |
| NOT_ANALYZED_NO_NORMS	| YES	| NO | Identifiers (filenames, primary keys), telephone and Social Security numbers, URLs, personal names, dates, and textual fields for sorting|
| ANALYZED | YES | WITH_POSITIONS_OFFSETS | Document title, document abstract |
| ANALYZED | NO | WITH_POSITIONS_OFFSETS | Document body |
| NO | YES | NO | Document type, database primary key (if not used for searching) |
| NOT_ANALYZED | NO | NO | Hidden keywords |

### Field options for sorting
- If the field is numeric, use `NumericField`
- If the field is textual, such as the sender’s name in an email message, you must add it as a `Field` that’s indexed but not analyzed using `Field.Index.NOT_ANALYZED`
- If you aren’t doing any boosting for the field, you should index it without norms, to save disk space and memory, using `Field.Index.NOT_ANALYZED_NO_NORMS`:

```java
new Field("author", "Arthur C. Clark", Field.Store.YES,
          Field.Index.NOT_ANALYZED_NO_NORMS);
```

`Fields` used for sorting must be indexed and must contain one token per document. Typically this means using `Field.Index.NOT_ANALYZED` or `Field.Index.NOT_ANALYZED_NO_NORMS` (if you’re not boosting documents or fields), but if your analyzer will always produce only one token, such as `KeywordAnalyzer`, `Field.Index.ANALYZED` or `Field.Index.ANALYZED_NO_NORMS` will work as well.

### Multivalued fields
This is perfectly acceptable and encouraged, as it’s a natural way to represent a field that legitimately has multiple values.

## BOOSTING DOCUMENTS AND FIELDS
### Boosting documents
By changing a document’s boost factor, you can instruct Lucene to consider it more or less important with respect to other documents in the index when computing relevance.

Listing 2.4. Selectively boosting documents and fields

![l2.4](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/049fig01_alt.jpg)

### Boosting fields
Just as you can boost documents, you can also boost individual fields.

To achieve this behavior, we use the setBoost(float) method of the Field class:

```java
Field subjectField = new Field("subject", subject,
                               Field.Store.YES,
                               Field.Index.ANALYZED);
subjectField.setBoost(1.2F);
```

### Norms
During searching, norms for any field being searched are loaded into memory, decoded back into a floating-point number, and used when computing the relevance score.

## INDEXING NUMBERS, DATES, AND TIMES
### Indexing numbers
```java
doc.add(new NumericField("price").setDoubleValue(19.99));
```

### Indexing dates and times
```java
doc.add(new NumericField("timestamp").setLongValue(new Date().getTime()));

doc.add(new NumericField("day").setIntValue((int) (new Date().getTime()/24/3600)));

Calendar cal = Calendar.getInstance();
cal.setTime(date);
doc.add(new NumericField("dayOfMonth").setIntValue(cal.get(Calendar.DAY_OF_MONTH)));
```

## FIELD TRUNCATION
`IndexWriter` allows you to truncate per-Field indexing so that only the first N terms are indexed for an analyzed field. When you instantiate IndexWriter, you must pass in a `MaxFieldLength` instance expressing this limit. MaxFieldLength provides two convenient default instances: `MaxFieldLength.UNLIMITED`, which means no truncation will take place, and `MaxFieldLength.LIMITED`, which means fields are truncated at 10,000 terms. You can also instantiate MaxFieldLength with your own limit.

## NEAR-REAL-TIME SEARCH
```java
IndexReader getReader()
```

This method immediately flushes any buffered added or deleted documents, and then creates a new read-only IndexReader that includes those documents.

## OPTIMIZING AN INDEX
Optimizing only improves searching speed, not indexing speed.

IndexWriter exposes four methods to optimize:

- optimize() reduces the index to a single segment, not returning until the operation is finished.
- optimize(int maxNumSegments), also known as partial optimize, reduces the index to at most maxNumSegments segments. Because the final merge down to one segment is the most costly, optimizing to, say, five segments should be quite a bit faster than optimizing down to one segment, allowing you to trade less optimization time for slower search speed.
- optimize(boolean doWait) is just like optimize, except if doWait is false then the call returns immediately while the necessary merges take place in the background. Note that doWait=false only works for a merge scheduler that runs merges in background threads, such as the default ConcurrentMergeScheduler.
- optimize(int maxNumSegments, boolean doWait) is a partial optimize that runs in the background if doWait is false.

## OTHER DIRECTORY IMPLEMENTATIONS
Table 2.2. Lucene’s several core Directory implementations

| Directory | Description |
| --- | --- |
| SimpleFSDirectory	| A simplistic Directory that stores files in the file system, using java.io.* APIs. It doesn’t scale well with many threads.|
| NIOFSDirectory | A Directory that stores files in the file system, using java.nio.* APIs. This does scale well with threads on all platforms except Microsoft Windows, due to a longstanding issue with Sun’s Java Runtime Environment (JRE).|
| MMapDirectory | A Directory that uses memory-mapped I/O to access files. This is a good choice on 64-bit JREs, or on 32-bit JREs where the size of the index is relatively small.|
| RAMDirectory | A Directory that stores all files in RAM.|
| FileSwitchDirectory	| A Directory that takes two directories in, and switches between these directories based on file extension.|

## CONCURRENCY, THREAD SAFETY, AND LOCKING ISSUES
### Thread and multi-JVM safety
Figure 2.3. A single IndexWriter can be shared by multiple threads.

![2.3](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/02fig03.jpg)

### Accessing an index over a remote file system
Table 2.3. Issues related to accessing a Lucene index across remote file systems

| Remote file system | Notes |
| --- | --- |
| Samba/CIFS 1.0 | The standard remote file system for Windows computers. Sharing a Lucene index works fine.|
| Samba/CIFS 2.0 | The new version of Samba/CIFS that’s the default for Windows Server 2007 and Windows Vista. Lucene has trouble due to incoherent client-side caches.|
| Networked File System (NFS) | The standard remote file systems for most Unix OSs. Lucene has trouble due to both incoherent client-side caches as well as how NFS handles deletion of files that are held open by another computer.|
| Apple File Protocol (AFP) | Apple’s standard remote file system protocol. Lucene has trouble due to incoherent client-side caches.|

### Index locking
Table 2.4. Locking implementations provided by Lucene

| Locking class name | Description |
| -- | --- |
| NativeFSLockFactory |	This is the default locking for FSDirectory, using java.nio native OS locking, which will never leave leftover lock files when the JVM exits. But this locking implementation may not work correctly over certain shared file systems, notably NFS.|
| SimpleFSLockFactory	| Uses Java’s File.createNewFile API, which may be more portable across different file systems than NativeFSLockFactory. Be aware that if the JVM crashes or IndexWriter isn’t closed before the JVM exits, this may leave a leftover write.lock file, which you must manually remove.|
| SingleInstanceLockFactory	| Creates a lock entirely in memory. This is the default locking implementation for RAMDirectory. Use this when you know all IndexWriters will be instantiated in a single JVM.|
| NoLockFactory	| Disables locking entirely. Be careful! Only use this when you are absolutely certain that Lucene’s normal locking safeguard isn’t necessary—for example, when using a private RAMDirectory with a single IndexWriter instance.|

Listing 2.5. Using file-based locks to enforce a single writer at a time

![2.5](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/063fig01_alt.jpg)

# Index File Formats 
http://lucene.apache.org/core/3_5_0/fileformats.html

## Definitions
- An `index` contains a sequence of documents.
- A `document` is a sequence of fields.
- A `field` is a named sequence of terms.
- A `term` is a string.

## Types of Fields
In Lucene, fields may be `stored`, in which case their text is stored in the index literally, in a non-inverted manner. Fields that are inverted are called `indexed`. A field may be both stored and indexed.

The text of a field may be tokenized into terms to be indexed, or the text of a field may be used literally as a term to be indexed. Most fields are tokenized, but sometimes it is useful for certain identifier fields to be indexed literally.

## Segments
Lucene indexes may be composed of multiple sub-indexes, or `segments`. Each segment is a fully independent index, which could be searched separately. Indexes evolve by:

1. Creating new segments for newly added documents.
2. Merging existing segments.

## Document Numbers
Internally, Lucene refers to documents by an integer `document number`. The first document added to an index is numbered zero, and each subsequent document added gets a number one greater than the previous.

In particular, numbers may change in the following situations:

- The numbers stored in each segment are unique only within the segment, and must be converted before they can be used in a larger context. The standard technique is to allocate each segment a range of values, based on the range of numbers used in that segment. To convert a document number from a segment to an external value, the segment's base document number is added. To convert an external value back to a segment-specific value, the segment is identified by the range that the external value is in, and the segment's base value is subtracted. For example two five document segments might be combined, so that the first segment has a base value of zero, and the second of five. Document three from the second segment would have an external value of eight.
- When documents are deleted, gaps are created in the numbering. These are eventually removed as the index evolves through merging. Deleted documents are dropped when segments are merged. A freshly-merged segment thus has no gaps in its numbering.

## Overview
Each segment index maintains the following:

- `Field names`. This contains the set of field names used in the index.
- `Stored Field values`. This contains, for each document, a list of attribute-value pairs, where the attributes are field names. These are used to store auxiliary information about the document, such as its title, url, or an identifier to access a database. The set of stored fields are what is returned for each hit when searching. This is keyed by document number.
- `Term dictionary`. A dictionary containing all of the terms used in all of the indexed fields of all of the documents. The dictionary also contains the number of documents which contain the term, and pointers to the term's frequency and proximity data.
- `Term Frequency data`. For each term in the dictionary, the numbers of all the documents that contain that term, and the frequency of the term in that document, unless frequencies are omitted (IndexOptions.DOCS_ONLY)
- `Term Proximity data`. For each term in the dictionary, the positions that the term occurs in each document. Note that this will not exist if all fields in all documents omit position data.
- `Normalization factors`. For each field in each document, a value is stored that is multiplied into the score for hits on that field.
- `Term Vectors`. For each field in each document, the term vector (sometimes called document vector) may be stored. A term vector consists of term text and term frequency. 
- `Deleted documents`. An optional file indicating which documents are deleted.

## File Naming
All files belonging to a segment have the same name with varying extensions. The extensions correspond to the different file formats described below. When using the Compound File format (default in 1.4 and greater) these files are collapsed into a single `.cfs` file (see below for details)

Typically, all segments in an index are stored in a single directory, although this is not required.

As of version 2.1 (lock-less commits), file names are never re-used (there is one exception, "segments.gen", see below). That is, when any file is saved to the Directory `it is given a never before used filename`. This is achieved using a simple generations approach. For example, the first segments file is segments_1, then segments_2, etc. The generation is a sequential long integer represented in alpha-numeric (base 36) form.

# Adding search to your application
Table 3.1. Lucene’s primary searching API

| Class | Purpose |
| --- | --- |
| IndexSearcher | Gateway to searching an index. All searches come through an IndexSearcher instance using any of the several overloaded search methods.|
| Query (and subclasses) | Concrete subclasses encapsulate logic for a particular query type. Instances of Query are passed to an IndexSearcher’s search method.|
| QueryParser | Processes a human-entered (and readable) expression into a concrete Query object.|
| TopDocs | Holds the top scoring documents, returned by IndexSearcher.search.|
| ScoreDoc | Provides access to each search result in TopDocs.|

## IMPLEMENTING A SIMPLE SEARCH FEATURE
### Searching for a specific term
Listing 3.1. Simple searching with TermQuery

![l3.1](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/077fig01_alt.jpg)

### Parsing a user-entered query expression: QueryParser
Figure 3.1. QueryParser translates a textual expression from the end user into an arbitrarily complex query for searching.

![f3.1](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/03fig01.jpg)

Listing 3.2. QueryParser, which makes it trivial to translate search text into a Query

![l3.2](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/078fig01_alt.jpg)

Table 3.2. Expression examples that QueryParser handles

| Query expression | Matches documents that... |
| --- | --- |
| java | Contain the term java in the default field|
| java junit | Contain the term java or junit, or both, in the default field|
| java OR junit | - |
| +java +junit | Contain both java and junit in the default field |
| java AND junit | - |
| title:ant | Contain the term ant in the title field|
| title:extreme–subject:sports | Contain extreme in the title field and don’t have sports in the subject field|
| title:extreme AND NOT subject:sports	| - |
| (agile OR extreme) AND methodology | Contain methodology and must also contain agile and/or extreme, all in the default field|
| title:"junit in action" | Contain the exact phrase “junit in action” in the title field|
| title:"junit action"~5 | Contain the terms junit and action within five positions of one another, in the title field |
| java*	| Contain terms that begin with java, like javaspaces, javaserver, java.net, and the exact tem java itself.|
| java~ | Contain terms that are close to the word java, such as lava|
| lastmodified: [1/1/09 TO 12/31/09] | Have lastmodified field values between the dates January 1, 2009 and December 31, 2009|

## USING INDEXSEARCHER
### Creating an IndexSearcher
Figure 3.2. The relationship between the common classes used for searching

![f2.3](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/03fig02.jpg)

### Performing searches
Table 3.3. Primary IndexSearcher search methods

| IndexSearcher.search method signature | When to use |
| --- | --- |
| TopDocs search(Query query, int n) | Straightforward searches. The int n parameter specifies how many top-scoring documents to return.|
| TopDocs search(Query query, Filter filter, int n) | Searches constrained to a subset of available documents, based on filter criteria.|
| TopFieldDocs search(Query query, Filter filter, int n, Sort sort) | Searches constrained to a subset of available documents based on filter criteria, and sorted by a custom Sort object|
| void search(Query query, Collector results) | Used when you have custom logic to implement for each document visited, or you’d like to collect a different subset of documents than the top N by the sort criteria.|
| void search(Query query, Filter filter, Collector results) | Same as previous, except documents are only accepted if they pass the filter criteria.|

### Working with TopDocs
Table 3.4. TopDocs methods for efficiently accessing search results03_Ch03.fm

| TopDocs method or attribute | Return value |
| --- | --- |
| totalHits | Number of documents that matched the search|
| scoreDocs | Array of ScoreDoc instances that contains the results|
| getMaxScore() | Returns best score of all matches, if scoring was done while searching (when sorting by field, you separately control whether scores are computed)|

### Paging through results
You can choose from a couple of implementation approaches:

- Gather multiple pages’ worth of results on the initial search and keep the resulting ScoreDocs and IndexSearcher instances available while the user is navigating the search results.
- Requery each time the user navigates to a new page.

### Near-real-time search
Listing 3.3. Near-real-time search

![l3.3](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/ch03ex03-0.jpg)
![l3.3-1](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/ch03ex03-1.jpg)

## UNDERSTANDING LUCENE SCORING
### How Lucene scores
Figure 3.3. Lucene uses this formula to determine a document score based on a query.

![f3.3](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/03fig03_alt.jpg)

Table 3.5. Factors in the scoring formula

| Factor |  Description |
| --- | --- |
| tf(t in d) | Term frequency factor for the term (t) in the document (d)—how many times the term t occurs in the document.|
| idf(t) | Inverse document frequency of the term: a measure of how “unique” the term is. Very common terms have a low idf; very rare terms have a high idf.
| boost(t.field in d) | Field and document boost, as set during indexing (see section 2.5). You may use this to statically boost certain fields and certain documents over others.|
| lengthNorm(t.field in d) | Normalization value of a field, given the number of terms within the field. This value is computed during indexing and stored in the index norms. Shorter fields (fewer tokens) get a bigger boost from this factor.|
| coord(q, d) | Coordination factor, based on the number of query terms the document contains. The coordination factor gives an AND-like boost to documents that contain more of the search terms than other documents.|
| queryNorm(q) | Normalization value for a query, given the sum of the squared weights of each of the query terms.|

### Using explain() to understand hit scoring
Listing 3.4. The explain() method

![l3.4](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/088fig01_alt.jpg)

![l3.4-1](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/089fig01.jpg)

## LUCENE’S DIVERSE QUERIES
### Searching by term: TermQuery
```java
public void testKeyword() throws Exception {
  Directory dir = TestUtil.getBookIndexDirectory();
  IndexSearcher searcher = new IndexSearcher(dir);

  Term t = new Term("isbn", "9781935182023");
  Query query = new TermQuery(t);
  TopDocs docs = searcher.search(query, 10);
  assertEquals("JUnit in Action, Second Edition",
               1, docs.totalHits);

  searcher.close();
  dir.close();
}
```

### Searching within a term range: TermRangeQuery
```java
public void testTermRangeQuery() throws Exception {
  Directory dir = TestUtil.getBookIndexDirectory();
  IndexSearcher searcher = new IndexSearcher(dir);
  TermRangeQuery query = new TermRangeQuery("title2", "d", "j",
                                            true, true);
  TopDocs matches = searcher.search(query, 100);
  assertEquals(3, matches.totalHits);
  searcher.close();
  dir.close();
}
```

### Searching within a numeric range: NumericRangeQuery
```java
public void testInclusive() throws Exception {
  Directory dir = TestUtil.getBookIndexDirectory();
  IndexSearcher searcher = new IndexSearcher(dir);
  // pub date of TTC was September 2006
  NumericRangeQuery query = NumericRangeQuery.newIntRange("pubmonth",
                                                          200605,
                                                          200609,
                                                          true,
                                                          true);

  TopDocs matches = searcher.search(query, 10);
  assertEquals(1, matches.totalHits);
  searcher.close();
  dir.close();
}

public void testExclusive() throws Exception {
  Directory dir = TestUtil.getBookIndexDirectory();
  IndexSearcher searcher = new IndexSearcher(dir);

  // pub date of TTC was September 2006
  NumericRangeQuery query = NumericRangeQuery.newIntRange("pubmonth",
                                                          200605,
                                                          200609,
                                                          false,
                                                          false);
  TopDocs matches = searcher.search(query, 10);
  assertEquals(0, matches.totalHits);
  searcher.close();
  dir.close();
}
```

### Searching on a string: PrefixQuery
Listing 3.5. PrefixQuery

![l3.5](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/093fig01_alt.jpg)

### Combining queries: BooleanQuery
Listing 3.6. Using BooleanQuery to combine required subqueries

![l3.6](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/094fig01_alt.jpg)

```java
public static boolean hitsIncludeTitle(IndexSearcher searcher,
                                       TopDocs hits, String title)
  throws IOException {
  for (ScoreDoc match : hits.scoreDocs) {
    Document doc = searcher.doc(match.doc);
    if (title.equals(doc.get("title"))) {
      return true;
    }
  }
  System.out.println("title '" + title + "' not found");
  return false;
}
```

Listing 3.7. Using BooleanQuery to combine optional subqueries.

![l3.7](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/095fig01_alt.jpg)

### Searching by phrase: PhraseQuery
Listing 3.8. PhraseQuery

![l3.8](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/096fig01_alt.jpg)

### Searching by wildcard: WildcardQuery
Listing 3.9. WildcardQuery

![l3.9](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/099fig01_alt.jpg)

### Searching for similar terms: FuzzyQuery
```java
public void testFuzzy() throws Exception {
  indexSingleFieldDocs(new Field[] { new Field("contents",
                                               "fuzzy",
                                               Field.Store.YES,
                                               Field.Index.ANALYZED),
                                     new Field("contents",
                                               "wuzzy",
                                               Field.Store.YES,
                                               Field.Index.ANALYZED)
                                   });

  IndexSearcher searcher = new IndexSearcher(directory);
  Query query = new FuzzyQuery(new Term("contents", "wuzza"));
  TopDocs matches = searcher.search(query, 10);
  assertEquals("both close enough", 2, matches.totalHits);

  assertTrue("wuzzy closer than fuzzy",
             matches.scoreDocs[0].score != matches.scoreDocs[1].score);

  Document doc = searcher.doc(matches.scoreDocs[0].doc);
  assertEquals("wuzza bear", "wuzzy", doc.get("contents"));
  searcher.close();
}
```

### Matching all documents: MatchAllDocsQuery
```java
Query query = new MatchAllDocsQuery(field);
```

## PARSING QUERY EXPRESSIONS: QUERYPARSER
### Query.toString
```java
public void testToString() throws Exception {
  BooleanQuery query = new BooleanQuery();
  query.add(new FuzzyQuery(new Term("field", "kountry")),
            BooleanClause.Occur.MUST);
  query.add(new TermQuery(new Term("title", "western")),
            BooleanClause.Occur.SHOULD);
  assertEquals("both kinds", "+kountry~0.5 title:western",
               query.toString("field"));
}
```

### TermQuery
```java
public void testTermQuery() throws Exception {
  QueryParser parser = new QueryParser(Version.LUCENE_30,
                                       "subject", analyzer);
  Query query = parser.parse("computers");
  System.out.println("term: " + query);
}
```

produces this output:

```
term: subject:computers
```

### Term range searches
Listing 3.10. Creating a TermRangeQuery using QueryParser

![l310](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/103fig01_alt.jpg)

### Numeric and date range searches
QueryParser does include certain built-in logic for parsing dates when they appear as part of a range query, but the logic doesn’t work when you’ve indexed your dates using NumericField.

### Prefix and wildcard queries
```java
public void testLowercasing() throws Exception {
  Query q = new QueryParser(Version.LUCENE_30,
          "field", analyzer).parse("PrefixQuery*");
  assertEquals("lowercased",
      "prefixquery*", q.toString("field"));

  QueryParser qp = new QueryParser(Version.LUCENE_30,
                                   "field", analyzer);
  qp.setLowercaseExpandedTerms(false);
  q = qp.parse("PrefixQuery*");
  assertEquals("not lowercased",
      "PrefixQuery*", q.toString("field"));
}
```

### Boolean operators
```java
QueryParser parser = new QueryParser(Version.LUCENE_30,
                                     "contents", analyzer);
parser.setDefaultOperator(QueryParser.AND_OPERATOR);
```

Table 3.6. Boolean query operator shortcuts

| Verbose syntax | Shortcut syntax |
| --- | --- |
| a AND b	| +a +b |
| a OR b | a b |
| a AND NOT b | +a –b |

### Phrase queries
```java
public void testPhraseQuery() throws Exception {
  Query q = new QueryParser(Version.LUCENE_30,
                            "field",
                            new StandardAnalyzer(
                              Version.LUCENE_30))
                .parse("\"This is Some Phrase*\"");

  assertEquals("analyzed",
      "\"? ? some phrase\"", q.toString("field"));

  q = new QueryParser(Version.LUCENE_30,
                      "field", analyzer)
                .parse("\"term\"");
  assertTrue("reduced to TermQuery", q instanceof TermQuery);
}

public void testSlop() throws Exception {
  Query q = new QueryParser(Version.LUCENE_30,
       "field", analyzer)
          .parse("\"exact phrase\"");
  assertEquals("zero slop",
      "\"exact phrase\"", q.toString("field"));

  QueryParser qp = new QueryParser(Version.LUCENE_30,
                                   "field", analyzer);
  qp.setPhraseSlop(5);
  q = qp.parse("\"sloppy phrase\"");
  assertEquals("sloppy, implicitly",
      "\"sloppy phrase\"~5", q.toString("field"));
}
```

### Fuzzy queries
```java
public void testFuzzyQuery() throws Exception {
  QueryParser parser = new QueryParser(Version.LUCENE_30,
                                       "subject", analyzer);
  Query query = parser.parse("kountry~");
  System.out.println("fuzzy: " + query);

  query = parser.parse("kountry~0.7");
  System.out.println("fuzzy 2: " + query);
}
```

This produces the following output:

```
fuzzy: subject:kountry~0.5
fuzzy 2: subject:kountry~0.7
```

### MatchAllDocsQuery
QueryParser produces the MatchAllDocsQuery when you enter `*:*`.

### Grouping
```java
public void testGrouping() throws Exception {
  Query query = new QueryParser(
      Version.LUCENE_30,
      "subject",
      analyzer).parse("(agile OR extreme) AND methodology");
  TopDocs matches = searcher.search(query, 10);

  assertTrue(TestUtil.hitsIncludeTitle(searcher, matches,
                                       "Extreme Programming Explained"));
  assertTrue(TestUtil.hitsIncludeTitle(searcher,
                                       matches,
                                       "The Pragmatic Programmer"));
}
```

Figure 3.7. A Query can have an arbitrary nested structure, easily expressed with QueryParser’s grouping. This query is achieved by parsing the expression (+"brown fox" +quick) "red dog".

![f3.7](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/03fig07_alt.jpg)

### Setting the boost for a subquery
A caret (^) followed by a floating-point number sets the boost factor for the preceding query. For example, the query expression junit^2.0 testing sets the junit TermQuery to a boost of 2.0 and leaves the testing TermQuery at the default boost of 1.0. 

# Lucene’s analysis process
## USING ANALYZERS
```
Analyzing "The quick brown fox jumped over the lazy dog"
  WhitespaceAnalyzer:
    [The] [quick] [brown] [fox] [jumped] [over] [the] [lazy] [dog]

  SimpleAnalyzer:
    [the] [quick] [brown] [fox] [jumped] [over] [the] [lazy] [dog]

  StopAnalyzer:
    [quick] [brown] [fox] [jumped] [over] [lazy] [dog]

  StandardAnalyzer:
    [quick] [brown] [fox] [jumped] [over] [lazy] [dog]

Analyzing "XY&Z Corporation - xyz@example.com"
  WhitespaceAnalyzer:
    [XY&Z] [Corporation] [-] [xyz@example.com]

  SimpleAnalyzer:
    [xy] [z] [corporation] [xyz] [example] [com]

  StopAnalyzer:
    [xy] [z] [corporation] [xyz] [example] [com]

  StandardAnalyzer:
    [xy&z] [corporation] [xyz@example.com]
```

In the meantime, here’s a summary of each of these analyzers:

- `WhitespaceAnalyzer`, as the name implies, splits text into tokens on whitespace characters and makes no other effort to normalize the tokens. It doesn’t lowercase each token.
- `SimpleAnalyzer` first splits tokens at nonletter characters, then lowercases each token. Be careful! This analyzer quietly discards numeric characters but keeps all other characters.
- `StopAnalyzer` is the same as SimpleAnalyzer, except it removes common words. By default, it removes common words specific to the English language (the, a, etc.), though you can pass in your own set.
- `StandardAnalyzer` is Lucene’s most sophisticated core analyzer. It has quite a bit of logic to identify certain kinds of tokens, such as company names, email addresses, and hostnames. It also lowercases each token and removes stop words and punctuation.

### Indexing analysis
Figure 4.1. Analysis process during indexing. Fields 1 and 2 are analyzed, producing a sequence of tokens; Field 3 is unanalyzed, causing its entire value to be indexed as a single token.

![f4.1](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/04fig01.jpg)

### QueryParser analysis
```java
QueryParser parser = new QueryParser(Version.LUCENE_30,
                                     "contents", analyzer);
Query query = parser.parse(expression);
```

### Parsing vs. analysis: when an analyzer isn’t appropriate
- Analyzers are used to analyze a specific field at a time and break things into tokens only within that field.
- Analyzers don’t help in field separation because their scope is to deal with a single field at a time. Instead, parsing these documents prior to analysis is required.

## WHAT’S INSIDE AN ANALYZER?
```java
public final class SimpleAnalyzer extends Analyzer {
  @Override
  public TokenStream tokenStream(String fieldName, Reader reader) {
    return new LowerCaseTokenizer(reader);
  }

  @Override
  public TokenStream reusableTokenStream(String fieldName, Reader reader
       throws IOException {
    Tokenizer tokenizer = (Tokenizer) getPreviousTokenStream();
    if (tokenizer == null) {
      tokenizer = new LowerCaseTokenizer(reader);
      setPreviousTokenStream(tokenizer);
    } else
      tokenizer.reset(reader);
    return tokenizer;
  }
}
```

### What’s in a token?
Figure 4.2. A token stream with positional and offset information

![f4.2](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/04fig02.jpg)

### TokenStream uncensored
Figure 4.3. The hierarchy of classes used to produce tokens: TokenStream is the abstract base class; Tokenizer creates tokens from a Reader; and TokenFilter filters any other TokenStream.

![f4.3](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/04fig03.jpg)

Figure 4.4. An analyzer chain starts with a Tokenizer, to produce initial tokens from the characters read from a Reader, then modifies the tokens with any number of chained TokenFilters.

![f4.4](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/04fig04.jpg)

Figure 4.5. TokenFilter and Tokenizer class hierarchy

![f4.5](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/04fig05_alt.jpg)

To illustrate the analyzer chain in code, here’s a simple example analyzer:

```java
public TokenStream tokenStream(String fieldName, Reader reader) {
    return new StopFilter(true,
                          new LowerCaseTokenizer(reader),
                          stopWords);
}
```

### Visualizing analyzers
Listing 4.1. AnalyzerDemo: seeing analysis in action

![l4.1](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/120fig01_alt.jpg)

Listing 4.2. AnalyzerUtils: delving into an analyzer

![l4.2](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/121fig01_alt.jpg)

The AnalyzerDemo application lets you specify one or more strings from the command line to be analyzed instead of the embedded example ones:

```
%java lia.analysis.AnalyzerDemo "No Fluff, Just Stuff"

Analyzing "No Fluff, Just Stuff"
  org.apache.lucene.analysis.WhitespaceAnalyzer:
    [No] [Fluff,] [Just] [Stuff]

  org.apache.lucene.analysis.SimpleAnalyzer:
    [no] [fluff] [just] [stuff]

  org.apache.lucene.analysis.StopAnalyzer:
    [fluff] [just] [stuff]

  org.apache.lucene.analysis.standard.StandardAnalyzer:
    [fluff] [just] [stuff]
```

Listing 4.3. Seeing the term, offsets, type, and position increment of each token

![l4.3](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/122fig01_alt.jpg)

We display all token information on the example phrase using SimpleAnalyzer:

```java
public static void main(String[] args) throws IOException {
  AnalyzerUtils.displayTokensWithFullDetails(new SimpleAnalyzer(),
      "The quick brown fox....");
}
```

Here’s the output:

```
1: [the:0->3:word]
2: [quick:4->9:word]
3: [brown:10->15:word]
4: [fox:16->19:word]
```

Analyzing the phrase “I’ll email you at xyz@example.com” with `StandardAnalyzer` produces this interesting output:

```
1: [i'll:0->4:<APOSTROPHE>]
2: [email:5->10:<ALPHANUM>]
3: [you:11->14:<ALPHANUM>]
5: [xyz@example.com:18->33:<EMAIL>]
```

## USING THE BUILT-IN ANALYZERS
Table 4.3. Primary analyzers available in Lucene

| Analyzer | Steps taken |
| --- | --- |
| WhitespaceAnalyzer | Splits tokens at whitespace.|
| SimpleAnalyzer | Divides text at nonletter characters and lowercases.|
| StopAnalyzer | Divides text at nonletter characters, lowercases, and removes stop words.|
| KeywordAnalyzer | Treats entire text as a single token.|
| StandardAnalyzer | Tokenizes based on a sophisticated grammar that recognizes email addresses, acronyms, Chinese-Japanese-Korean characters, alphanumerics, and more. It also lowercases and removes stop words.|

## SOUNDS-LIKE QUERYING
We chose the `Metaphone` algorithm as an example, but other algorithms are available, such as `Soundex`.

Listing 4.4. Searching for words that sound like one another

![l4.4](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/129fig01_alt.jpg)

The trick lies in the MetaphoneReplacementAnalyzer:

```java
public class MetaphoneReplacementAnalyzer extends Analyzer {
  public TokenStream tokenStream(String fieldName, Reader reader) {
    return new MetaphoneReplacementFilter(
                   new LetterTokenizer(reader));
  }
}
```

Listing 4.5. TokenFilter that replaces tokens with their metaphone equivalents

![l4.5](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/130fig01_alt.jpg)

Using our AnalyzerUtils, two phrases that sound similar yet are spelled differently are tokenized and displayed:

```java
public static void main(String[] args) throws IOException {
  MetaphoneReplacementAnalyzer analyzer =
                               new MetaphoneReplacementAnalyzer();
  AnalyzerUtils.displayTokens(analyzer,
                 "The quick brown fox jumped over the lazy dog");

  System.out.println("");
  AnalyzerUtils.displayTokens(analyzer,
                 "Tha quik brown phox jumpd ovvar tha lazi dag");
}
```

We get a sample of the metaphone encoder, shown here:

```
[0] [KK] [BRN] [FKS] [JMPT] [OFR] [0] [LS] [TKS]
[0] [KK] [BRN] [FKS] [JMPT] [OFR] [0] [LS] [TKS]
```

## SYNONYMS, ALIASES, AND WORDS THAT MEAN THE SAME
Listing 4.6. Testing the synonym analyzer

![l4.6](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/131fig01_alt.jpg)

### Creating SynonymAnalyzer
Listing 4.7. SynonymAnalyzer implementation

```java
public class SynonymAnalyzer extends Analyzer {
  private SynonymEngine engine;

  public SynonymAnalyzer(SynonymEngine engine) {
    this.engine = engine;
  }

  public TokenStream tokenStream(String fieldName, Reader reader) {
    TokenStream result = new SynonymFilter(
                          new StopFilter(true,
                            new LowerCaseFilter(
                              new StandardFilter(
                                new StandardTokenizer(
                                 Version.LUCENE_30, reader))),
                            StopAnalyzer.ENGLISH_STOP_WORDS_SET),
                          engine
                         );
    return result;
  }
}
```

Listing 4.8. SynonymFilter: buffering tokens and emitting one at a time

![l4.8](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/ch04ex08-0.jpg)

The design of SynonymAnalyzer allows for pluggable SynonymEngine implementations. SynonymEngine is a one-method interface:

```java
public interface SynonymEngine {
  String[] getSynonyms(String s) throws IOException;
}

public class TestSynonymEngine implements SynonymEngine {
  private static HashMap<String, String[]> map =

    new HashMap<String, String[]>();

  static {
    map.put("quick", new String[] {"fast", "speedy"});
    map.put("jumps", new String[] {"leaps", "hops"});
    map.put("over", new String[] {"above"});
    map.put("lazy", new String[] {"apathetic", "sluggish"});
    map.put("dog", new String[] {"canine", "pooch"});
  }
  public String[] getSynonyms(String s) {
    return map.get(s);
  }
}
```

Listing 4.9. SynonymAnalyzerTest: showing that synonym queries work

![l4.9](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/ch04ex09-0.jpg)
![l4.9-1](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/ch04ex09-1.jpg)

Listing 4.10. Testing SynonymAnalyzer with QueryParser

![l4.10](https://www.safaribooksonline.com/library/view/lucene-in-action/9781933988177/136fig01_alt.jpg)

The test produces the following output:

```
With SynonymAnalyzer, "fox jumps" parses to "fox (jumps hops leaps)"
With StandardAnalyzer, "fox jumps" parses to "fox jumps"
```

### Visualizing token positions
Listing 4.11. Visualizing the position increment of each token

```java
public static void displayTokensWithPositions
  (Analyzer analyzer, String text) throws IOException {

  TokenStream stream = analyzer.tokenStream("contents",
                                            new StringReader(text));
  TermAttribute term = stream.addAttribute(TermAttribute.class);
  PositionIncrementAttribute posIncr =
       stream.addAttribute(PositionIncrementAttribute.class);

  int position = 0;
  while(stream.incrementToken()) {
    int increment = posIncr.getPositionIncrement();
    if (increment > 0) {
      position = position + increment;
      System.out.println();
      System.out.print(position + ": ");
    }

    System.out.print("[" + term.term() + "] ");
  }
  System.out.println();
}
```

We wrote a quick piece of code to see what our SynonymAnalyzer is doing:

```java
public class SynonymAnalyzerViewer {

  public static void main(String[] args) throws IOException {

  SynonymEngine engine = new TestSynonymEngine();

  AnalyzerUtils.displayTokensWithPositions(
    new SynonymAnalyzer(engine),
    "The quick brown fox jumps over the lazy dog");
  }
}
```

And we can now visualize the synonyms placed in the same positions as the original words:

```
2: [quick] [speedy] [fast]
3: [brown]
4: [fox]
5: [jumps] [hops] [leaps]
6: [over] [above]
8: [lazy] [sluggish] [apathetic]
9: [dog] [pooch] [canine]
```

## STEMMING ANALYSIS
### StopFilter leaves holes
This is illustrated from the output of AnalyzerUtils.displayTokensWithPositions:

```
2: [quick]
3: [brown]
4: [fox]
5: [jump]
6: [over]
8: [lazi]
9: [dog]
```

### Combining stemming and stop-word removal
Listing 4.12. PositionalPorterStopAnalyzer: stemming and stop word removal

```java
public class PositionalPorterStopAnalyzer extends Analyzer {
  private Set stopWords;

  public PositionalPorterStopAnalyzer() {
    this(StopAnalyzer.ENGLISH_STOP_WORDS_SET);
  }

  public PositionalPorterStopAnalyzer(Set stopWords) {
    this.stopWords = stopWords;
  }

  public TokenStream tokenStream(String fieldName, Reader reader) {
    StopFilter stopFilter = new StopFilter(true,
                                           new LowerCaseTokenizer(reader),
                                           stopWords);
    stopFilter.setEnablePositionIncrements(true);
    return new PorterStemFilter(stopFilter);
  }
}
```




















