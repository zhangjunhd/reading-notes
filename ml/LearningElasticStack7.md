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
- [oreilly](https://learning.oreilly.com/library/view/learning-elastic-stack/9781789954395/)

---

- [Section 1: Introduction to Elastic Stack and Elasticsearch](#section-1-introduction-to-elastic-stack-and-elasticsearch)
- [Introducing Elastic Stack](#introducing-elastic-stack)
  - [What is Elasticsearch, and why use it?](#what-is-elasticsearch-and-why-use-it)
  - [Exploring the components of the Elastic Stack](#exploring-the-components-of-the-elastic-stack)
  - [Use cases of Elastic Stack](#use-cases-of-elastic-stack)
    - [Log and security analytics](#log-and-security-analytics)
    - [Product search](#product-search)
    - [Metrics analytics](#metrics-analytics)
    - [Web search and website search](#web-search-and-website-search)
- [Getting Started with Elasticsearch](#getting-started-with-elasticsearch)
  - [Using the Kibana Console UI](#using-the-kibana-console-ui)
  - [Core concepts of Elasticsearch](#core-concepts-of-elasticsearch)
    - [Indexes](#indexes)
    - [Types](#types)
    - [Documents](#documents)
    - [Nodes](#nodes)
    - [Clusters](#clusters)
    - [Shards and replicas](#shards-and-replicas)

# Section 1: Introduction to Elastic Stack and Elasticsearch
# Introducing Elastic Stack
## What is Elasticsearch, and why use it?
Let's look at the key benefits of using Elasticsearch as your data store:

- Schemaless, document-oriented
- Searching
- Analytics
- Rich client library support and the REST API
- Easy to operate and easy to scale
- Near real-time
- Lightning-fast
- Fault-tolerant

## Exploring the components of the Elastic Stack
![](https://learning.oreilly.com/library/view/learning-elastic-stack/9781789954395/assets/a7df18a3-5272-4297-a1eb-f317adc8f644.png)

## Use cases of Elastic Stack
### Log and security analytics
The application infrastructure could have the following components:

- Web servers
- Application servers
- Database servers
- Message brokers

Each component can be used to solve this problem as follows:

- The `Beats` framework, Filebeat in particular, can run as a lightweight agent to collect and forward logs.
- `Logstash` can centralize events received from Beats, and parse and transform each log entry before sending it to the Elasticsearch cluster.
- `Elasticsearch` indexes logs. It enables both search and analytics on the parsed logs.
- `Kibana` then lets you create visualizations based on errors, warnings, and other information logs. It lets you create dashboards on which you can centrally monitor events as they occur, in real time.
- With `X-Pack`, you can secure the solution, configure alerts, get reports, and analyze relationships in data.

### Product search
A product search involves searching for the most `relevant` product from thousands or tens of thousands of products and presenting the most relevant products at the top of the list before other, less relevant, products.

`Elasticsearch`'s full-text and relevance search capabilities can find the best-matching results. Text analysis capabilities backed by `Lucene`, and innovations added by Elasticsearch.

### Metrics analytics
`Elasticsearch` and `Kibana` allow for slicing and dicing metric data along different dimensions to provide a deep insight into your data.

### Web search and website search
`Apache Nutch` crawls the web, parses HTML pages, stores them, and also builds indexes to make the content searchable. Apache Nutch supports indexing into `Elasticsearch` or `Apache Solr` for its search engine.

# Getting Started with Elasticsearch
## Using the Kibana Console UI
The following diagram shows the Console UI:

![](https://learning.oreilly.com/library/view/learning-elastic-stack/9781789954395/assets/6497314a-42f6-4aa3-9f15-cceb4b7b182a.png)

Figure 2.1: Kibana Console

As you start typing in the Console editor, you will get an autosuggestion dropdown, as displayed in the following screenshot:

![](https://learning.oreilly.com/library/view/learning-elastic-stack/9781789954395/assets/1ac2dfec-191a-4962-8db3-3f728a64e659.png)

Figure 2.2: Kibana Dev Tools Console autosuggestions

## Core concepts of Elasticsearch
### Indexes
An `index` is a container that stores and manages documents of a single type in Elasticsearch. An index can contain documents of a single `Type`, as depicted in the following diagram:

![](https://learning.oreilly.com/library/view/learning-elastic-stack/9781789954395/assets/e8c8fa07-e081-4bf6-b14c-ec94904471aa.png)

Figure 2.3: Organization of Index, Type, and Document

An index is a logical container of a type. Some configuration parameters are defined at the index level, while other configuration parameters are defined at the type level.

>Prior to Elasticsearch 6.0, one index could contain multiple types. This has been changed since 6.0 to allow only one type within an index.

### Types
Typically, documents with mostly common sets of `fields` are grouped under one `type`. Elasticsearch is `schemaless`, allowing you to store any JSON document with any set of fields into a type.

The following code is for the index for customers:

```json
PUT /customers/_doc/1
{ 
    "firstName": "John", 
    "lastName": "Smith", 
    "contact": 
    { 
        "mobile": "212-xxx-yyyy" 
    }, 
    ...
}
```

The following code is for the index for products:

```json
PUT /products/_doc/1
{ 
    "title": "Apple iPhone Xs (Gold, 4GB RAM, 64GB Storage, 12 MP Dual Camera, 458 PPI Display)", 
    "price": 999.99, 
    ...
}
```

### Documents
A `document` consists of multiple `fields` and is the basic unit of information that's stored in Elasticsearch.

In addition to the fields that are sent by the user in the document, Elasticsearch maintains internal metafields. These fields are as follows:

- `_id`: This is the unique identifier of the document within the type, just like a primary key in a database table. It can be autogenerated or specified by the user.
- `_type`: This field contains the type of the document. 
- `_index`: This field contains the index name of the document.

### Nodes
An Elasticsearch `node` is a single server of Elasticsearch, which may be part of a larger cluster of nodes. Every Elasticsearch node is assigned a unique `ID` and `name` when it is started. A node can also be assigned a `static name` via the `node.name` parameter in the Elasticsearch configuration file, `config/elasticsearch.yml`.

### Clusters
A `cluster` is formed by one or more nodes. If you start multiple nodes on the same network without modifying the `cluster.name` property in `config/elasticsearch.yml`, they form a cluster automatically.

A cluster consists of multiple nodes, where each node takes responsibility for storing and managing its share of data. One cluster can host one or more indexes. An index is a logical grouping of related types of documents.

### Shards and replicas










































































































































































