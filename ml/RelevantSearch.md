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
  - [3.1.Applications to Solr and Elasticsearch: examples in Elasticsearch](#31applications-to-solr-and-elasticsearch-examples-in-elasticsearch)
  - [3.2.Our most prominent data set: TMDB](#32our-most-prominent-data-set-tmdb)
  - [3.3.Examples programmed in Python](#33examples-programmed-in-python)
  - [3.4.Your first search application](#34your-first-search-application)
    - [3.4.1.Your first searches of the TMDB Elasticsearch index](#341your-first-searches-of-the-tmdb-elasticsearch-index)
  - [3.5.Debugging query matching](#35debugging-query-matching)
    - [3.5.1.Examining the underlying query strategy](#351examining-the-underlying-query-strategy)
    - [3.5.2.Taking apart query parsing](#352taking-apart-query-parsing)
    - [3.5.3.Debugging analysis to solve matching issues](#353debugging-analysis-to-solve-matching-issues)
    - [3.5.4.Comparing your query to the inverted index](#354comparing-your-query-to-the-inverted-index)
    - [3.5.5.Fixing our matching by changing analyzers](#355fixing-our-matching-by-changing-analyzers)
  - [3.6.Debugging ranking](#36debugging-ranking)
    - [3.6.1.Decomposing the relevance score with Lucene’s explain feature](#361decomposing-the-relevance-score-with-lucenes-explain-feature)

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

The `term dictionary` and `postings list` for this simple set of documents are presented in the following two listings, respectively.

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
You’ll begin to use our search engine, Elasticsearch, to search over a real data set. As you encounter the common beginner’s problem, your focus will be on debugging two primary internal layers key to relevance: `matching` and `ranking`.

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/03fig01_alt.jpg)

Figure 3.1. As a relevance engineer, you have several tools available for debugging relevance problems.

## 3.1.Applications to Solr and Elasticsearch: examples in Elasticsearch
It’s important to note that this book isn’t about Elasticsearch. We focus on features related to relevance, completely ignoring other features and concerns when using a search engine: analytics, ingesting your data, scaling, and performance.

## 3.2.Our most prominent data set: TMDB
We’re excited about [TMDB](http://themoviedb.org/)’s data, as its content contains several attributes that many search applications must work with. When searching movies, these attributes include:

- Prose text (including overviews, synopsis, and user reviews)
- Shorter text (such as director and actor names, and titles)
- Numerical attributes (user ratings, movie revenue, number of awards)
- Movie release dates and other attributes important in search

In this book, you’ll primarily use a prepackaged version of TMDB data. Packaged with the book’s GitHub [repository](http://github.com/o19s/relevant-search-book) is a file containing a snapshot of TMDB movies used at the time of writing this book.

## 3.3.Examples programmed in Python
 This code imports requests (an HTTP client library) and Python’s JSON standard library:

```py
import requests # requests HTTP library
import json # json parsing
```

## 3.4.Your first search application
To index movies, first you need to read them in! To access tmdb.json with the movie dictionary, you’ll use a function called `extract`. In the following listing, you’ll pull back each movie by parsing the JSON file into a Python dictionary.

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/043fig01_alt.jpg)

Listing 3.1. Extract movies from tmdb.json

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/044fig01_alt.jpg)

Listing 3.2. Sample TMDB movie from tmdb.json

You’ll predominantly use the `bulk index` API that allows you to efficiently index multiple documents in one HTTP request.

That being said, let’s create a function, `reindex`, that you can refer to. The reindex function takes settings and the movieDict dictionary returned from extract, re-creates the Elasticsearch index, and indexes the data into Elasticsearch.

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/044fig02_alt.jpg)

Listing 3.3. Indexing with Elasticsearch’s bulk API—reindex

```py
movieDict = extract()
reindex(movieDict=movieDict)
```

Listing 3.4. Pulling data from TMDB into Elasticsearch

You’ve built your first ETL (extract, transform, load) pipeline. Here you’ve done the following:

- Extracted information from an external system
- Transformed the data into a form amenable to the search engine
- Indexed the data into Elasticsearch

### 3.4.1.Your first searches of the TMDB Elasticsearch index
Let’s implement a `search` function that lets you search with passed-in Query DSL queries. search is a fairly straightforward function that passes a query and prints the search results in order of relevance, as shown in the following listing.

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/046fig01_alt.jpg)

Listing 3.5. The search function

In listing 3.6, you construct a Query DSL search using `multi_match`. You attempt to tell Elasticsearch that a title field is 10 times more important than the overview field when ranking . 

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/047fig01_alt.jpg)

Listing 3.6. Your first search

Output:

```
Num  Relevance Score     Movie Title
1    0.8424165           Aliens
2    0.5603433           The Basketball Diaries
3    0.52651036          Cowboys & Aliens
4    0.42120826          Aliens vs Predator: Requiem
5    0.42120826          Aliens in the Attic
6    0.42120826          Monsters vs Aliens
7    0.262869            Dances with Wolves
8    0.262869            Interview with the Vampire
9    0.262869            From Russia with Love
10   0.262869            Gone with the Wind
11   0.262869            Fire with Fire
```

Unfortunately,most of the top movies listed seem to be about basketball or aliens, but not both. Other movies seem to be completely unrelated to basketball or aliens, and we’re completely missing the mark. Where’s Space Jam? If you request additional results from Elasticsearch, you finally see your result:

```
43   0.016977157            Space Jam
```

You need to answer two main questions:

- Why did certain documents match query terms? Why did a movie such as Fire with Fire even match your query?
- Why did less relevant documents rank as highly as they did? Why is The Basketball Diaries ranked higher than our target Space Jam?

## 3.5.Debugging query matching
First, we’ll remind you of what we mean by `matching`. This exacting matching behavior points to two areas to take apart:

- `Query parsing` —How your Query DSL query translates into a matching strategy of specific terms to fields
- `Analysis` —The process of creating tokens from the query and document text

### 3.5.1.Examining the underlying query strategy
The first thing you’ll do to inspect matching behavior is ask Elasticsearch to explain how the query was parsed.

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/049fig01_alt.jpg)

Response:

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/049fig02_alt.jpg)

Listing 3.7. Explaining the behavior of your query

Your query is translated into a more precise syntax that gives deeper information about how Lucene will work with your Elasticsearch query:

```
((title:basketball title:with title:cartoon title:aliens)^10.0) | (overview:basketball overview:with overview:cartoon overview:aliens)
```

### 3.5.2.Taking apart query parsing
Above the innermost matches, you see four `SHOULD` clauses scored together (grouped with parentheses):

```
(title:basketball title:with title:cartoon title:aliens)
```

Boosted by a factor of 10 (as we’ve requested when searching), you have the following:

```
(title:basketball title:with title:cartoon title:aliens)^10
```

Compared to another query, with a maximum score taken (| symbol), you have this:

```
((title:basketball title:with title:cartoon title:aliens)^10.0) |(overview:basketball overview:with overview:cartoon overview:aliens)
```

### 3.5.3.Debugging analysis to solve matching issues
![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/051fig01_alt.jpg)

The result (in prettier YAML) is as follows:

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/051fig02.jpg)

Listing 3.8. Debugging analysis

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/052fig01.jpg)

Listing 3.9. SimpleText index representation for the term fire

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/053fig01.jpg)

Listing 3.10. View of title index with Fire with Fire terms highlighted

### 3.5.4.Comparing your query to the inverted index
You’re now prepared to compare your parsed query with the context of the inverted index. If you compare the parsed query

```
((title:basketball title:with title:cartoon title:aliens)^10.0) |(overview:basketball overview:with overview:cartoon overview:aliens)
```

against the inverted index snippet from the token stream for _Fire with Fire_, you see exactly where the match occurs:

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/053fig02.jpg)

The clause _title:with_ pulls in doc 0, _Fire with Fire_, from the inverted index.

### 3.5.5.Fixing our matching by changing analyzers
Elasticsearch has an analyzer that handles English text fairly well. It strings together character filters, a `tokenizer`, and token filters to normalize English to standard word forms. It can stem English terms to root forms (running -> run), and remove noise terms such as the, known as `stop words`. Lucky for us, with is one such stop word.

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/054fig01_alt.jpg)

Listing 3.11. Reindexing with the English analyzer

Let’s reanalyze Fire with Fire to see the results:

```py
resp = requests.get('http://localhost:9200/tmdb/_analyze?field=title&format=yaml', data="Fire with Fire")
```

Response:

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/055fig01.jpg)

Rerunning the query validation also shows a removal of with from the query:

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/055fig02_alt.jpg)

