![cover](https://img3.doubanio.com/view/subject/s/public/s28854701.jpg)

    作者: Doug Turnbull / John Berryman
    出版社: Manning Publications
    副标题: With applications for Solr and Elasticsearch
    出版年: 2016-7-31
    页数: 360
    定价: USD 44.99
    装帧: Paperback
    ISBN: 9781617292774

- [豆瓣](https://book.douban.com/subject/26827294/)
- [oreilly](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/)

---

- [1.The search relevance problem](#1the-search-relevance-problem)
  - [1.1.Your goal: gaining the skills of a relevance engineer](#11your-goal-gaining-the-skills-of-a-relevance-engineer)
  - [1.3.Gaining insight from relevance research](#13gaining-insight-from-relevance-research)
    - [1.3.1.Information retrieval](#131information-retrieval)
    - [1.3.2.Can we use information retrieval to solve relevance?](#132can-we-use-information-retrieval-to-solve-relevance)
  - [1.4.How do you solve relevance?](#14how-do-you-solve-relevance)
- [2.Search—under the hood](#2searchunder-the-hood)
  - [2.1.Search 101](#21search-101)
    - [2.1.1.What’s a search document?](#211whats-a-search-document)
    - [2.1.2.Searching the content](#212searching-the-content)
    - [2.1.3.Exploring content through search](#213exploring-content-through-search)
    - [2.1.4.Getting content into the search engine](#214getting-content-into-the-search-engine)
  - [2.2.Search engine data structures](#22search-engine-data-structures)
    - [2.2.1.The inverted index](#221the-inverted-index)
    - [2.2.2.Other pieces of the inverted index](#222other-pieces-of-the-inverted-index)
  - [2.3.Indexing content: extraction, enrichment, analysis, and indexing](#23indexing-content-extraction-enrichment-analysis-and-indexing)
    - [2.3.1.Extracting content into documents](#231extracting-content-into-documents)
    - [2.3.2.Enriching documents to clean, augment, and merge data](#232enriching-documents-to-clean-augment-and-merge-data)
    - [2.3.3.Performing analysis](#233performing-analysis)
      - [Tokens as search features](#tokens-as-search-features)
      - [Components of analysis](#components-of-analysis)
    - [2.3.4.Indexing](#234indexing)
- [3.Debugging your first relevance problem](#3debugging-your-first-relevance-problem)

# 1.The search relevance problem
## 1.1.Your goal: gaining the skills of a relevance engineer
A `relevance engineer` transforms the search engine into a seemingly smart system that understands the needs of users and the business. 

These search-time ranking factors that measure what users care about are called `signals`.

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/01fig01_alt.jpg)

Figure 1.1. The relevance engineer works with the search engine and back-end technologies to express business-ranking logic. They collaborate on relevance closely with a cross-functional team and are informed heavily by user metrics.

## 1.3.Gaining insight from relevance research
### 1.3.1.Information retrieval
In information retrieval, `relevance` is defined as the practice of returning search results that most satisfy the user’s information needs.

These annotated lists of search results that are relevant with respect to a set of queries are known as `judgment` lists (see figure 1.3).

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/01fig03_alt.jpg)

Figure 1.3. Example of making a relevance judgment for the query “Rambo” in Quepid, a judgment list management application

### 1.3.2.Can we use information retrieval to solve relevance?
In fact, before we move on, let’s refine our definition of `relevance` to what it takes to solve an applied relevance problem:

>Relevance is the practice of improving search results for users by satisfying their information needs in the context of a particular user experience, while balancing how ranking impacts our business’s needs.

## 1.4.How do you solve relevance?
To solve relevance, the relevance engineer:

1. Identifies salient `features` describing the content, the user, or the search query
2. Finds a way to tell the search engine about those features through extraction and enrichment
3. At search time, measures what’s relevant to a user’s search by crafting `signals`
4. Carefully balances the influence of multiple signals to rank results by manipulating the ranking function

This process is shown in figure 1.4.

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/01fig04_alt.jpg)

Figure 1.4. Relevance engineers select, enrich, or create important features from back-end systems and express ranking signals in terms of those features.

A `feature` is an attribute of the content or query. Features drive decisions. Much of the engineering work in search relevance is in `feature selection`—the act of discovering and generating features that give us the appropriate information when a user searches.

`Signals` measure whether items are relevant for a given search (using features, of course!). It’s rare to have only one signal that measures relevance. More often, multiple signals combine to rank search results in         the search engine’s `ranking function`.

# 2.Search—under the hood
## 2.1.Search 101
![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/02fig01_alt.jpg)

Figure 2.1. A simple model of a search engine based on possible interactions

### 2.1.1.What’s a search document?
In search applications, the notion of a `document` is central, because documents are items being stored, searched, and returned.

Unlike an SQL table, every document can contain different fields. The fields in one document can be different from the fields in another.

### 2.1.2.Searching the content
![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/02fig02_alt.jpg)

Figure 2.2. Typical search user interface and response page                  

### 2.1.3.Exploring content through search
Front and center, as illustrated in figure 2.2, the search engine provides users with a list of **matching** documents.

Instead of the field values, search engines often return summarized `snippets` that highlight the part that matches. These highlighted snippets (highlights, for short) convey exactly why a document is a match for the user’s search.

As illustrated in figure 2.2, this aggregate information is often presented in a sidebar as a set of filters also known as `facets`.

### 2.1.4.Getting content into the search engine
![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/02fig03.jpg)

Figure 2.3. “Barcelona Beaches” article indexed and analyzed (only title-field analysis shown)                              

Analysis converts the field values (usually text) into elements called `tokens`.

After analysis is complete, the documents are `indexed`; the tokens from the analysis step are stored into search engine data structures for document retrieval. In addition, the original, untokenized text fields are stored so that they can be presented back to the user in search results.

## 2.2.Search engine data structures
### 2.2.1.The inverted index
![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/02fig04_alt.jpg)

Figure 2.4. The inverted index data structure used by search engines closely resembles the index that you can find in the back of a textbook.

An `inverted index` is composed of two main pieces: a `term dictionary` and a postings list. The term dictionary is a sorted list of all terms that occur in a given field across a set of documents. For each term in the dictionary, there’s a corresponding list of documents that contain that term.

Consider the set of documents shown in the following listing.

```
0. One shoe, two shoe, the red shoe, the blue shoe.
1. The blue dress shoe is the best shoe.
2. The best dress is the one red dress.
```

Listing 2.1. Documents

The term dictionary and postings list for this simple set of documents are presented in the following two listings, respectively.

```
best  → 0
blue  → 1
dress → 2
is    → 3
one   → 4
red   → 5
shoe  → 6
the   → 7
two   → 8
```

Listing 2.2. Term dictionary

```
0 → [1,2]
1 → [0,1]
2 → [1,2]
3 → [1,2]
4 → [0,2]
5 → [0,2]
6 → [0,1]
7 → [0,1,2]
8 → [0]
```

Listing 2.3. Postings list

### 2.2.2.Other pieces of the inverted index
Table 2.1. Important pieces of data associated with the inverted index

Name | Description
--- | ---
Doc frequency | A count of documents that contain a particular term, or the length of the postings associated with a particular term. In listing 2.3, the doc frequency for the term “shoe” is 2 because it occurs in documents 0 and 1. Doc frequency is useful in document scoring because it establishes a notion of importance for a particular term. For instance, the term “the” typically has a high document frequency, which indicates that it carries little discriminatory value when determining the relevancy of a document for a given search.
Term frequency | The number of times that a term occurs in a particular document. In listing 2.3, the term frequency for “shoe” in document 0 is 4, and the term frequency for “shoe” in document 1 is 2. Term frequency is  useful in document scoring because it establishes a notion of how important a document is for a given term. So, loosely speaking, if someone searches for “shoe”, document 0 can be considered twice as important as document 1 because “shoe” occurs twice as often in document 0.
Term positions | Word position is often important for search. Consider the semantic difference between a query for “dress AND shoes” and a query for “dress shoes.” Term positions are a list of numbers indicating where a term occurs within a particular document. For instance, the term positions for “shoe” in document 0 from our example would be 1, 3, 6, 9. Term positions make it possible to find documents based on phrase matches so that a search for “dress shoes” will give users exactly what they’re looking for.
Term offsets | One of the best ways to provide search users with feedback about why a particular document matches a query is to present them with highlighted snippets of the matching text. But reanalyzing the original text to extract highlights is often slow. The fastest way to highlight snippets is to keep track of the start and end character offsets of the terms when they’re first analyzed during indexing. Then, at search “time” all that needs to be done is to insert the appropriate tags at the corresponding offsets.
Payloads | Each term in the index can be associated with arbitrary data. One common example is to tag a token with its part of speech and use this in relevance scoring. Another common example is to associate an externally generated score with a token (this mention of “Barcelona” ought to be scored as 100, this other “Barcelona” mention a 59).
Stored fields | Information stored in an inverted index is useful for searching, but this information is a rather scrambled version of the original document. Any fields are to be presented back to the user or must be saved separately in stored fields. These stored fields can take up a lot of disk space. For this reason, many search developers avoid storing data directly in the search engine, instead retrieving display fields from the source system.
Doc values | It’s common to incorporate auxiliary values into the relevance-scoring heuristic. For instance, an e-commerce search might boost catalog items that are on clearance or that have a high profit margin. It’s also common to allow users to sort search results by a metric such as price or popularity. The doc values data structure allows for quick access to these auxiliary values and is useful when sorting, scoring, and grouping documents.

## 2.3.Indexing content: extraction, enrichment, analysis, and indexing
![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/02fig05.jpg)

Figure 2.5. The full search ETL pipeline: extraction, enrichment, analysis, and indexing

- `Extraction` is the process of retrieving the documents from their sources.
- The optional step of `enrichment` adds information to the documents useful for relevance.
- `Analysis`, as you saw earlier in this chapter, converts document text or data into tokens that enable matching.
- `Indexing` is the process of placing data into those data structures.

### 2.3.1.Extracting content into documents
A `document` may be exactly like the document described in section 2.1.1, **a collection of typed fields that contain various values**. Or, for search engines such as Elasticsearch, these can be complex hierarchical documents represented as `JSON`.

### 2.3.2.Enriching documents to clean, augment, and merge data
Document enrichment comprises three main categories: cleaning data, augmenting existing data, and merging external data.

- First, `cleaning`. If you want a top-notch search experience, it’s usually well worth the time to parse through documents, look for silly mistakes such as misspellings and document duplications, and correct them.
- Second, often the existing data can be post-processed to `augment` the features already there. For instance, machine-learning techniques can be used to classify or cluster documents. Or sentiment analysis can be used to determine whether the text in a document is more positive or negative in tone.
- Finally, new information can be merged into the documents from `external sources`. For instance, in e-commerce the products being sold often come from external vendors. Product data provided by the vendors can be sparse—for instance, missing important fields such as the product title. In this case, additional information can be joined into the documents. The existing product codes can be used to look up product titles, or missing descriptions can be written in by hand. 

### 2.3.3.Performing analysis
`Tokens` are symbols that represent the content of a field in a document. 

```
The, Brown’s, fiftieth, wedding, anniversary, at, Café, Olé
```

Listing 2.4. Text tokenization example

```
brown, fiftieth, wedding, anniversary, cafe, ole
```

Listing 2.5. Text tokenization example with normalization and filtering

Geographic locations(for instance, the location of the White House, 38.8977° N, 77.0366° W) can be tokenized using geohashing. In this case, reasonable tokens might be as follows.

```
dqcjqcpee, dqcjqcpe, dqcjqcp, dqcjqc, dqcjq, dqcj, dqc, dq, d
```

Listing 2.6. Geolocation tokenization using geohashing

#### Tokens as search features
The `tokens` that come from the analysis process serve as the `features` that describe the document.

#### Components of analysis
Analysis is composed of three steps: `character filtering`, `tokenization`, and `token filtering`.

During the first step, `character filtering`, the characters of text fields can be adjusted or filtered in various ways.

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/02fig06.jpg)

Figure 2.6. Analysis—character filtering

The next step is `tokenization`, during this step raw text is converted into a stream of tokens.

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/02fig07.jpg)

Figure 2.7. Analysis—tokenizing

The final step is `token filtering`.

In order to appropriately normalize the tokens from our sample sentence, a typical choice would be to lowercase the tokens, remove common words such as the and at (these common words are called `stop words`), and remove the possessive after Brown

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/02fig08.jpg)

Figure 2.8. Analysis—token filtering

One final note before we move on to indexing. During analysis, it’s common to store extra metadata with each token that the analysis process generates. The most common metadata are the `term positions` and `term offsets`, which are useful for phrase queries and highlighting, respectively. You can also create custom token filters that add arbitrary metadata to the tokens in values called `payloads`.

### 2.3.4.Indexing
Most importantly, you must decide which fields to index and/or store which fields to index and/or store, and which fields to both index and store.

- `Indexing` refers to the process of updating the inverted index with the extracted tokens to enable search on that field. A field is searchable only if it’s indexed.
- `Storing` refers to retaining the original, unaltered document content in the stored field’s data structure (see table 2.1) so that it can be retrieved and presented to the user in search results. 

# 3.Debugging your first relevance problem



















































