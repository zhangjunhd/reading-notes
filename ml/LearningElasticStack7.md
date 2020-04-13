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





















































































































































































