Further, because of more sophisticated analysis, stemming, and token normalization, you’re picking up other matches of alien that were missing.

```
Num  Relevance Score    Movie Title
1    1.0643067          Alien
2    1.0643067          Aliens
3    1.0643067          Alien3
4    1.0254613          The Basketball Diaries
5    0.66519165         Cowboys & Aliens
6    0.66519165         Aliens in the Attic
7    0.66519165         Alien: Resurrection
8    0.53215337         Aliens vs Predator: Requiem
9    0.53215337         AVP: Alien vs. Predator
10   0.53215337         Monsters vs Aliens
11   0.08334568         Space Jam
```

## 3.6.Debugging ranking
After resolving your matching issue, you’re still left wondering why movies like Alien, Aliens, and Basketball Diaries rank above Space Jam. None of these movies have basketball-playing aliens.

What you’ll see is that debugging ranking means understanding the following:

- The calculation of individual match scores
- How these match scores factor into the document’s overall relevance score

### 3.6.1.Decomposing the relevance score with Lucene’s explain feature
Lucene’s `explain` feature lets you decompose the calculation behind the relevance score.

![](https://learning.oreilly.com/library/view/relevant-search-with/9781617292774/058fig01_alt.jpg)

Listing 3.12. Requesting a relevancy scoring explanation

Without further ado, here’s a snippet of the JSON explain for _Alien_:

```json
{
"description": "max of:", 
"value": 1.0643067, 
"details": [
  {
  "description": "product of:",   
  "value": 1.0643067,   
  "details": [
    {
    "description": "sum of:",
    "value": 3.19292,
    "details": [
      {
      "description": "weight(title:alien in 223)[PerFieldSimilarity], result of:",
      "value": 3.19292,
      "details": [
        {
          "description": "score(doc=223,freq=1.0 = termFreq=1.0\n),product of:",
          "value": 3.19292,
          "details": [
            {
              "description": "queryWeight, product of:",
              "value": 0.4793294,
              "details": [
              {
                "description": "idf(docFreq=9, maxDocs=2875)",
                "value": 6.661223
              }
<omitted>
}
```



























































































































