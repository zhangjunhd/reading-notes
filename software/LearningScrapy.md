![cover](https://img1.doubanio.com/view/subject/l/public/s28431839.jpg)

    作者: Dimitrios Kouzis-Loukas
    出版社: Packt Publishing - ebooks Account
    出版年: 2016-1-30
    页数: 270
    定价: USD 34.99
    装帧: Paperback
    ISBN: 9781784399788

[豆瓣链接](https://book.douban.com/subject/26708820/)

- [Basic Crawling](#basic-crawling)
    - [Vagrant: this book's official way to run examples](#vagrant-this-books-official-way-to-run-examples)
  - [UR2IM – the fundamental scraping process](#ur2im-%e2%80%93-the-fundamental-scraping-process)
    - [The URL](#the-url)
    - [The request and the response](#the-request-and-the-response)
    - [The Items](#the-items)
  - [A Scrapy project](#a-scrapy-project)
    - [Defining items](#defining-items)
    - [Writing spiders](#writing-spiders)
    - [Populating an item](#populating-an-item)
    - [Saving to files](#saving-to-files)
    - [Cleaning up – item loaders and housekeeping fields](#cleaning-up-%e2%80%93-item-loaders-and-housekeeping-fields)
    - [Creating contracts](#creating-contracts)
  - [Extracting more URLs](#extracting-more-urls)
    - [Two-direction crawling with a spider](#two-direction-crawling-with-a-spider)
    - [Two-direction crawling with a CrawlSpider](#two-direction-crawling-with-a-crawlspider)
- [Quick Spider Recipes](#quick-spider-recipes)
  - [A spider that logs in](#a-spider-that-logs-in)
  - [A spider that uses JSON APIs and AJAX pages](#a-spider-that-uses-json-apis-and-ajax-pages)
    - [Passing arguments between responses](#passing-arguments-between-responses)
  - [A 30-times faster property spider](#a-30-times-faster-property-spider)
  - [A spider that crawls based on an Excel file](#a-spider-that-crawls-based-on-an-excel-file)
- [Deploying to Scrapinghub](#deploying-to-scrapinghub)
  - [Signing up, signing in, and starting a project](#signing-up-signing-in-and-starting-a-project)
  - [Deploying our spiders and scheduling runs](#deploying-our-spiders-and-scheduling-runs)
  - [Accessing our items](#accessing-our-items)
  - [Scheduling recurring crawls](#scheduling-recurring-crawls)
- [Configuration and Management](#configuration-and-management)
  - [Using Scrapy settings](#using-scrapy-settings)
  - [Essential settings](#essential-settings)
  - [Further settings](#further-settings)
- [Programming Scrapy](#programming-scrapy)
  - [Scrapy is a Twisted application](#scrapy-is-a-twisted-application)
    - [Deferreds and deferred chains](#deferreds-and-deferred-chains)
    - [Understanding Twisted and nonblocking I/O – a Python tale](#understanding-twisted-and-nonblocking-io-%e2%80%93-a-python-tale)
  - [Overview of Scrapy architecture](#overview-of-scrapy-architecture)
  - [Signals](#signals)
  - [Extending beyond middlewares](#extending-beyond-middlewares)
- [Pipeline Recipes](#pipeline-recipes)
  - [Using REST APIs](#using-rest-apis)
    - [Using treq](#using-treq)
    - [A pipeline that writes to Elasticsearch](#a-pipeline-that-writes-to-elasticsearch)
    - [A pipeline that geocodes using the Google Geocoding API](#a-pipeline-that-geocodes-using-the-google-geocoding-api)
    - [Enabling geoindexing on Elasticsearch](#enabling-geoindexing-on-elasticsearch)
  - [Interfacing databases with standard Python clients](#interfacing-databases-with-standard-python-clients)
    - [A pipeline that writes to MySQL](#a-pipeline-that-writes-to-mysql)
  - [Interfacing services using Twisted-specific clients](#interfacing-services-using-twisted-specific-clients)
    - [A pipeline that reads/writes to Redis](#a-pipeline-that-readswrites-to-redis)
  - [Interfacing CPU-intensive, blocking, or legacy functionality](#interfacing-cpu-intensive-blocking-or-legacy-functionality)
    - [A pipeline that performs CPU-intensive or blocking operations](#a-pipeline-that-performs-cpu-intensive-or-blocking-operations)
    - [A pipeline that uses binaries or scripts](#a-pipeline-that-uses-binaries-or-scripts)
- [Understanding Scrapy's Performance](#understanding-scrapys-performance)
  - [Scrapy's engine – an intuitive approach](#scrapys-engine-%e2%80%93-an-intuitive-approach)
    - [Cascading queuing systems](#cascading-queuing-systems)
    - [Scrapy's performance model](#scrapys-performance-model)
  - [Our benchmark system](#our-benchmark-system)
  - [The standard performance model](#the-standard-performance-model)
  - [Solving performance problems](#solving-performance-problems)
    - [Case #1 – saturated CPU](#case-1-%e2%80%93-saturated-cpu)
    - [Case #2 – blocking code](#case-2-%e2%80%93-blocking-code)
    - [Case #3 – &quot;garbage&quot; on the downloader](#case-3-%e2%80%93-quotgarbagequot-on-the-downloader)
    - [Case #4 – overflow due to many or large responses](#case-4-%e2%80%93-overflow-due-to-many-or-large-responses)
    - [Case #5 – overflow due to limited/excessive item concurrency](#case-5-%e2%80%93-overflow-due-to-limitedexcessive-item-concurrency)
    - [Case #6 – the downloader doesn't have enough to do](#case-6-%e2%80%93-the-downloader-doesnt-have-enough-to-do)
  - [Troubleshooting flow](#troubleshooting-flow)
- [Distributed Crawling with Scrapyd and Real-Time Analytics](#distributed-crawling-with-scrapyd-and-real-time-analytics)
  - [Scrapyd](#scrapyd)
  - [Overview of our distributed system](#overview-of-our-distributed-system)
    - [Sharded-index crawling](#sharded-index-crawling)
    - [Batching crawl URLs](#batching-crawl-urls)
    - [Getting start URLs from settings](#getting-start-urls-from-settings)
    - [Deploy your project to scrapyd servers](#deploy-your-project-to-scrapyd-servers)
  - [Creating our custom monitoring command](#creating-our-custom-monitoring-command)

# Basic Crawling
### Vagrant: this book's official way to run examples
![1](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_03_02.jpg)

The system used in this book

## UR2IM – the fundamental scraping process
![2](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_03_03.jpg)

The UR2IM process

### The URL
If you want to load one of their pages, you can use the Scrapy shell, as follows:

```
scrapy shell -s USER_AGENT="Mozilla/5.0" <your url here  e.g. http://www.gumtree.com/p/studios-bedsits-rent/...>
```

To debug problems while using scrapy shell, add the --pdb argument to enable interactive debugging in case of exceptions. For example:

```
scrapy shell --pdb https://gumtree.com
```

Let's open a page from that server with the Scrapy shell, and play a bit by typing the following on our dev machine:

```
$ scrapy shell http://web:9312/properties/property_000000.html
...
[s] Available Scrapy objects:
[s]   crawler    <scrapy.crawler.Crawler object at 0x2d4fb10>
[s]   item       {}
[s]   request    <GET http:// web:9312/.../property_000000.html>
[s]   response   <200 http://web:9312/.../property_000000.html>
[s]   settings   <scrapy.settings.Settings object at 0x2d4fa90>
[s]   spider     <DefaultSpider 'default' at 0x3ea0bd0>
[s] Useful shortcuts:

[s]   shelp()           Shell help (print this help)
[s]   fetch(req_or_url) Fetch request (or URL) and update local...
[s]   view(response)    View response in a browser
>>>
```

### The request and the response
If we try to print the first 50 characters of response.body, we get the following:

```
>>> response.body[:50]
'<!DOCTYPE html>\n<html>\n<head>\n<meta charset="UTF-8"'
```

### The Items
The next step is to try and extract data from the response into the fields of the `Item`.

![3](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_03_04.jpg)

The page, the fields we are interested in, and their HTML code

![4](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_03_05.jpg)

Extracting the title

Let's check to see if this XPath expression works with the Scrapy shell:

```
>>> response.xpath('//h1/text()').extract()
[u'set unique family well']
```

We will almost always use /text() for textual fields. If we skip it, we get the text for the whole element including markup, which is not what we want:

```
>>> response.xpath('//h1').extract()
[u'<h1 itemprop="name" class="space-mbs">set unique family well</h1>']
```

Price is contained in the following HTML structure:

```html
<strong class="ad-price txt-xlarge txt-emphasis" itemprop="price"> £334.39pw</strong>
```

Again we see itemprop="name", which is brilliant. Our XPath will be //*[@itemprop="price"][1]/text(). Let's try it:

```
>>> response.xpath('//*[@itemprop="price"][1]/text()').extract()
[u'\xa3334.39pw']
```

We can do so by using the re() method and a simple regular expression instead of extract():

```
>>> response.xpath('//*[@itemprop="price"][1]/text()').re('[.0-9]+')
[u'334.39']
```

## A Scrapy project
```
$ scrapy startproject properties
$ cd properties
$ tree
.
├── properties
│   ├── __init__.py
│   ├── items.py
│   ├── pipelines.py
│   ├── settings.py
│   └── spiders
│       └── __init__.py
└── scrapy.cfg

2 directories, 6 files
```

### Defining items
With our text editor, we modify the properties/items.py file until it contains the following:

```py
from scrapy.item import Item, Field

class PropertiesItem(Item):
    # Primary fields
    title = Field()
    price = Field()
    description = Field()
    address = Field()
    image_urls = Field()

    # Calculated fields
    images = Field()
    location = Field()

    # Housekeeping fields
    url = Field()
    project = Field()
    spider = Field()
    server = Field()
    date = Field()
```

### Writing spiders
```py
$ scrapy genspider basic web
Created spider 'basic' using template 'basic' in module:
  properties.spiders.basic
```

If we have a look at the properties/spiders/basic.py file, we will see the following code:

```py
import scrapy

class BasicSpider(scrapy.Spider):
    name = "basic"
    allowed_domains = ["web"]
    start_urls = (
        'http://www.web/',
    )

    def parse(self, response):
        pass
```

First we will use the URL that we used with Scrapy shell by setting start_urls accordingly. Then we will use spider's predefined method log() to output everything that we summarized in the primary fields table. The modified code of properties/spiders/basic.py will be as follows:

```py
import scrapy

class BasicSpider(scrapy.Spider):
    name = "basic"
    allowed_domains = ["web"]
    start_urls = (
        'http://web:9312/properties/property_000000.html',
    )

    def parse(self, response):
        self.log("title: %s" % response.xpath(
            '//*[@itemprop="name"][1]/text()').extract())
        self.log("price: %s" % response.xpath(
            '//*[@itemprop="price"][1]/text()').re('[.0-9]+'))
        self.log("description: %s" % response.xpath(
            '//*[@itemprop="description"][1]/text()').extract())
        self.log("address: %s" % response.xpath(
            '//*[@itemtype="http://schema.org/'
            'Place"][1]/text()').extract())
        self.log("image_urls: %s" % response.xpath(
            '//*[@itemprop="image"][1]/@src').extract())
```

After all this wait, it's high time we run our spider. We can do so using the command scrapy crawl followed by the name of the spider:

```py
$ scrapy crawl basic
INFO: Scrapy 1.0.3 started (bot: properties)
...
INFO: Spider opened
DEBUG: Crawled (200) <GET http://...000.html>
DEBUG: title: [u'set unique family well']
DEBUG: price: [u'334.39']
DEBUG: description: [u'website...']
DEBUG: address: [u'Angel, London']
DEBUG: image_urls: [u'../images/i01.jpg']
INFO: Closing spider (finished)
...
```

Let's also play with another command—scrapy parse. It allows us to use the "most suitable" spider to parse any URL given as an argument. I don't like to leave things to chance, so let's use it in conjunction with the --spider parameter to set the spider:

```
$ scrapy parse --spider=basic http://web:9312/properties/property_000001.html
```

### Populating an item
```py
import scrapy
from properties.items import PropertiesItem

class BasicSpider(scrapy.Spider):
    name = "basic"
    allowed_domains = ["web"]
    start_urls = (
        'http://web:9312/properties/property_000000.html',
    )

    def parse(self, response):
        item = PropertiesItem()
        item['title'] = response.xpath(
            '//*[@itemprop="name"][1]/text()').extract()
        item['price'] = response.xpath(
            '//*[@itemprop="price"][1]/text()').re('[.0-9]+')
        item['description'] = response.xpath(
            '//*[@itemprop="description"][1]/text()').extract()
        item['address'] = response.xpath(
            '//*[@itemtype="http://schema.org/'
            'Place"][1]/text()').extract()
        item['image_urls'] = response.xpath(
            '//*[@itemprop="image"][1]/@src').extract()
        return item
```

### Saving to files
```
$ scrapy crawl basic -o items.json
$ cat items.json
[{"price": ["334.39"], "address": ["Angel, London"], "description": ["website court ... offered"], "image_urls": ["../images/i01.jpg"], "title": ["set unique family well"]}]

$ scrapy crawl basic -o items.jl
$ cat items.jl
{"price": ["334.39"], "address": ["Angel, London"], "description": ["website court ... offered"], "image_urls": ["../images/i01.jpg"], "title": ["set unique family well"]}

$ scrapy crawl basic -o items.csv
$ cat items.csv
description,title,url,price,spider,image_urls...
"...offered",set unique family well,,334.39,,../images/i01.jpg

$ scrapy crawl basic -o items.xml
$ cat items.xml
<?xml version="1.0" encoding="utf-8"?>
<items><item><price><value>334.39</value></price>...</item></items>
```

By using the following, for example, you will have Scrapy automatically upload the files for you on an FTP or an S3 bucket:

```
$ scrapy crawl basic -o "ftp://user:pass@ftp.scrapybook.com/items.json "
$ scrapy crawl basic -o "s3://aws_key:aws_secret@scrapybook/items.json"
```

 I was originally surprised by the lack of built-in support by Scrapy for MySQL or other databases. The fact is that there is nothing built-in, because it's fundamentally wrong for Scrapy's way of thinking. Scrapy is meant to be fast and scalable. It uses very little CPU and as much inbound bandwidth as possible. **Inserting to most relational databases would be a disaster from the perspective of performance.**

One more thing to notice is that if you try to use scrapy parse now, it will show you the scraped items and new requests (none in this case) that your crawl generated:

```
$ scrapy parse --spider=basic http://web:9312/properties/property_000001.html
INFO: Scrapy 1.0.3 started (bot: properties)
...
INFO: Spider closed (finished)

>>> STATUS DEPTH LEVEL 1 <<<
# Scraped Items  ------------------------------------------------
[{'address': [u'Plaistow, London'],
  'description': [u'features'],
  'image_urls': [u'../images/i02.jpg'],
  'price': [u'388.03'],
  'title': [u'belsize marylebone...deal']}]
# Requests  ------------------------------------------------
[]
```

### Cleaning up – item loaders and housekeeping fields
We start by using a great utility class, `ItemLoader`, in order to replace all those messy looking extract() and xpath() operations. By using it, our parse() method changes to the following:

```py
def parse(self, response):
    l = ItemLoader(item=PropertiesItem(), response=response)

    l.add_xpath('title', '//*[@itemprop="name"][1]/text()')
    l.add_xpath('price', './/*[@itemprop="price"]'
           '[1]/text()', re='[,.0-9]+')
    l.add_xpath('description', '//*[@itemprop="description"]'
           '[1]/text()')
    l.add_xpath('address', '//*[@itemtype='
           '"http://schema.org/Place"][1]/text()')
    l.add_xpath('image_urls', '//*[@itemprop="image"][1]/@src')

    return l.load_item()
```

`ItemLoaders` pass values from XPath/CSS expressions through different processor classes. Processors are fast yet simple functions. An example of a processor is `Join()`. This processor, assuming that you have selected multiple paragraphs with some XPath expression like //p, will join their text together in a single entry. Another particularly interesting processor is `MapCompose()`. You can use it with any Python function or chain of Python functions to implement complex functionality.

```py
>>> from scrapy.loader.processors import MapCompose, Join
>>> Join()(['hi','John'])
u'hi John'
>>> MapCompose(unicode.strip)([u'  I',u' am\n'])
[u'I', u'am']
>>> MapCompose(unicode.strip, unicode.title)([u'nIce cODe'])
[u'Nice Code']
>>> MapCompose(float)(['3.14'])
[3.14]
>>> MapCompose(lambda i: i.replace(',', ''), float)(['1,400.23'])
[1400.23]
>>> import urlparse
>>> mc = MapCompose(lambda i: urlparse.urljoin('http://my.com/test/abc', i))
>>> mc(['example.html#check'])
['http://my.com/test/example.html#check']
>>> mc(['http://absolute/url#help'])
['http://absolute/url#help']
```

The key thing to take away is that processors are just simple and small functions that post-process our XPath/CSS results.

```py
def parse(self, response):
    l.add_xpath('title', '//*[@itemprop="name"][1]/text()',
                MapCompose(unicode.strip, unicode.title))
    l.add_xpath('price', './/*[@itemprop="price"][1]/text()',
                MapCompose(lambda i: i.replace(',', ''), float),
                re='[,.0-9]+')
    l.add_xpath('description', '//*[@itemprop="description"]'
                '[1]/text()', MapCompose(unicode.strip), Join())
    l.add_xpath('address',
                '//*[@itemtype="http://schema.org/Place"][1]/text()',
                MapCompose(unicode.strip))
    l.add_xpath('image_urls', '//*[@itemprop="image"][1]/@src',
                MapCompose(
                lambda i: urlparse.urljoin(response.url, i)))
```

Finally, we can add single values that we calculate with Python (instead of XPath/CSS expressions) by using the `add_value()` method.

```py
l.add_value('url', response.url)
l.add_value('project', self.settings.get('BOT_NAME'))
l.add_value('spider', self.name)
l.add_value('server', socket.gethostname())
l.add_value('date', datetime.datetime.now())
```

### Creating contracts
`Contracts` are a bit like unit tests for spiders. They allow you to quickly know if something is broken.

```py
def parse(self, response):
    """ This function parses a property page.

    @url http://web:9312/properties/property_000000.html
    @returns items 1
    @scrapes title price description address image_urls
    @scrapes url project spider server date
    """

$ scrapy check basic
----------------------------------------------------------------
Ran 3 contracts in 1.640s
OK

FAIL: [basic] parse (@scrapes post-hook)
------------------------------------------------------------------
ContractFail: 'url' field is missing
```

Overall, the following is the code for our first basic spider:

```py
from scrapy.loader.processors import MapCompose, Join
from scrapy.loader import ItemLoader
from properties.items import PropertiesItem
import datetime
import urlparse
import socket
import scrapy

class BasicSpider(scrapy.Spider):
    name = "basic"
    allowed_domains = ["web"]

    # Start on a property page
    start_urls = (
        'http://web:9312/properties/property_000000.html',
    )

    def parse(self, response):
        """ This function parses a property page.
        @url http://web:9312/properties/property_000000.html
        @returns items 1
        @scrapes title price description address image_urls
        @scrapes url project spider server date
        """
        # Create the loader using the response
        l = ItemLoader(item=PropertiesItem(), response=response)

        # Load fields using XPath expressions
        l.add_xpath('title', '//*[@itemprop="name"][1]/text()',
                    MapCompose(unicode.strip, unicode.title))
        l.add_xpath('price', './/*[@itemprop="price"][1]/text()',
                    MapCompose(lambda i: i.replace(',', ''), float),
                    re='[,.0-9]+')
        l.add_xpath('description', '//*[@itemprop="description"]'
                    '[1]/text()',
                    MapCompose(unicode.strip), Join())
        l.add_xpath('address',
                    '//*[@itemtype="http://schema.org/Place"]'
                    '[1]/text()',
                    MapCompose(unicode.strip))
        l.add_xpath('image_urls', '//*[@itemprop="image"]'
                    '[1]/@src', MapCompose(
                    lambda i: urlparse.urljoin(response.url, i)))

        # Housekeeping fields
        l.add_value('url', response.url)
        l.add_value('project', self.settings.get('BOT_NAME'))
        l.add_value('spider', self.name)
        l.add_value('server', socket.gethostname())
        l.add_value('date', datetime.datetime.now())

        return l.load_item()
```

## Extracting more URLs
A typical crawler moves in two directions:

- Horizontally—from an index page to another
- Vertically—from an index page to the listing pages to extract Items

### Two-direction crawling with a spider
We are now ready to write a new parse() method that will perform both horizontal and vertical crawling:

```py
def parse(self, response):
    # Get the next index URLs and yield Requests
    next_selector = response.xpath('//*[contains(@class,'
                                   '"next")]//@href')
    for url in next_selector.extract():
        yield Request(urlparse.urljoin(response.url, url))

    # Get item URLs and yield Requests
    item_selector = response.xpath('//*[@itemprop="url"]/@href')
    for url in item_selector.extract():
        yield Request(urlparse.urljoin(response.url, url),
                      callback=self.parse_item)
```

```
$ scrapy crawl manual -s CLOSESPIDER_ITEMCOUNT=90
INFO: Scrapy 1.0.3 started (bot: properties)
...
DEBUG: Crawled (200) <...index_00000.html> (referer: None)
DEBUG: Crawled (200) <...property_000029.html> (referer: ...index_00000.html)
DEBUG: Scraped from <200 ...property_000029.html>
  {'address': [u'Clapham, London'],
   'date': [datetime.datetime(2015, 10, 4, 21, 25, 22, 801098)],
   'description': [u'situated camden facilities corner'],
   'image_urls': [u'http://web:9312/images/i10.jpg'],
   'price': [223.88],
   'project': ['properties'],
   'server': ['scrapyserver1'],
   'spider': ['manual'],
   'title': [u'Portered Mile'],
   'url': ['http://.../property_000029.html']}
DEBUG: Crawled (200) <...property_000028.html> (referer: ...index_00000.html)
...
DEBUG: Crawled (200) <...index_00001.html> (referer: ...)
DEBUG: Crawled (200) <...property_000059.html> (referer: ...)
...
INFO: Dumping Scrapy stats: ...
   'downloader/request_count': 94, ...
   'item_scraped_count': 90,
```

### Two-direction crawling with a CrawlSpider
If you felt that this two-direction crawling was a bit too tedious, then you are really getting it. The easiest way to achieve the same results is by using a `CrawlSpider`, a class that allows easier implementation of such crawls.

```
$ scrapy genspider -t crawl easy web
Created spider 'crawl' using template 'crawl' in module:
  properties.spiders.easy
```

Now the file properties/spiders/easy.py contains the following:

```py
...
class EasySpider(CrawlSpider):
    name = 'easy'
    allowed_domains = ['web']
    start_urls = ['http://www.web/']

    rules = (
        Rule(LinkExtractor(allow=r'Items/'), callback='parse_item', follow=True),
    )

    def parse_item(self, response):
        ...
```

CrawlSpider provides an implementation of the parse() method that uses the rules variable to do exactly what we did manually in the previous example.

We will replace the predefined rules variable instead with two rules, one for horizontal and one for vertical crawling:

```py
rules = (
    Rule(LinkExtractor(restrict_xpaths='//*[contains(@class,"next")]')),
Rule(LinkExtractor(restrict_xpaths='//*[@itemprop="url"]'),
         callback='parse_item')
)
```

```
$ scrapy crawl easy -s CLOSESPIDER_ITEMCOUNT=90
```

# Quick Spider Recipes
## A spider that logs in
![1](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_05_01.jpg)

Requests and Responses while logging in on a website

```py
class LoginSpider(CrawlSpider):
    name = 'login'
```

We need to send the initial request that logs in by performing a POST request on http://localhost:9312/dynamic/login. We do this with Scrapy's `FormRequest` class.

```py
from scrapy.http import FormRequest

# Start with a login request
def start_requests(self):
  return [
    FormRequest(
      "http://web:9312/dynamic/login",
      formdata={"user": "user", "pass": "pass"}
         )]
```

We can run this using scrapy crawl as usual:

```
$ scrapy crawl login
INFO: Scrapy 1.0.3 started (bot: properties)
...
DEBUG: Redirecting (302) to <GET .../gated> from <POST .../login >
DEBUG: Crawled (200) <GET .../data.php>
DEBUG: Crawled (200) <GET .../property_000001.html> (referer: .../data.php)
DEBUG: Scraped from <200 .../property_000001.html>
  {'address': [u'Plaistow, London'],
   'date': [datetime.datetime(2015, 11, 25, 12, 7, 27, 120119)],
   'description': [u'features'],
   'image_urls': [u'http://web:9312/images/i02.jpg'],
...
INFO: Closing spider (finished)
INFO: Dumping Scrapy stats:
  {...
   'downloader/request_method_count/GET': 4,
   'downloader/request_method_count/POST': 1,
...
   'item_scraped_count': 3,
```

If we used the wrong user/pass, we would get a redirect to a page with no item URLs and the process would terminate at that point, as you can see in the following run:

```
$ scrapy crawl login
INFO: Scrapy 1.0.3 started (bot: properties)
...
DEBUG: Redirecting (302) to <GET .../dynamic/error > from <POST .../dynamic/login>
DEBUG: Crawled (200) <GET .../dynamic/error>
...
INFO: Spider closed (closespider_itemcount)
```

Some sites, for example, require you to pass some form variables from the form page to the login page while performing the POST request in order to confirm that cookies are enabled, and also to make it a bit more difficult for you to try to check with brute-force thousands of user/pass combinations.

![2](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_05_02.jpg)

For example, if you visit http://localhost:9312/dynamic/nonce, you will see a page that looks identical, but if you use Chrome's Debugger, you will notice that the form in this page has a hidden field called `nonce`. When you submit this form (to http://localhost:9312/dynamic/nonce-login), the login won't be successful unless you pass not only the correct user/pass, but also the exact nonce value that server gave you when you visited this login page.

All we need to do is to use the `formdata` argument to fill in the user and pass fields and return the `FormRequest`. Here is the relevant code:

```py
# Start on the welcome page
def start_requests(self):
    return [
        Request(
            "http://web:9312/dynamic/nonce",
            callback=self.parse_welcome)
    ]

# Post welcome page's first form with the given user/pass
def parse_welcome(self, response):
    return FormRequest.from_response(
        response,
        formdata={"user": "user", "pass": "pass"}
    )
```

We can run this spider as usual:

```
$ scrapy crawl noncelogin
INFO: Scrapy 1.0.3 started (bot: properties)
...
DEBUG: Crawled (200) <GET .../dynamic/nonce>
DEBUG: Redirecting (302) to <GET .../dynamic/gated > from <POST .../dynamic/login-nonce>
DEBUG: Crawled (200) <GET .../dynamic/gated>
...
INFO: Dumping Scrapy stats:
  {...
   'downloader/request_method_count/GET': 5,
   'downloader/request_method_count/POST': 1,
...
   'item_scraped_count': 3,
```

## A spider that uses JSON APIs and AJAX pages
![3](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_05_03.jpg)

Request and Response on pages that load JSON objects dynamically

Our new start_urls should be the JSON API URL:

```py
start_urls = (
    'http://web:9312/properties/api.json',
)
```

We can `import json` and use the following code to parse the JSON object:

```py
def parse(self, response):
    base_url = "http://web:9312/properties/"
    js = json.loads(response.body)
    for item in js:
        id = item["id"]
        url = base_url + "property_%06d.html" % id
        yield Request(url, callback=self.parse_item)
```

We can run this example as usual with scrapy crawl:

```
$ scrapy crawl api
INFO: Scrapy 1.0.3 started (bot: properties)
...
DEBUG: Crawled (200) <GET ...properties/api.json>
DEBUG: Crawled (200) <GET .../property_000029.html>
...
INFO: Closing spider (finished)
INFO: Dumping Scrapy stats:
...
   'downloader/request_count': 31, ...
   'item_scraped_count': 30,
```

### Passing arguments between responses
We can then retrieve this from the Response that `parse_item()` receives. Request has a dict named `meta` that is directly accessible on Response. For our example, let's set a title value on this dict to store the title from the JSON object:

```py
title = item["title"]
yield Request(url, meta={"title": title},callback=self.parse_item)
```

Inside parse_item(), we can use this value instead of the XPath expression that we used to have:

```py
l.add_value('title', response.meta['title'],
		   MapCompose(unicode.strip, unicode.title))
```

## A 30-times faster property spider
>Please keep in mind that many websites offer a different number of items on their index pages. For example, a website might be able to give you 10, 50 or 100 listings per index page by tuning a parameter, such as &show=50. If so, obviously, set it to the maximum value available.

## A spider that crawls based on an Excel file
![4](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_05_05.jpg)

todo.csv contains URLs and XPath expressions

```py
import csv
import scrapy
from scrapy.http import Request
from scrapy.loader import ItemLoader
from scrapy.item import Item, Field

class FromcsvSpider(scrapy.Spider):
    name = "fromcsv"

def start_requests(self):
    with open("todo.csv", "rU") as f:
        reader = csv.DictReader(f)
        for line in reader:
            request = Request(line.pop('url'))
            request.meta['fields'] = line
            yield request

def parse(self, response):
    item = Item()
    l = ItemLoader(item=item, response=response)
    for name, xpath in response.meta['fields'].iteritems():
        if xpath:
            item.fields[name] = Field()
            l.add_xpath(name, xpath)
    return l.load_item()
```

Let's crawl and save the output to an out.csv file:

```
$ scrapy crawl fromcsv -o out.csv
INFO: Scrapy 0.0.3 started (bot: generic)
...
DEBUG: Scraped from <200 a.html>
{'name': [u'My item'], 'price': [u'128']}
DEBUG: Scraped from <200 b.html>
{'name': [u'Getting interesting'], 'price': [u'300']}
DEBUG: Scraped from <200 c.html>
{'name': [u'Buy this now']}
...
INFO: Spider closed (finished)
$ cat out.csv 
price,name
128,My item
300,Getting interesting
,Buy this now
```

# Deploying to Scrapinghub
## Signing up, signing in, and starting a project
The first step is to open an account on http://scrapinghub.com/.

![1](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_06_01.jpg)

Creating a new project with scrapinghub

We can name our project properties (2) and click on the Create button (3). Then, we click on the new link in the homepage (4) to open the project.

![2](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_06_02.jpg)

The main menu

`Jobs` and `Spiders` sections provide information about our runs and spiders, respectively. `Periodic Jobs` enables us to schedule recurrent crawls.

![3](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_06_03.jpg)

Spider deployment settings

## Deploying our spiders and scheduling runs
We will deploy directly from our dev machine. In order to do so, we just have to copy the lines from the `Scrapy Deploy` page (3) and put them on `scrapy.cfg` of our project, replacing the default `[deploy]` section.

```
$ pwd
/root/book/ch06/properties
$ ls
properties  scrapy.cfg
$ cat scrapy.cfg
...

[settings]
default = properties.settings

# Project: properties
[deploy]
url = http://dash.scrapinghub.com/api/scrapyd/
username = 180128bc7a0.....50e8290dbf3b0
password =
project = 28814
```

In order to deploy the spider, we will use the `shub` tool provided by Scrapinghub.

```
$ shub login
Insert your Scrapinghub API key : 180128bc7a0.....50e8290dbf3b0
Success.

$ shub deploy
Packing version 1449092838
Deploying to project "28814" in {"status": "ok", "project": 28814, "version": "1449092838", "spiders": 1}
Run your spiders at: https://dash.scrapinghub.com/p/28814/
```

![4](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_06_04.jpg)

Selecting the spider

![5](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_06_05.jpg)

Scheduling a spider run

## Accessing our items
![6](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_06_06.jpg)

Inspecting and exporting items

Another way to access our items is through Scrapinghub's Items API.

```
https://dash.scrapinghub.com/p/28814/job/1/1/
```

On this URL, 28814 is the **project number** (we have also set this in the scrapy.cfg file before) then the first 1 is the **number/ID of this spider** (the one named "tomobile"), and the second 1 is **the number of the job**. Using these three numbers in this order, we can use curl from our console to retrieve our items by making a request to `https://storage.scrapinghub.com/items/<project id>/<spider id>/<job id> `and using our username/API key to authenticate, as follows:

```
$ curl -u 180128bc7a0.....50e8290dbf3b0: https://storage.scrapinghub.com/items/28814/1/1
{"_type":"PropertiesItem","description":["same\r\nsmoking\r\nr...
{"_type":"PropertiesItem","description":["british bit keep eve...
...
```

## Scheduling recurring crawls
![7](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_06_07.jpg)

Scheduling recurrent crawls

# Configuration and Management
## Using Scrapy settings
You wouldn't typically need to modify the default settings but `scrapy/settings/default_settings.py` (in your system's Scrapy source code or Scrapy's GitHub) is certainly an interesting read.

More often than not, we modify settings just after the command level on our project's `<project_name>/settings.py` file.

## Essential settings
![1](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_07_01.jpg)

Essential Scrapy settings

## Further settings
![2](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_07_02.jpg)

Further Scrapy settings

# Programming Scrapy
## Scrapy is a Twisted application
![1](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_08_01.jpg)

Multithreaded code versus Twisted asynchronous code

### Deferreds and deferred chains
You can use a Python console to run the following experiments interactively:

```py
$ python
>>> from twisted.internet import defer
>>> # Experiment 1
>>> d = defer.Deferred()
>>> d.called
False
>>> d.callback(3)
>>> d.called
True
>>> d.result
3

>>> # Experiment 2
>>> d = defer.Deferred()
>>> def foo(v):
...     print "foo called"
...     return v+1
...
>>> d.addCallback(foo)
<Deferred at 0x7f...>
>>> d.called
False
>>> d.callback(3)
foo called
>>> d.called
True
>>> d.result
4

>>> # Experiment 3
>>> def status(*ds):
...     return [(getattr(d, 'result', "N/A"), len(d.callbacks)) for d in ds]
>>> def b_callback(arg):
...     print "b_callback called with arg =", arg
...     return b
>>> def on_done(arg):
...     print "on_done called with arg =", arg
...     return arg

>>> # Experiment 3.a
>>> a = defer.Deferred()
>>> b = defer.Deferred()
>>> a.addCallback(b_callback).addCallback(on_done)
>>> status(a, b)
[('N/A', 2), ('N/A', 0)]
>>> a.callback(3)
b_callback called with arg = 3
>>> status(a, b)
[(<Deferred at 0x10e7209e0>, 1), ('N/A', 1)]
>>> b.callback(4)
on_done called with arg = 4
>>> status(a, b)
[(4, 0), (None, 0)]

>>> # Experiment 3.b
>>> a = defer.Deferred()
>>> b = defer.Deferred()
>>> a.addCallback(b_callback).addCallback(on_done)
>>> status(a, b)
[('N/A', 2), ('N/A', 0)]
>>> b.callback(4)
>>> status(a, b)
[('N/A', 2), (4, 0)]
>>> a.callback(3)
b_callback called with arg = 3
on_done called with arg = 4
>>> status(a, b)
[(4, 0), (None, 0)]

>>> # Experiment 4
>>> deferreds = [defer.Deferred() for i in xrange(5)]
>>> join = defer.DeferredList(deferreds)
>>> join.addCallback(on_done)
>>> for i in xrange(4):
...     deferreds[i].callback(i)
>>> deferreds[4].callback(4)
on_done called with arg = [(True, 0), (True, 1), (True, 2),
                           (True, 3), (True, 4)]
```

### Understanding Twisted and nonblocking I/O – a Python tale
```py
# ~*~ Twisted - A Python tale ~*~

from time import sleep

# Hello, I'm a developer and I mainly setup Wordpress.
def install_wordpress(customer):
    # Our hosting company Threads Ltd. is bad. I start installation and...
    print "Start installation for", customer
    # ...then wait till the installation finishes successfully. It is
    # boring and I'm spending most of my time waiting while consuming
    # resources (memory and some CPU cycles). It's because the process
    # is *blocking*.
    sleep(3)
    print "All done for", customer

# I do this all day long for our customers
def developer_day(customers):
    for customer in customers:
        install_wordpress(customer)

developer_day(["Bill", "Elon", "Steve", "Mark"])
```

Let's run it:

```
$ ./deferreds.py 1
------ Running example 1 ------
Start installation for Bill
All done for Bill
Start installation
...
* Elapsed time: 12.03 seconds
```

```py
import threading

# The company grew. We now have many customers and I can't handle the
# workload. We are now 5 developers doing exactly the same thing.
def developers_day(customers):
    # But we now have to synchronize... a.k.a. bureaucracy
    lock = threading.Lock()
    #
    def dev_day(id):
        print "Goodmorning from developer", id
        # Yuck - I hate locks...
        lock.acquire()
        while customers:
            customer = customers.pop(0)
            lock.release()
            # My Python is less readable
            install_wordpress(customer)
            lock.acquire()
        lock.release()
        print "Bye from developer", id
    # We go to work in the morning
    devs = [threading.Thread(target=dev_day, args=(i,)) for i in range(5)]
    [dev.start() for dev in devs]
    # We leave for the evening
    [dev.join() for dev in devs]

# We now get more done in the same time but our dev process got more
# complex. As we grew we spend more time managing queues than doing dev
# work. We even had occasional deadlocks when processes got extremely
# complex. The fact is that we are still mostly pressing buttons and
# waiting but now we also spend some time in meetings.
developers_day(["Customer %d" % i for i in xrange(15)])
```

Let's run it as follows:

```
$ ./deferreds.py 2
------ Running example 2 ------
Goodmorning from developer 0Goodmorning from developer
1Start installation forGoodmorning from developer 2
Goodmorning from developer 3Customer 0
...
from developerCustomer 13 3Bye from developer 2
* Elapsed time: 9.02 seconds
```

It's quite hard to get even easy multithreaded code perfectly right, which leads us to `Twisted`:

```py
# For years we thought this was all there was... We kept hiring more
# developers, more managers and buying servers. We were trying harder
# optimising processes and fire-fighting while getting mediocre
# performance in return. Till luckily one day our hosting
# company decided to increase their fees and we decided to
# switch to Twisted Ltd.!

from twisted.internet import reactor
from twisted.internet import defer
from twisted.internet import task

# Twisted has a slightly different approach
def schedule_install(customer):
    # They are calling us back when a Wordpress installation completes.
    # They connected the caller recognition system with our CRM and
    # we know exactly what a call is about and what has to be done # next.
    #
    # We now design processes of what has to happen on certain events.
    def schedule_install_wordpress():
        def on_done():
            print "Callback: Finished installation for", customer
        print "Scheduling: Installation for", customer
        return task.deferLater(reactor, 3, on_done)
    #
    def all_done(_):
        print "All done for", customer
    #
    # For each customer, we schedule these processes on the CRM # and that
    # is all our chief-Twisted developer has to do
    d = schedule_install_wordpress()
    d.addCallback(all_done)
    #
    return d

# Yes, we don't need many developers anymore or any synchronization.
# ~~ Super-powered Twisted developer ~~
def twisted_developer_day(customers):
    print "Goodmorning from Twisted developer"
    #
    # Here's what has to be done today
    work = [schedule_install(customer) for customer in customers]
    # Turn off the lights when done
    join = defer.DeferredList(work)
    join.addCallback(lambda _: reactor.stop())
    #
    print "Bye from Twisted developer!"
# Even his day is particularly short!
twisted_developer_day(["Customer %d" % i for i in xrange(15)])

# Reactor, our secretary uses the CRM and follows-up on events!
reactor.run()
```

Let's run it:

```
$ ./deferreds.py 3
------ Running example 3 ------
Goodmorning from Twisted developer
Scheduling: Installation for Customer 0
....
Scheduling: Installation for Customer 14
Bye from Twisted developer!
Callback: Finished installation for Customer 0
All done for Customer 0
Callback: Finished installation for Customer 1
All done for Customer 1
...
All done for Customer 14
* Elapsed time: 3.18 seconds
```

The code doesn't have any threading nonsense but still these callback functions look a bit ugly. This leads us to the next example:

```py
# Twisted gave us utilities that make our code way more readable!
@defer.inlineCallbacks
def inline_install(customer):
    print "Scheduling: Installation for", customer
    yield task.deferLater(reactor, 3, lambda: None)
    print "Callback: Finished installation for", customer
    print "All done for", customer

def twisted_developer_day(customers):
   ... same as previously but using inline_install()
       instead of schedule_install()

twisted_developer_day(["Customer %d" % i for i in xrange(15)])
reactor.run()
```

Let's run it as follows:

```
$ ./deferreds.py 4
... exactly the same as before
```

Scrapy uses the same mechanism to limit the amount of concurrency in item processing pipelines (the `CONCURRENT_ITEMS` setting):

```py
@defer.inlineCallbacks
def inline_install(customer):
   ... same as above

# The new "problem" is that we have to manage all this concurrency to
# avoid causing problems to others, but this is a nice problem to have.
def twisted_developer_day(customers):
    print "Goodmorning from Twisted developer"
    work = (inline_install(customer) for customer in customers)
    #
    # We use the Cooperator mechanism to make the secretary not
    # service more than 5 customers simultaneously.
    coop = task.Cooperator()
    join = defer.DeferredList([coop.coiterate(work) for i in xrange(5)])
    #
    join.addCallback(lambda _: reactor.stop())
    print "Bye from Twisted developer!"

twisted_developer_day(["Customer %d" % i for i in xrange(15)])
reactor.run()

# We are now more lean than ever, our customers happy, our hosting
# bills ridiculously low and our performance stellar.

# ~*~ THE END ~*~
```

Let's run it:

```
$ ./deferreds.py 5
------ Running example 5 ------
Goodmorning from Twisted developer
Bye from Twisted developer!
Scheduling: Installation for Customer 0
...
Callback: Finished installation for Customer 4
All done for Customer 4
Scheduling: Installation for Customer 5
...
Callback: Finished installation for Customer 14
All done for Customer 14
* Elapsed time: 9.19 seconds
```

## Overview of Scrapy architecture
![2](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_08_02.jpg)

Scrapy's architecture

![3](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_08_03.jpg)

Middleware hierarchy

## Signals
Signals provide a mechanism to add callbacks to events that happen in the system, such as when a spider opens, or when an item gets scraped. You can hook to them using the `crawler.signals.connect()` method.

## Extending beyond middlewares
![4](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_08_04.jpg)

Scrapy interfaces and core objects

# Pipeline Recipes
![1](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_09_01.jpg)

The system for this chapter

## Using REST APIs
### Using treq
`treq` is a Python package that tries to be the equivalent of the Python requests package for Twisted-based applications.

### A pipeline that writes to Elasticsearch
Let's log in on our dev and verify that it's running fine:

```json
$ curl http://es:9200
{
  "name" : "Living Brain",
  "cluster_name" : "elasticsearch",
  "version" : { ... },
  "tagline" : "You Know, for Search"
}
```

In essence, this spider consists of just four lines of code:

```py
@defer.inlineCallbacks
def process_item(self, item, spider):
    data = json.dumps(dict(item), ensure_ascii=False).encode("utf-8")
    yield treq.post(self.es_url, data)
```

In order to enable the pipeline, we have to add it on an `ITEM_PIPELINES` setting inside settings.py and initialize our `ES_PIPELINE_URL` setting:

```py
ITEM_PIPELINES = {
    'properties.pipelines.tidyup.TidyUp': 100,
    'properties.pipelines.es.EsWriter': 800,
}
ES_PIPELINE_URL = 'http://es:9200/properties/property'
```

After doing so, we can go to the appropriate directory:

```
$ pwd
/root/book/ch09/properties
$ ls
properties  scrapy.cfg
```

Then we can run our spider:

```
$ scrapy crawl easy -s CLOSESPIDER_ITEMCOUNT=90
...
INFO: Enabled item pipelines: EsWriter...
INFO: Closing spider (closespider_itemcount)...
   'item_scraped_count': 106,
```

### A pipeline that geocodes using the Google Geocoding API
```
$ curl "https://maps.googleapis.com/maps/api/geocode/json?sensor=false&address=london"
{
   "results" : [
         ...
         "formatted_address" : "London, UK",
         "geometry" : {
            ...
            "location" : {
               "lat" : 51.5073509,
               "lng" : -0.1277583
            },
            "location_type" : "APPROXIMATE",
            ...
   ],
   "status" : "OK"
}
```

```py
@defer.inlineCallbacks
def geocode(self, address):
   endpoint = 'http://web:9312/maps/api/geocode/json'

   parms = [('address', address), ('sensor', 'false')]
   response = yield treq.get(endpoint, params=parms)
   content = yield response.json()

   geo = content['results'][0]["geometry"]["location"]
   defer.returnValue({"lat": geo["lat"], "lon": geo["lng"]})
```

By using geocode(), process_item() becomes a single line as follows:

```py
item["location"] = yield self.geocode(item["address"][0])
```

Let's enable this pipeline by adding it to our settings' `ITEM_PIPELINES` with a priority number that is smaller than ES's so that ES gets our location values:

```py
ITEM_PIPELINES = {
    ...
    'properties.pipelines.geo.GeoPipeline': 400,
```

Let's run a quick crawl with debug data enabled:

```
$ scrapy crawl easy -s CLOSESPIDER_ITEMCOUNT=90 -L DEBUG
...
{'address': [u'Greenwich, London'],
...
 'image_urls': [u'http://web:9312/images/i06.jpg'],
 'location': {'lat': 51.482577, 'lon': -0.007659},
 'price': [1030.0],
...
```

Here is a simple and good enough implementation of a **throttling engine** using Twisted's techniques:

```py
class Throttler(object):
    def __init__(self, rate):
        self.queue = []
        self.looping_call = task.LoopingCall(self._allow_one)
        self.looping_call.start(1. / float(rate))

    def stop(self):
        self.looping_call.stop()

    def throttle(self):
        d = defer.Deferred()
        self.queue.append(d)
        return d

    def _allow_one(self):
        if self.queue:
            self.queue.pop(0).callback(None)

class GeoPipeline(object):
    def __init__(self, stats):
        self.throttler = Throttler(5)  # 5 Requests per second

    def close_spider(self, spider):
        self.throttler.stop()

class DeferredCache(object):
    def __init__(self, key_not_found_callback):
        self.records = {}
        self.deferreds_waiting = {}
        self.key_not_found_callback = key_not_found_callback

    @defer.inlineCallbacks
    def find(self, key):
        rv = defer.Deferred()

        if key in self.deferreds_waiting:
            self.deferreds_waiting[key].append(rv)
        else:
            self.deferreds_waiting[key] = [rv]

            if not key in self.records:
                try:
                    value = yield self.key_not_found_callback(key)
                    self.records[key] = lambda d: d.callback(value)
                except Exception as e:
                    self.records[key] = lambda d: d.errback(e)

            action = self.records[key]
            for d in self.deferreds_waiting.pop(key):
                reactor.callFromThread(action, d)

        value = yield rv
        defer.returnValue(value)
```

In `process_item()`, we look up using the cache as follows:

```py
def __init__(self, stats):
    self.cache = DeferredCache(self.cache_key_not_found_callback)

@defer.inlineCallbacks
def cache_key_not_found_callback(self, address):
    yield self.throttler.enqueue()
    value = yield self.geocode(address)
    defer.returnValue(value)

@defer.inlineCallbacks
def process_item(self, item, spider):
    item["location"] = yield self.cache.find(item["address"][0])
    defer.returnValue(item)
```

In order to enable this pipeline, we disable (comment out) our previous implementation and add this to ITEM_PIPELINES in settings.py as follows:

```
ITEM_PIPELINES = {
    'properties.pipelines.tidyup.TidyUp': 100,
    'properties.pipelines.es.EsWriter': 800,
    # DISABLE 'properties.pipelines.geo.GeoPipeline': 400,
    'properties.pipelines.geo2.GeoPipeline': 400,
}
```

We can then run the spider with the following code:

```
$ scrapy crawl easy -s CLOSESPIDER_ITEMCOUNT=1000
...
Scraped... 15.8 items/s, avg latency: 1.74 s and avg time in pipelines: 0.94 s
Scraped... 32.2 items/s, avg latency: 1.76 s and avg time in pipelines: 0.97 s
Scraped... 25.6 items/s, avg latency: 0.76 s and avg time in pipelines: 0.14 s
...
: Dumping Scrapy stats:...
   'geo_pipeline/misses': 35,
   'item_scraped_count': 1019,
```

### Enabling geoindexing on Elasticsearch
Here is an HTTP POST request (done using curl) that returns properties that have "Angel" in their title and are sorted by their distance from the point {51.54, -0.19}:

```json
$ curl http://es:9200/properties/property/_search -d '{
    "query" : {"term" : { "title" : "angel" } },
    "sort": [{"_geo_distance": {
        "location":      {"lat":  51.54, "lon": -0.19},
        "order":         "asc",
        "unit":          "km",
        "distance_type": "plane"
}}]}'
```

First, we save the autodetected mapping in a file as a starting point:

```
$ curl 'http://es:9200/properties/_mapping/property' > property.txt
```

Then we edit property.txt as follows:

```json
"location":{"properties":{"lat":{"type":"double"},"lon":{"type":"double"}}}
```

We replace this line of code with the following one:

```json
"location": {"type": "geo_point"}
```

We also delete `{"properties":{"mappings": and two }}` at the end of the file. We are then done with the file. We can now delete the old type and create a new one with our explicit schema as follows:

```
$ curl -XDELETE 'http://es:9200/properties'
$ curl -XPUT 'http://es:9200/properties'
$ curl -XPUT 'http://es:9200/properties/_mapping/property' --data @property.txt
```

We can now rerun a quick crawl, and we will be able to run the curl command that we saw earlier in this section and get results sorted by distance.

## Interfacing databases with standard Python clients
### A pipeline that writes to MySQL
```sql
$ mysql -h mysql -uroot -ppass
mysql> create database properties;
mysql> use properties
mysql> CREATE TABLE properties (
  url varchar(100) NOT NULL,
  title varchar(30),
  price DOUBLE,
  description varchar(30),
  PRIMARY KEY (url)
);
mysql> SELECT * FROM properties LIMIT 10;
Empty set (0.00 sec)
```

```py
from twisted.enterprise import adbapi
...
class MysqlWriter(object):
    ...
    def __init__(self, mysql_url):
        conn_kwargs = MysqlWriter.parse_mysql_url(mysql_url)
        self.dbpool = adbapi.ConnectionPool('MySQLdb',
                                            charset='utf8',
                                            use_unicode=True,
                                            connect_timeout=5,
                                            **conn_kwargs)

    def close_spider(self, spider):
        self.dbpool.close()

    @defer.inlineCallbacks
    def process_item(self, item, spider):
        try:
            yield self.dbpool.runInteraction(self.do_replace, item)
        except:
            print traceback.format_exc()

        defer.returnValue(item)

    @staticmethod
    def do_replace(tx, item):
        sql = """REPLACE INTO properties (url, title, price,
        description) VALUES (%s,%s,%s,%s)"""

        args = (
            item["url"][0][:100],
            item["title"][0][:30],
            item["price"][0],
            item["description"][0].replace("\r\n", " ")[:30]
        )

        tx.execute(sql, args)
```

In order to use this pipeline, we have to add it in our `ITEM_PIPELINES` dict in settings.py, as well as set the `MYSQL_PIPELINE_URL` appropriately:

```
ITEM_PIPELINES = { ...
    'properties.pipelines.mysql.MysqlWriter': 700,
...
MYSQL_PIPELINE_URL = 'mysql://root:pass@mysql/properties'
```

Execute the following command:

```sql
scrapy crawl easy -s CLOSESPIDER_ITEMCOUNT=1000

mysql> SELECT COUNT(*) FROM properties;
+----------+
|     1006 |
+----------+
mysql> SELECT * FROM properties LIMIT 4;
+------------------+--------------------------+--------+-----------+
| url              | title                    | price  | description
+------------------+--------------------------+--------+-----------+
| http://...0.html | Set Unique Family Well   | 334.39 | website c
| http://...1.html | Belsize Marylebone Shopp | 388.03 | features
| http://...2.html | Bathroom Fully Jubilee S | 365.85 | vibrant own
| http://...3.html | Residential Brentford Ot | 238.71 | go court
+------------------+--------------------------+--------+-----------+
4 rows in set (0.00 sec)
```

## Interfacing services using Twisted-specific clients
### A pipeline that reads/writes to Redis
```
$ redis-cli -h redis
redis:6379> info keyspace
# Keyspace
redis:6379> set key value
OK
redis:6379> info keyspace
# Keyspace
db0:keys=1,expires=0,avg_ttl=0
redis:6379> FLUSHALL
OK
redis:6379> info keyspace
# Keyspace
redis:6379> exit
```

We initialize our RedisCache pipeline as follows:

```py
from txredisapi import lazyConnectionPool

class RedisCache(object):
...
    def __init__(self, crawler, redis_url, redis_nm):
        self.redis_url = redis_url
        self.redis_nm = redis_nm

        args = RedisCache.parse_redis_url(redis_url)
        self.connection = lazyConnectionPool(connectTimeout=5,
                                             replyTimeout=5,
                                             **args)

        crawler.signals.connect(
                self.item_scraped,signal=signals.item_scraped)
```

We keep this cache simple by looking up and recording addresses and locations for every Item. This makes sense for Redis because it very often runs on the same server, which makes it very fast.

```py
@defer.inlineCallbacks
def process_item(self, item, spider):
    address = item["address"][0]
    key = self.redis_nm + ":" + address
    value = yield self.connection.get(key)
    if value:
        item["location"] = json.loads(value)
    defer.returnValue(item)
```

When an Item reaches the end of all our pipelines, we recapture it in order to store to Redis location values. Here is how we do this:

```py
from txredisapi import ConnectionError

   def item_scraped(self, item, spider):
       try:
           location = item["location"]
           value = json.dumps(location, ensure_ascii=False)
       except KeyError:
           return

       address = item["address"][0]
       key = self.redis_nm + ":" + address
       quiet = lambda failure: failure.trap(ConnectionError)
       return self.connection.set(key, value).addErrback(quiet)
```

To enable this pipeline, all we have to do is add it to our `ITEM_PIPELINES` settings and provide a `REDIS_PIPELINE_URL` inside `settings.py`.

```
ITEM_PIPELINES = { ...
    'properties.pipelines.redis.RedisCache': 300,
    'properties.pipelines.geo.GeoPipeline': 400,
...
REDIS_PIPELINE_URL = 'redis://redis:6379'
```

We can run this spider as usual. The first run will be similar to before, but any subsequent run will be as follows:

```
$ scrapy crawl easy -s CLOSESPIDER_ITEMCOUNT=100
...
INFO: Enabled item pipelines: TidyUp, RedisCache, GeoPipeline, MysqlWriter, EsWriter
...
Scraped... 0.0 items/s, avg latency: 0.00 s, time in pipelines: 0.00 s
Scraped... 21.2 items/s, avg latency: 0.78 s, time in pipelines: 0.15 s
Scraped... 24.2 items/s, avg latency: 0.82 s, time in pipelines: 0.16 s
...
INFO: Dumping Scrapy stats: {...
   'geo_pipeline/already_set': 106,
   'item_scraped_count': 106,
```

## Interfacing CPU-intensive, blocking, or legacy functionality
### A pipeline that performs CPU-intensive or blocking operations
Twisted provides thread pools that can be used to execute slow operations in some thread other than the main (Twisted's reactor) using the `reactor.callInThread()` API call. This means that the reactor will keep running its processing and reacting to events while the computation takes place.

```py
class UsingBlocking(object):
    @defer.inlineCallbacks
    def process_item(self, item, spider):
        price = item["price"][0]

        out = defer.Deferred()
        reactor.callInThread(self._do_calculation, price, out)

        item["price"][0] = yield out

        defer.returnValue(item)

    def _do_calculation(self, price, out):
        new_price = price + 1
        time.sleep(0.10)
        reactor.callFromThread(out.callback, new_price)
```

What happens if we have global state, for example counters, moving averages, and so on, that we need to use in our _do_calucation()?

To prevent this from happening, we have to use a lock, for example, Python's `threading.RLock()` recursive lock. Using it, we ensure that no two threads will execute the critical section it protects at the same time:

```py
class UsingBlocking(object):
    def __init__(self):
        ...
        self.lock = threading.RLock()
    ...
    def _do_calculation(self, price, out):
        with self.lock:
            self.beta += 1
            ...
            new_price = price + self.beta - self.delta + 1

        assert abs(new_price-price-1) < 0.01 ...
```

To use this pipeline, we just have to add it to the `ITEM_PIPELINES` setting inside `settings.py` as follows:

```
ITEM_PIPELINES = { ...
    'properties.pipelines.computation.UsingBlocking': 500,
```

### A pipeline that uses binaries or scripts
We can use the `reactor.spawnProcess()` API and the relevant `protocol.ProcessProtocol` to run executables of any kind.

```sh
#!/bin/bash
trap "" SIGINT
sleep 3

while read line
do
    # 4 per second
    sleep 0.25
    awk "BEGIN {print 1.20 * $line}"
done

$ properties/pipelines/legacy.sh
12 <- If you type this quickly you will wait ~3 seconds to get results
14.40
13 <- For further numbers you will notice just a slight delay
15.60
```

We start with a slightly simplified version:

```py
class CommandSlot(protocol.ProcessProtocol):
    def __init__(self, args):
        self._queue = []
        reactor.spawnProcess(self, args[0], args)

    def legacy_calculate(self, price):
        d = defer.Deferred()
        self._queue.append(d)
        self.transport.write("%f\n" % price)
        return d

    # Overriding from protocol.ProcessProtocol
    def outReceived(self, data):
        """Called when new output is received"""
        self._queue.pop(0).callback(float(data))

class Pricing(object):
    def __init__(self):
        self.slot = CommandSlot(['properties/pipelines/legacy.sh'])

    @defer.inlineCallbacks
    def process_item(self, item, spider):
        item["price"][0] = yield self.slot.legacy_calculate(item["price"][0])
       defer.returnValue(item)
```

We can enable this pipeline by adding it to `ITEM_PIPELINES` and running it as usual:

```
ITEM_PIPELINES = {...
    'properties.pipelines.legacy.Pricing': 600,
```

To increase it, all we need to do is modify the pipeline slightly to allow multiple such processes to run in parallel, as follows:

```py
class Pricing(object):
    def __init__(self):
        self.concurrency = 16
        args = ['properties/pipelines/legacy.sh']
        self.slots = [CommandSlot(args)
                      for i in xrange(self.concurrency)]
        self.rr = 0

    @defer.inlineCallbacks
    def process_item(self, item, spider):
        slot = self.slots[self.rr]
        self.rr = (self.rr + 1) % self.concurrency
        item["price"][0] = yield
                         slot.legacy_calculate(item["price"][0])
        defer.returnValue(item)
```

We can confirm it with a quick crawl as follows:

```
$ scrapy crawl easy -s CLOSESPIDER_ITEMCOUNT=1000
...
Scraped... 0.0 items/s, avg latency: 0.00 s and avg time in pipelines: 0.00 s
Scraped... 21.0 items/s, avg latency: 2.20 s and avg time in pipelines: 1.48 s
Scraped... 24.2 items/s, avg latency: 1.16 s and avg time in pipelines: 0.52 s
```

# Understanding Scrapy's Performance
## Scrapy's engine – an intuitive approach
A fundamental law for queue systems is Little's law, which asserts that the number of elements in the queuing system (N) in equilibrium is equal to the throughput of the system (T) multiplied by the total queuing/service time (S); N = T ∙ S. The other two forms, T = N / S and S = N / T, are also useful for calculations.

![1](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788_10_01.jpg)

Figure 1. Little's law, queuing systems, and pipes

### Cascading queuing systems
When you connect several pipes with different cross-sectional areas/throughputs one after the other, intuitively one can understand that the flow of the overall system will be limited by the flow of the narrowest (smallest throughput: `T`) pipe (see Figure 2).

![2](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788_10_02.jpg)

Figure 2. Cascading queuing systems with different capacities

### Scrapy's performance model
Let's return to Scrapy and see its performance model in detail (see Figure 3).

![3](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788_10_03.jpg)

Figure 3. Scrapy's performance model

Scrapy consists of the following:

- `The scheduler`: This is where multiple Request get queued until the downloader is ready to process them. They consist mostly of just URLs and, thus, are quite compact, which means that having many of them doesn't hurt that much and allows us to keep the downloader fully utilized in case of irregular flow of incoming Request.
- `The throttler`: This is a safety valve that feeds back from the scraper (the large tank) and if the aggregated size of Response in progress is larger than 5 MB it stops the flow of further Request into the downloader. This can cause unexpected performance fluctuations.
- `The downloader`: This is the most important component of Scrapy in terms of performance. It poses a complex limit on the number of Request it can perform in parallel. Its delay (the length of the pipe) is equal to the time it takes the remote server to respond, plus any network/operating system and Python/Twisted delays. We can adjust the number of parallel Requests, but we, typically, have little control over delays. The capacity of the downloader is limited by the CONCURRENT_REQUESTS* settings, as we shall soon see.
- `The Spider`: This is the part of the scraper that turns Response to Item and a further Request. We write these, and typically they aren't a performance bottleneck as long as we follow the rules.
- `Item pipelines`: This is the second part of the scraper that we write. Our spiders might generate hundreds of Items per Request, and only CONCURRENT_ITEMS will be processed in parallel at a time. This is important because if, for example, you're doing database accesses in your pipelines, you might unintentionally flood your database and the default (100) seems dangerously high.

## Our benchmark system
The code is somewhat cumbersome, and you can find it in `speed/spiders/speed.py`.

We will see the core metrics being printed as follows:

```
$ time scrapy crawl speed
...
INFO:  s/edule  d/load  scrape  p/line    done       mem
INFO:        0       0       0       0       0         0
INFO:     4938      14      16       0      32     16384
INFO:     4831      16       6       0     147      6144
...
INFO:      119      16      16       0    4849     16384
INFO:        2      16      12       0    4970     12288
...
real  0m46.561s
```

| Column | Metric |
| ------ | ------ |
| s/edule | len(engine.slot.scheduler.mqs) |
| d/load | len(engine.downloader.active) |
| scrape | len(engine.scraper.slot.active) |
| p/line | engine.scraper.slot.itemproc_size |
| done | stats.get_value('item_scraped_count') |
| mem | engine.scraper.slot.active_size |

## The standard performance model
![4](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788_10_05.jpg)

Figure 5. The standard performance model and some experimental results

Overall, if you need to complete a job of N `Request`s and our Spider is properly tuned, you should be able to complete it in:

$t_{job}=\frac{N \dot (t_{response} + t_{overhead})}{CONCURRENT\_REQUESTS}+t_{start/stop}$

$T=\frac{N}{t_{job}-t_{start/stop}}$

By running a long job of N Requests, we can measure the $t_{job}$ aggregated time and then it's straightforward to calculate T.

## Solving performance problems
### Case #1 – saturated CPU
![6](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788_10_06.jpg)

Figure 6. Performance flattens out as you increase concurrency beyond a certain level

### Case #2 – blocking code
![7](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788_10_07.jpg)

Figure 7. Blocking code invalidates concurrency in unpredictable ways

### Case #3 – "garbage" on the downloader
![8](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788_10_08.jpg)

Figure 8. Performance is defined by the spurious API requests

![9](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788_10_09.jpg)

Figure 9. It's perfectly fine to have long pipelines (check "industrial heat exchanger" in Google images).

### Case #4 – overflow due to many or large responses
![10](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788_10_10.jpg)

Figure 10. Irregular number of Requests on the downloader indicates Response size throttling

### Case #5 – overflow due to limited/excessive item concurrency
![11](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788_10_11.jpg)

Figure 11. Crawl time as a function of CONCURRENT_ITEMS

### Case #6 – the downloader doesn't have enough to do
![12](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788_10_12.jpg)

Figure 12. Throughput as a function of details and next page links per index page

## Troubleshooting flow
Start with a low value of `CONCURRENT_REQUESTS` and increase until just before you hit one of the following limits:

- CPU usage > 80-90%
- Source website latency increasing excessively
- Memory limit of 5 Mb of Responses in your scraper

At the same time also perform the following:

- Keep at least a few Requests at all times in the scheduler's queues (mqs/dqs) to prevent the downloader's URL starvation
- Never use any blocking code or CPU-intensive code

![13](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788_10_13.jpg)

Figure 13 summarizes the procedure of diagnosing and repairing Scrapy's performance problems.

# Distributed Crawling with Scrapyd and Real-Time Analytics
## Scrapyd
Let's first have a look on scrapyd's web interface that we can find at http://localhost:6800/.

![1](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_11_01.jpg)

Scrapyd's web interface

In order to do so, we must first deploy the spider to the scrapyd server. The first step is to modify the · configuration file as follows:

```
$ pwd
/root/book/ch03/properties
$ cat scrapy.cfg
...
[settings]
default = properties.settings

[deploy]
url = http://localhost:6800/
project = properties
```

Now, in order to deploy the spider, we use the scrapyd-deploy tool that is provided by scrapyd-client.

```
$ scrapyd-deploy
Packing version 1450044699
Deploying to project "properties" in http://localhost:6800/addversion.json
Server response (200):
{"status": "ok", "project": "properties", "version": "1450044699", "spiders": 3, "node_name": "dev"}
```

As the deployment was successful, we will be also able to see the project mentioned in the **Available projects** section in the main page of the scrapyd web interface.

```
$ curl http://localhost:6800/schedule.json -d project=properties -d spider=easy
{"status": "ok", "jobid": " d4df...", "node_name": "dev"}
```

If we turn back to the Jobs section of the web interface, we will be able to see the job running. We can use the **jobid schedule.json** that returns us to cancel the job using **cancel.json** a bit later:

```
$ curl http://localhost:6800/cancel.json -d project=properties -d job=d4df...
{"status": "ok", "prevstate": "running", "node_name": "dev"}
```

It's worth being aware of them by having a look in scrapyd's documentation at http://scrapyd.readthedocs.org/.

## Overview of our distributed system
![2](https://www.safaribooksonline.com/library/view/learning-scrapy/9781784399788/graphics/9788OS_11_02.jpg)

Overview of the system

### Sharded-index crawling
We will calculate the initial index IDs for each shard with the following expression:

```py
>>> map(lambda x: 1667 * x / 20, range(20))
[0, 83, 166, 250, 333, 416, 500, ...  1166, 1250, 1333, 1416, 1500, 1583]
```

Consequently, we set our start_urls to the following:

```py
start_urls = ['http://web:9312/properties/index_%05d.html' % id
              for id in map(lambda x: 1667 * x / 20, range(20))]
```

### Batching crawl URLs
Instead of dropping URLs as OffsiteMiddleware does, we will batch them and send them to scrapyds. It turns out that we can. Here's part of the implementation:

```py
def __init__(self, crawler):
    settings = crawler.settings
    self._target = settings.getint('DISTRIBUTED_TARGET_RULE', -1)
    self._seen = set()
    self._urls = []
    self._batch_size = settings.getint('DISTRIBUTED_BATCH_SIZE', 1000)
    ...

def process_spider_output(self, response, result, spider):
    for x in result:
        if not isinstance(x, Request):
            yield x
        else:
            rule = x.meta.get('rule')

            if rule == self._target:
                self._add_to_batch(spider, x)
            else:
                yield x

def _add_to_batch(self, spider, request):
    url = request.url
    if not url in self._seen:
        self._seen.add(url)
        self._urls.append(url)
        if len(self._urls) >= self._batch_size:
            self._flush_urls(spider)
```

We then add those URLs to the `_urls` list, and if its size exceeds `_batch_size` (the DISTRIBUTED_BATCH_SIZE setting), it triggers a call to `_flush_urls()`. This method provides the following key functionality:

```py
def __init__(self, crawler):
    ...
    self._targets = settings.get("DISTRIBUTED_TARGET_HOSTS")
    self._batch = 1
    self._project = settings.get('BOT_NAME')
    self._feed_uri = settings.get('DISTRIBUTED_TARGET_FEED_URL', None)
    self._scrapyd_submits_to_wait = []

def _flush_urls(self, spider):
    if not self._urls:
        return

    target = self._targets[(self._batch-1) % len(self._targets)]

    data = [
        ("project", self._project),
        ("spider", spider.name),
        ("setting", "FEED_URI=%s" % self._feed_uri),
        ("batch", str(self._batch)),
    ]

    json_urls = json.dumps(self._urls)
    data.append(("setting", "DISTRIBUTED_START_URLS=%s" % json_urls))

    d = treq.post("http://%s/schedule.json" % target,
                  data=data, timeout=5, persistent=False)

    self._scrapyd_submits_to_wait.append(d)

    self._urls = []
    self._batch += 1
```

We then form a POST request to scrapyd's **schedule.json**.

```
scrapy crawl distr \
-s DISTRIBUTED_START_URLS='[".../property_000000.html", ... ]' \
-s FEED_URI='ftp://anonymous@spark/%(batch)s_%(name)s_%(time)s.jl' \
-a batch=1
```

### Getting start URLs from settings
Frankly, we look at Scrapy's source code, find the way that CrawlSpider creates their Request and do exactly the same. In this case it is:

```py
def __init__(self, crawler):
    ...
    self._start_urls = settings.get('DISTRIBUTED_START_URLS', None)
    self.is_worker = self._start_urls is not None

def process_start_requests(self, start_requests, spider):
    if not self.is_worker:
        for x in start_requests:
            yield x
    else:
        for url in json.loads(self._start_urls):
            yield Request(url, spider._response_downloaded,
                          meta={'rule': self._target})
```

We enable it and set its settings in our settings.py:

```
SPIDER_MIDDLEWARES = {
    'properties.middlewares.Distributed': 100,
}
DISTRIBUTED_TARGET_RULE = 1
DISTRIBUTED_BATCH_SIZE = 2000
DISTRIBUTED_TARGET_FEED_URL = ("ftp://anonymous@spark/"
                               "%(batch)s_%(name)s_%(time)s.jl")
DISTRIBUTED_TARGET_HOSTS = [
    "scrapyd1:6800",
    "scrapyd2:6800",
    "scrapyd3:6800",
]
```

You can consider it as a default value that you can override on your spiders using a custom_settings attribute, for example:

```
custom_settings = {
    'DISTRIBUTED_TARGET_RULE': 3
}
```

We can perform a test run that will crawl a single page that is provided as a setting:

```
$ scrapy crawl distr -s \
DISTRIBUTED_START_URLS='["http://web:9312/properties/property_000000.html"]'
```

After this succeeds, we can try a more ambitious one, which crawls a page and FTPs it to our Spark server:

```
scrapy crawl distr -s \
DISTRIBUTED_START_URLS='["http://web:9312/properties/property_000000.html"]' \
-s FEED_URI='ftp://anonymous@spark/%(batch)s_%(name)s_%(time)s.jl' -a batch=12
```

### Deploy your project to scrapyd servers
In order to be able to deploy the spiders to our three scrapyd servers, we have to add them to our `scrapy.cfg` file. Each `[deploy:target-name]` section on this file defines a new deployment target:

```
$ pwd
/root/book/ch11/properties
$ cat scrapy.cfg
...
[deploy:scrapyd1]
url = http://scrapyd1:6800/
[deploy:scrapyd2]
url = http://scrapyd2:6800/
[deploy:scrapyd3]
url = http://scrapyd3:6800/
```

You can query the available targets with `scrapyd-deploy -l`:

```
$ scrapyd-deploy -l
scrapyd1             http://scrapyd1:6800/
scrapyd2             http://scrapyd2:6800/
scrapyd3             http://scrapyd3:6800/
```

It's easy to deploy to any of them with `scrapyd-deploy <target name>`:

```
$ scrapyd-deploy scrapyd1
Packing version 1449991257
Deploying to project "properties" in http://scrapyd1:6800/addversion.json
Server response (200):
{"status": "ok", "project": "properties", "version": "1449991257", "spiders": 2, "node_name": "scrapyd1"}
```

After this, if we query each of those servers using `scrapyd-deploy -L`, we can confirm that the project has been successfully deployed, as follows:

```
$ scrapyd-deploy -L scrapyd1
properties
```

## Creating our custom monitoring command
If you want to monitor the progress of your crawl across many scrapyd servers, you have to do it manually. This is a nice opportunity for us to exercise everything we've seen up to now to create a primitive Scrapy command, **scrapy monitor**, which monitors a set of scrapyd servers.

```py
class Command(ScrapyCommand):
    requires_project = True

    def run(self, args, opts):
        self._to_monitor = {}
        for name, target in self._get_targets().iteritems():
            if name in args:
               project = self.settings.get('BOT_NAME')
                url = target['url'] + "listjobs.json?project=" + project
               self._to_monitor[name] = url

        l = task.LoopingCall(self._monitor)
        l.start(5)  # call every 5 seconds

        reactor.run()
```
