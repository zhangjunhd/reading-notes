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































































































