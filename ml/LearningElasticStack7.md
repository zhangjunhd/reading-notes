![cover](https://img1.doubanio.com/view/subject/s/public/s33618999.jpg)

    作者: Pranav Shukla / Sharath Kumar M N
    副标题: A beginner's guide to storing, managing, and analyzing data with the updated features of Elastic 7.0
    出版年: 2019-5
    ISBN: 9781789954395

- [豆瓣](https://book.douban.com/subject/35030562/)
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
    - [Mappings and datatypes](#mappings-and-datatypes)
      - [Datatypes](#datatypes)
      - [Mappings](#mappings)
  - [CRUD operations](#crud-operations)

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
The process of dividing the data among shards is called `sharding`.

By default, every index is configured to have five shards in Elasticsearch. The following diagram illustrates how five shards of one index may be distributed on a three-node cluster:

![](https://learning.oreilly.com/library/view/learning-elastic-stack/9781789954395/assets/0f837399-4293-4596-8c95-3120fe5590a6.png)

Figure 2.4: Organization of shards across the nodes of a cluster

Distributed systems such as Elasticsearch are expected to run in spite of hardware failure. This issue is addressed by `replica shards` or `replicas`. Each shard in an index can be configured to have zero or more replica shards. Replica shards are extra copies of the original or primary shard and provide a high availability of data.

For example, with one replica of each shard, we will have one extra copy of each replica. In the following diagram, we have five primary shards, with one replica of each shard:

![](https://learning.oreilly.com/library/view/learning-elastic-stack/9781789954395/assets/2315dca5-e7ba-40d9-a8aa-68d88bd02d46.png)

Figure 2.6: Organization of shards with replicas on cluster nodes

### Mappings and datatypes
#### Datatypes
In a document, each field has a datatype associated with it. The core datatypes supported by Elasticsearch are as follows:

- String datatypes:
  - `text`: The `text` datatype is useful for supporting full-text search for fields that contain a description or lengthy text values. These fields are analyzed before indexing to support full-text search.
  - `keyword`: The `keyword` type enables analytics on string fields. Fields of this type support sorting, filtering, and aggregations.
- Numeric datatypes:
  - `byte`, `short`, `integer`, and `long`: Signed integers with 8-bit, 16-bit, 32-bit, and 64-bit precision, respectively
  - `float` and `double`: IEEE 754 floating-point numbers with single-precision 32-bit and double-precision 64-bit representations
  - `half_float`: IEEE 754 floating-point number with half-precision 16-bit representation
  - `scaled_float`: Floating-point number backed by a long and fixed scaling factor
- Date datatype:
  - `date`: Date with an optional timestamp component that's capable of storing precision timestamps down to the millisecond
- Boolean datatype:
  - `boolean`: The boolean datatype that is common in all programming languages
- Binary datatype:
  - `binary`: Allows you to store arbitrary binary values after performing Base64 encoding
- Range datatypes:
  - `integer_range`, `float_range`, `long_range`, `double_range`, and `date_range`: Defines ranges of integers, floats, longs, and more
  - `scaled_float` is a very useful datatype for storing something such as price, which always has a precision of a limited number of decimal places

The complex datatypes supported by Elasticsearch are as follows:

- `Array datatype`: Arrays of the same types of instances. For example, arrays of strings, integers, and more. Doesn't allow for the mixing of datatypes in arrays.
- `Object datatype`: Allows inner objects within JSON documents.
- `Nested datatype`: Useful for supporting arrays of inner objects, where each inner object needs to be independently queriable.

The other datatypes supported by Elasticsearch are as follows:

- `Geo-point datatype`: Allows the storing of geo-points as longitude and latitude. The geo-point datatype enables queries such as searching across all ATMs within a distance of 2 km from a point.
- `Geo-shape datatype`: Allows you to store geometric shapes such as polygons, maps, and more. Geo-shape enables queries such as searching for all items within a shape.
- `IP datatype`: Allows you to store IPv4 and IPv6 addresses.

#### Mappings
Let's add another product to the product catalog:

```json
PUT /catalog/_doc/2
{    
    "sku": "SP000002",    
    "title": "Google Pixel Phone 32GB - 5 inch display",    
    "description": "Google Pixel Phone 32GB - 5 inch display (Factory Unlocked US Version)",    
    "price": 400.00,    
    "resolution": "1440 x 2560 pixels",    
    "os": "Android 7.1"
}
```

As you can see, the product has many different fields, as it is of a completely different category. Yet, there are some fields that are common in all products.

When the first document about the product type was indexed in the index catalog, the following tasks were performed by Elasticsearch:

- Creating an index with the name catalog
- Defining the mappings for the type of documents that will be stored in the index's default type – `_doc`

Creating an index with the name catalog:

The first step involves creating an index, because the index doesn't exist already.

- Sometimes, an index needs to be created on the fly, just like in this case, where the insertion of the first document triggers the creation of a new index. The `index template` kicks in and provides the matching template for the index while creating the new index.
- An index can be created beforehand as well. Elasticsearch has a separate index API (https://www.elastic.co/guide/en/elasticsearch/reference/current/indices.html) that deals with index-level operations. This includes create, delete, get, create mapping, and many more advanced operations. 

The second step involves defining the mappings for the type of product.

When the first document is indexed within a type that doesn't exist yet, Elasticsearch tries to infer the datatypes of all the fields. This feature is called the `dynamic mapping` of types. 

To see the mappings of the product type in the catalog index, execute the following command in the Kibana Console UI:

```
GET /catalog/_mapping
```

The response should look like the following:

```json
{  
    "catalog": {    
        "mappings" : {      
            "properties" : {        
                "ISBN" : {          
                    "type" : "text",          
                    "fields" : {            
                        "keyword" : {              
                            "type" : "keyword",              
                            "ignore_above" : 256            
                            }          
                        }        
                    },        
                    "author" : {          
                        "type" : "text",          
                        "fields" : {            
                            "keyword" : {              
                                "type" : "keyword",              
                                "ignore_above" : 256          
                            }          
                        }        
                    },        
                    "description" : {          
                        "type" : "text",          
                        "fields" : {            
                            "keyword" : {              
                                "type" : "keyword",              
                                "ignore_above" : 256           
                            }          
                        }        
                    },        
                    "os" : {          
                        "type" : "text",          
                        "fields" : {            
                            "keyword" : {              
                                "type" : "keyword",              
                                "ignore_above" : 256           
                            }          
                        }        
                    },        
                    "price" : {          
                        "type" : "float"        
                    },        
                    "resolution" : {          
                        "type" : "text",          
                        "fields" : {            
                            "keyword" : {              
                                "type" : "keyword",              
                                "ignore_above" : 256           
                            }          
                        }        
                    },        
                    "sku" : {          
                        "type" : "text",          
                        "fields" : {            
                            "keyword" : {              
                                "type" : "keyword",              
                                "ignore_above" : 256            
                            }          
                        }        
                    },        
                    "title" : {          
                        "type" : "text",          
                        "fields" : {            
                            "keyword" : {              
                                "type" : "keyword",              
                                "ignore_above" : 256            
                            }          
                        }        
                    }      
                }    
            }  
        }
    }
```

The `text` datatype enables full-text search on a field. Additionally, the same field is also stored as a `multi-field`, and it is also stored as a `keyword` type. This effectively enables full-text search and analytics (such as sorting, aggregations, and filtering) on the same field. 

## CRUD operations



































































































































