![cover](https://img3.doubanio.com/lpic/s4606590.jpg)

    作者: Peter Morville / Jeffery Callender 
    出版社: O'Reilly Media
    副标题: Design for Discovery
    出版年: 2010-2-2
    页数: 192
    定价: USD 39.99
    装帧: Paperback
    ISBN: 9780596802271

- [豆瓣链接](https://book.douban.com/subject/4016085/)
- [safari链接](https://www.safaribooksonline.com/library/view/search-patterns/9781449380205/)

---

- [1.Pattern Recognition](#1pattern-recognition)
  - [Understanding Search](#understanding-search)
    - [The Box](#the-box)
      - [The Goal](#the-goal)
        - [Search](#search)
        - [Ask](#ask)
        - [Filter](#filter)
        - [Browse](#browse)
        - [Find](#find)
        - [Learn](#learn)
        - [Understand](#understand)
        - [Share](#share)
        - [Act](#act)
      - [The Engine](#the-engine)
- [2.The Anatomy of Search](#2the-anatomy-of-search)
  - [Users](#users)
    - [User Experience Honeycomb: Searcher’s Edition](#user-experience-honeycomb-searchers-edition)
  - [Interface](#interface)
  - [Engine](#engine)
    - [Learning + Collaboration](#learning--collaboration)
  - [Content](#content)
  - [Creators](#creators)
  - [Context](#context)
    - [Portal](#portal)
    - [Search](#search-1)
    - [Objects](#objects)
    - [All Together Now](#all-together-now)
- [3.Behavior](#3behavior)
  - [Patterns of Behavior](#patterns-of-behavior)
    - [Quit](#quit)
    - [Narrow](#narrow)
    - [Expand](#expand)
    - [Pearl Growing](#pearl-growing)
    - [Pogosticking](#pogosticking)
    - [Thrashing](#thrashing)
  - [Elements of Interaction](#elements-of-interaction)
  - [Principles of Design](#principles-of-design)
    - [Incremental Construction](#incremental-construction)
    - [Progressive Disclosure](#progressive-disclosure)
    - [Immediate Response](#immediate-response)
    - [Alternate Views](#alternate-views)
    - [Predictability](#predictability)
    - [Recognition Over Recall](#recognition-over-recall)
    - [Minimal Disruption](#minimal-disruption)
    - [Direct Manipulation](#direct-manipulation)
    - [Context of Use](#context-of-use)
- [4.Design Patterns](#4design-patterns)
  - [Autocomplete](#autocomplete)
  - [Best First](#best-first)
  - [Federated Search](#federated-search)
  - [Faceted Navigation](#faceted-navigation)
  - [Advanced Search](#advanced-search)
  - [Personalization](#personalization)
  - [Pagination](#pagination)
  - [Structured Results](#structured-results)

# 1.Pattern Recognition
## Understanding Search
### The Box
In search, the first ball in the air is a `box`. It’s the iconic symbol of search and a great place to start. 

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498350.png.jpg)

Figure 1-2. The iconic search box

The box comes in all colors, shapes, and sizes. It sports a variety of buttons and labels. 

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498352.png.jpg)

Figure 1-3. When is a box not a box?

On Flickr, we know we seek images, but we must learn how and why to query by tag and filter by interestingness.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498354.png)

Figure 1-4. There are many dialects in the language of search

As we begin to type, `autocomplete` offers to save time and typos, while `autosuggest` serves up Best Bets and related topics. Or, we can highlight a phrase in Firefox, drag and drop it into the search bar, and query a custom search engine using only our mouse.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498356.png.jpg)

Figure 1-5. Apple’s colorful version of autosuggest

iPhone users soon learn the rhythm of tap and type, understanding that the box has become subject to touch. Or we simply raise our phones to our ears and speak our search, relying on Google Mobile to derive what we want from who we are, where we stand, and what we say. No buttons. No typing. No clicks. Our identities, locations, and voices form a new kind of query that has us searching (and thinking) outside the box.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498358.png.jpg)

Figure 1-6. Google Mobile with Voice Search on the iPhone

Further reflection is inspired by the interplay between input and output. Often, the results are links and snippets, but sometimes they are answers to questions. If you ask nicely, Google will reply with weather forecasts, stock quotes, traffic maps, and sports scores.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498360.png)

Figure 1-7. Google presents structured results for special query types

**The box isn’t limited to search—it’s also a command-line interface that affords power and flexibility to users in the know. It’s a calculator. It’s a communicator. It’s a universal remote control. The box is a boundary object that links design, engineering, and marketing**. 

#### The Goal
Search is first and foremost about `findability`. The archetypal search is a quick lookup that leads from query to results to found object. It serves as a navigation shortcut that speeds our way from here to there. Search is the means to an end.

##### Search
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498364.png)

Figure 1-9. We search to find results

##### Ask
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498366.png.jpg)

Figure 1-10. We ask to find answers

In fact, the line between ask and search is fuzzy, **defined mostly by distinctions of syntax and semantics**. A query is simply a question without the ornament of natural language. When we ask and search, we seek to find. That is the goal.

##### Filter
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498368.png.jpg)

Figure 1-11. We use filters so the right stuff finds us

##### Browse
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498370.png)

Figure 1-12. Browsing involves wandering and wayfinding

##### Find
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498372.png.jpg)

Figure 1-13. We flow between modes

All these modes should be on the table when designing for findability. Each is but one tactic in support of a goal. Rather than prescribing tools and tasks, we must aim for (and beyond) the searchers’ intent. What do they want? What do they need?

**Search at its best is a conversation. It’s an iterative, interactive process where we find we learn**. The answer changes the question. The process moves the goal. Search has the power to suggest, define, refine, cross-sell, upsell, relate, and educate.

##### Learn
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498374.png)

Figure 1-14. In search, we find we learn

**Search also has the ability to enhance understanding. A search engine results page (SERP) is a custom map that’s built in response to a query**. It’s how we see what we’ve found. 

##### Understand
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498376.png.jpg)

Figure 1-15. Search helps us understand what we’ve found

We search on behalf of other people. We search with other people. We crowdsearch with Twitter and Mechanical Turk, distributing our queries (as whispers or shouts) to a networked community of searchers and solvers. Search can be a social experience in which we share goals, queries, and results. As designers, we must strive to support collaborative discovery. We must help people to search together.

##### Share
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498378.png.jpg)

Figure 1-16. We often search together

The goals of users may warrant other acts. While print, save, and share are most common, a variety of tasks may be integral to the process. Increasingly, on result pages, we can play music, watch videos, buy products, update calendars, and call contacts.

##### Act
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498380.png.jpg)

Figure 1-17. Users deserve actionable results

#### The Engine
For instance, there’s an engine called Evri, shown in Figure 1-18, that appears in the Washington Post’s website. At the end of each article, readers can learn more about relevant people, organizations, and topics.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498382.png.jpg)

Figure 1-18. Evri’s suggestions for an iPhone article

This reframing of search has produced a whole new generation of discovery tools and recommender systems. Last.fm, Pandora, Ambiently, and StumbleUpon are search without the box. We click, jump, and vote. Keywords are displaced by hearts and thumbs.

# 2.The Anatomy of Search
Our map to search features five elements: users, creators, content, engine, and interface. 

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498402.png.jpg)

Figure 2-1. The anatomy of search

## Users
Do our users care more about finding only the relevant results or all the relevant results? In search design, the two are inversely related. 

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498404.png.jpg)

Figure 2-2. The relevance seesaw

We should also consider expertise with respect to search in general and the domain in question. Let’s say we’re building a search application for health and medicine. Will most users (or our most important users) be familiar with medical terminology? And how about their digital literacy? Are they fluent or fumbling? It’s a common mistake to conflate these two types of mastery. 

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498406.png)

Figure 2-3. Expertise types

Type of search is another key variable. There’s a big difference between the simple lookup of `known-item search` and the dynamic learning of `exploratory search`. Google’s got lookup down. Fast, simple, relevant. If you know what you want, Google will find it in less than a second. It’s so fast, we use it for navigation, running queries even when we know the URL. But if you’re unsure what you need, Amazon offers a better model. `Faceted navigation` plus tools for recommendation help us learn. Search becomes an iterative, interactive experience where what we find changes what we seek. 

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498408.png.jpg)

Figure 2-4. Search modes

Of course, we must also consider platform, purpose, and context of use. Are we designing for desktops, laptops, televisions, kiosks, or mobiles in motion? 

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498410.png)

Figure 2-5. Context of use

### User Experience Honeycomb: Searcher’s Edition
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498412.png)

Figure 2-6. Qualities of the searcher’s experience

## Interface
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498414.png)

Figure 2-7. The interface includes query and results

In search, it’s helpful for creating and analyzing whole interfaces and their (perceived) affordances.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498416.png)

Figure 2-8. The Five Ws (and one H)

The search engine results page or SERP, as pictured in Figure 2-9 is among the most complex and important challenges to design.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498418.png.jpg)

Figure 2-9. Anatomy of a SERP

## Engine
### Learning + Collaboration
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498422.png)

Figure 2-11. Learning together

Organizations often cover the bases in terms of technology and finance but fail to press vendors on exactly what will be required to support their unique mix of features and content. A typical checklist may include the following:

- System architecture
  - Formal description of the hardware and software components, including crawlers, indexers, data models, and query parsers.
- Performance
  - How many simultaneous queries are supported? What’s the maximum number of sources? How about the size of the data repository?
- File formats
  - What types of content and data (e.g., HTML, PDF, mySQL) are supported? Can the system handle both structured and unstructured data?
- Integration
  - Is there a standards-based Web Services API for embedding search functionality in other sites and software? Is there a list of available connectors?
- Access control
  - Does the system support multiple levels of access for different user types and individuals? How does it manage privacy and security?
- Features
  - How does the system handle full text and metadata? Does it support Boolean operators, wildcards, stemming, stop words, phrase and proximity searching, and spellcheck? What algorithms are used for ranking? What are the options for query refinement? Can results be saved, printed, and shared?
- Implementation
  - What sort of expertise is required for installation, configuration, and maintenance? How does the vendor handle training and support?
- Pricing model
  - Is the product priced by data or activity volume, CPUs, features, and/or number of unique applications? How about support, maintenance, and professional services fees? What’s the total cost of ownership?
- Vendor credentials
  - How long has the vendor been in business? How are they positioned in the market? Can we see their financials and customer references?

A supplemental checklist that’s informed by an information architecture strategy and empathy for the user might include:

- Speed
  - What will it take to ensure subsecond response in the real world? It’s worth asking this question early and often. Don’t take “slow” for an answer!
- Relevance tuning
  - How are results ranked? Is it possible to adjust the settings to allow for popularity, content type, date, and diversity?
- Navigation and filtering
  - Is it easy to customize sort order and limit options? Is there native support for faceted navigation? Is it fast?
- Federated search
  - How does the system handle the simultaneous search of multiple databases or indexes? What is the impact on speed? Is it possible to merge several indexes into one to dramatically improve performance?
- Linguistic toolset
  - Is there support for thesaurus integration and crosswalking between vocabularies? How about autocategorization and entity extraction?
- Search analytics
  - What tools are provided for measuring and understanding user behavior? Is there an API that supports sharing and repurposing of this data?

## Content
For starters, the availability (or lack thereof) of full text and metadata shapes the what and how of search.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498424.png.jpg)

Figure 2-12. Relative value of text and metadata

Since complexity of the information retrieval challenge increases exponentially with linear increases in volume, we know the most dramatic way to improve performance is to search less content.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498426.png)

Figure 2-13. To search better, search less

So, early in the design process, it’s worth asking two questions. First, can we shrink the search space by removing ROT, content that’s redundant or outdated or trivial? By crafting a content policy that defines what’s in and out, then rigorously weeding their collections, organizations are often able to cut what’s searched by half. Second, can we add metadata fields that let users slice content into smaller sections? Even a massive article database becomes manageable when users can limit searches by topic and date.

## Creators
Designers of search applications must no longer accept content in its current state. It’s time to shake the tree. Questions we should ask include:

- Who are the current (and potential) creators of content?
- How can we motivate them to improve quality and quantity?
- What tools and processes will make publishing faster and easier?
- How can we enlist users in content creation and organization?
- How can we share analytics to inspire both use and cocreation?

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498428.png.jpg)

Figure 2-14. Knowledge management and search

## Context
In the context of websites, three key areas often emerge as powerful fulcra with the potential to move mountains: the portal, search system, and destination objects, as shown in Figure 2-16.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498432.png.jpg)

Figure 2-16. Three fulcra of large websites

A concept map, as shown in Figure 2-17, can help us to realize this big picture. The goal is to capture the key elements so we can begin to discuss how they relate.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498434.png.jpg)

Figure 2-17. A concept map

### Portal
The portal, which includes the home page and the top few layers of the website, often presents an opportunity to improve the user experience and the brand. 

The portal, in conjunction with a content management system, can also serve as a powerful tool for aligning staff efforts and incentives with user needs and goals.

### Search
Sites and services as diverse as Amazon, Google, Flickr, and Wikipedia have all developed solutions that work despite their lack of centralized control over content and metadata. They have succeeded by embracing search-centered solutions that recognize that searching and browsing must be used in combination to help people effectively navigate. These solutions typically possess the following three qualities:

- Federated
  - Since most users don’t know where to look, the site should allow people to perform searches across all of its content. This should not preclude advanced, focused queries on particular collections or databases.
- Faceted
  - The site should embrace faceted navigation (with flexible search scopes) as widely as possible so that users can move fluidly from searching the site to searching a content collection or a product catalog without having to start over or learn a new interface. Global facets might include topic, format, date, and author. Each database might present additional category-specific facets to support narrowing and filtering.
- Fast
  - The organization must invest in the hardware, software, and staff necessary to deliver subsecond response times. Speed is absolutely critical in allowing users to fully engage in an iterative, interactive search experience.

### Objects
Similarly, our big organization has an opportunity to make its content more social (viral) and findable by adopting best practices in search engine optimization and social media design. This requires redesigning the objects of search to serve as destinations, gateways, and subjects of conversation. 

Photos are easily findable via Google or Flickr’s own search system, and each photo offers many options for finding similar photos or for finding other photos from the same source, set, pool, or collection. Plus, users are invited to add tags, notes, and comments. Each photo is a catalyst for conversation and community. Additionally, the object isn’t stuck on the page. Users can share photos across multiple devices, channels, and services. We can order prints or add our image to stickers, calendars, business cards, T-shirts, magnets, puzzles, and mugs.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498438.png.jpg)

Figure 2-19. Flickr user model

### All Together Now
By working hard to serve users, refine the interface, tune the engine, enhance the content, and motivate creators while simultaneously striving to leverage and transform the wider context, Amazon and a handful of other pioneering firms are showing us how to make search better.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498440.png.jpg)

Figure 2-20. A map of Amazon

# 3.Behavior
## Patterns of Behavior
### Quit
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498446.png)

Figure 3-2. Quit is the most common pattern

In Figure 3-3 Yale University fails to state the system status clearly (e.g., “No results were found”), but otherwise provides a good combination of feedback and next steps. Links to popular pages and popular searches might also be helpful.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498448.png.jpg)

Figure 3-3. No results at Yale

On the other hand, if we can help users avoid “No Results” in the first place, that’s even better. As Figure 3-4 shows, we’re less likely to reach a dead end at Amazon, thanks to the autoexpand strategy of `partial match`, in which unrecognized keywords are omitted from the query string.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498450.png.jpg)

Figure 3-4. Amazon works to avoid no results

### Narrow
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498452.png)

Figure 3-5. Query refinement

`Faceted navigation` puts metadata on the map. As Figure 3-6 shows, Artist Rising lets us clarify whether we want drinking bars (places) or lemon bars (cuisine) and photos or paintings. Plus, we can refine by searching within these results. And even Sort provides a way to limit what we see. Artist Rising offers us many ways to narrow.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498454.png.jpg)

Figure 3-6. Faceted navigation puts metadata on the map

### Expand
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498456.png)

Figure 3-7. Casting the net wider

It’s most commonly seen in the thesaurus browsers of library databases, as shown in Figure 3-8 where structured vocabularies and the risky expectation of searcher expertise afford designers a sense of freedom to reveal the hierarchy (and potential polyhierarchy) that connects to broader terms.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498458.png.jpg)

Figure 3-8. CSA Illumina’s thesaurus browser

Rather than a formal hierarchy, search applications often let users expand (or at least explore) by showing related terms within matching categories, as shown in Figure 3-9.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498460.png.jpg)

Figure 3-9. Matching categories and related terms

### Pearl Growing
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498462.png)

Figure 3-10. A strategy for finding similar results

Fortunately, pearl growing is also a strategy we can spread by embedding it within the interface. Google’s Similar link is the most ubiquitous example.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498464.png.jpg)

Figure 3-11. Find similar

Similarly, music recommender systems make it easy to find songs we like by comparing the attributes, ratings, and collaborative filtering data of songs we know and those we don’t. Last.fm and Pandora rely heavily on up and down ratings of individual songs.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498466.png.jpg)

Figure 3-12. Similar controls at Last.fm and Pandora

### Pogosticking
Other patterns (or antipatterns) are produced by bad design. For instance, repetitive bouncing between the SERP and individual results is known as pogosticking. A little pogosticking means users are sampling results. That’s to be expected, but when it happens a lot, it’s not sampling; it’s a symptom.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498470.png)

Figure 3-14. Pogosticking is an antipattern

Perhaps our snippets and metadata lack the scent users need to effectively scan results, so they must visit each one in turn. Or, if sequential viewing of results is a desirable pattern, we need solutions that support this behavior. Cooliris, shown in Figure 3-15, uses the iPhone’s touchscreen to let users flick through image results in linear fashion.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498472.png.jpg)

Figure 3-15. No pogosticking at Cooliris

Lands’ End, shown in Figure 3-16, ensures the metadata and features that users need are available in the gallery of search results. It doesn’t stuff too many results on the page at the expense of rich summaries. A clear product image, displaying the sole on rollover, inline color selection, the name, and the price are just the right mix for most users.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498474.png.jpg)

Figure 3-16. Gallery of search results at Lands’ End

### Thrashing
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498476.png.jpg)

Figure 3-17. Thrashing derives from the anchoring bias

In thrashing, a design flaw resides in users’ heads in the form of the anchoring bias. We set the anchor with our initial query, and then, despite poor results, we insist on small variations of the flawed search phrase rather than trying new approaches.

For instance, a user searching for a concert may try many queries that begin with the (misspelled) nickname rather than switching to the performer’s full name.

```
sachmo
sachmo concert
sachmo jazz concert
sachmo jazz festival
sachmo music festival
sachmo summer celebration
```

In Figure 3-18, Yahoo! illustrates two ways to break this pattern. First, `autocomplete` helps users avoid typos and get the query right to begin with. Second, `autosuggest` can recommend related queries that don’t include the original search term.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498478.png.jpg)

Figure 3-18. Autocomplete and autosuggest at Yahoo!

## Elements of Interaction
The distinct features and the relationships between the iPod in your palm, the iTunes desktop application, and the iTunes Store on the Web serve as a familiar model. Apple’s genius was to locate key functions on the right platforms. As shown in Figure 3-22, we play on the device, manage on the desktop, and buy at the store.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498486.png.jpg)

Figure 3-22. Apple’s many interfaces

## Principles of Design
In the first 250 milliseconds, the preattentive variables of size, shape, position, alignment, orientation, color, and texture have already worked their magic. A well-crafted interface reveals its core features and layout to our subconscious before we have time to think.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498492.png.jpg)

Figure 3-25. Preattentive variables at the BBC

### Incremental Construction
People will build great queries incrementally, one click at a time, if we can get them past the start line and always offer at least one next step.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498494.png.jpg)

Figure 3-26. Forgiving format at Amazon

### Progressive Disclosure
Google Maps offers a good example of progressive disclosure and careful adherence to the user dictate: “Show me only what I want.” The initial interface is a basic map with an overlay for popular tasks like getting directions. A click adds a colorful traffic layer and a hover reveals more options. Google designs disclosures that are responsive to users.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498496.png.jpg)

Figure 3-27. Progressive disclosure in Google Maps

`Faceted navigation` is a similarly progressive design pattern. Users can begin with a few keywords and end with a few results. They can ignore the facets if they choose, but the power of incremental query refinement is available, plus the quantity and specificity of metadata fields often snowballs helpfully as they go. Facets allow people to learn search on gentle slopes rather than being forced into the big step from the bunny hills of the basic interface to the black diamond mode of advanced search.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498498.png.jpg)

Figure 3-28. Faceted navigation at the Triangle Research Libraries

### Immediate Response
Volkswagen UK employs a wonderfully subtle form of feedback. During active control of a slider, the options to be excluded from the results fade to gray. Then, upon release of the mouse button, the faded options disappear, and the remaining cars gracefully shift into position within the smaller result set. It takes a while for this rich Internet application to load, but once running, it’s a smooth ride with great performance and quick response.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498500.png.jpg)

Figure 3-29. Immediate response at Volkswagen UK

### Alternate Views
For many applications, the optimal view differs by user and task. One size does not fit all. This is certainly true in search, where the ideal mix of metadata depends upon user intent.

Viewzi takes alternate views to the extreme. This intriguing application provides the basic choice between small and large images, but it doesn’t stop there. Viewzi offers more than 18 different ways to view search results. Options include simple text, image grid, timeline, tag cloud, and a fashionable cover flow interface for browsing web screenshots.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498502.png.jpg)

Figure 3-30. Multiple views with Viewzi

`Sort order` also provides users with the choice of alternate views. Since users rarely explore beyond the first page of results, sorts act much like filters.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498504.png.jpg)

Figure 3-31. Controls for sort order

Another alternate view worth reflection is that of those who can’t see. As with other features of an application, search should be universally accessible. Clearly, this means that search and result interfaces must be easy to navigate with `text-to-speech` and Braille output screen readers.

### Predictability
In search, we need predictable features and results. Controls must be easy to discover and understand. The Gap, for instance, uses a simple hover invitation to feed-forward the Quick Look feature, which leads to an overlay instead of the detailed product page. Since the invite appears in the natural flow of result selection, it’s impossible to miss.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498506.png.jpg)

Figure 3-32. Hover invitation at The Gap

In contrast, Bloomberg’s rotate-to-view feature is less discoverable, but once found it works well, because it’s simple and consistent. When a gesture works the same way throughout an application, habituation improves efficiency. Users become comfortable with that gesture and know what to expect.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498508.png.jpg)

Figure 3-33. Rotate to view at Bloomberg

### Recognition Over Recall
Recognition is triggered by context. Users couldn’t recall commands, but they could easily recognize buttons and links.It’s a major reason why we shifted from CLI to GUI. 

In search, the first step is to make valuable options visible.Second, we must offer tools that reduce users’ short-term memory load. 

Sometimes the path to better recognition in search is browse. Search requires that we know what we want and have the words to describe our needs. In contrast, browse illustrates what’s available, shows the vocabulary, and reminds us of things we might need.

In mobile, browse is especially useful, because it takes time to type and we’re unsure what to search for. Applications like Where and AroundMe don’t require users to remember the types of things to be found. Instead, we can browse the map or a traditional taxonomy. We may not recall what we want, but we’ll recognize it when we see it.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498512.png.jpg)

Figure 3-35. Mobile browsing with Where and AroundMe

### Minimal Disruption
In light of our feeble memories, not to mention our general impatience and intolerance for change, it’s often best (when possible) to stay on the page. `Overlays`, `inlays`, `tabs`, `virtual scrolling` and `panning`, and `inline paging` are all creative ways to bring additional content and controls into the picture without shifting the frame.

Netflix takes convenience a step further. In addition to a detail overlay, Netflix serves up actionable results, so we can add items to the Instant Queue or start playing a movie, all without leaving the results page.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498514.png.jpg)

Figure 3-36. A detail overlay and actionable results at Netflix

### Direct Manipulation
Yet another factor in the success of GUI is the principle of direct manipulation. Interfaces that enable users to interact directly with visible objects are more easily learned and used. Sometimes we rely on real-world metaphors. We sort files on the desktop and drag them into the trash can. Other times, our idioms have no analog, yet direct manipulation drives them into our muscle memory. Our bodies remember what our minds forget.

Searchme lets users drag results into custom search stacks for later review or for sharing with friends and colleagues. There’s also an Add to Stack link, but it lacks the visual and tactile gratification of drag-and-drop.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498516.png.jpg)

Figure 3-37. Drag results to stacks at Searchme

The use of drag-and-drop invokes `Fitts’ Law`: the time to acquire a target is a function of the distance to and size of the target. This means we must think carefully about the size and placement of the drop zone. Many users have a hard time getting the mouse (and cursor or drag handle) into just the right place, especially while holding down the mouse button.

The pie menu (also known as a radial menu) is an interesting alternative. A music search engine named Songza illustrates the benefits. First, it’s self-revealing. When a user clicks on a result, the menu appears. Second, it plays well with Fitts’ Law. The options, including those within the nested menus, are near the original point of interaction. Third, it’s a gestural interface with the advantages of direct manipulation. Expert users can rely on muscle memory to select options without glancing at menus.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498518.png.jpg)

Figure 3-38. Songza’s self-revealing pie menu

### Context of Use
In design, `context` is a seven-letter word that means everything. It’s not enough for our applications to work great in the lab; they must succeed in the real world. This means we must consider users, goals, content, features, platform, and environment. An elderly man with fat fingers may have a hard time using the tiny touch targets of a soft keyboard to search for a nearby restaurant while bouncing on a bus. That’s why the iPhone employs iceberg tips and adaptive targets to make writing a little easier. It’s also why Google Mobile uses search history, autosuggest, and voice search to let us type a little less.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498520.png.jpg)

Figure 3-39. Adaptive solutions on the iPhone

# 4.Design Patterns
## Autocomplete
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498536.png)

Figure 4-8. The Autocomplete design pattern

It’s a pattern that first emerged within the Help functions of desktop applications. This solution solves several very common problems. First, typing takes time. Second, users can’t spell well. Third, we’re often at a loss for words. 

`Autocomplete` is now a familiar fixture across desktop, web, and mobile platforms (Figure 4-1).

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498522.png)

Figure 4-1. Autocomplete in a desktop application

A major prerequisite of autocomplete is a source of data for suggestions. Classic desktop applications rely on an alphabetical index of help topics. Google draws from a user’s personal search history and from the collective search behavior of many users (Figure 4-2). Firefox (also shown in Figure 4-2) taps browsing history and bookmarks. 

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498524.png.jpg)

Figure 4-2. Autocomplete in Google and Firefox

Yahoo! steps beyond autocomplete to autosuggest, shown in Figure 4-3 by tapping query reformulation data to recommend related queries that need not include the original search term.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498526.png.jpg)

Figure 4-3. Autocomplete and autosuggest

`Autosuggest` can help users to pivot by highlighting alternate concepts and relevant verticals. It’s worth noting that while autocomplete and autosuggest are distinct concepts, most applications blend them together for a small footprint. Consequently, in this book, we’ve bundled both under the autocomplete pattern.

Yahoo! has also experimented with visual autocomplete, shown in Figure 4-4. Sometimes users are able to clarify better with an image than a word.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498528.png.jpg)

Figure 4-4. Visual autocomplete

Reference sites like Answers.com, shown in Figure 4-5 draw upon a structured database to support query disambiguation, helping users to clarify before they search.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498530.png.jpg)

Figure 4-5. Autocomplete at Answers.com

For instance, autocomplete isn’t only about typing and spelling. Suggestions help us when we’re not sure what to seek. On websites, the information architecture provides users with structural and semantic clues that precede and inform the search. Similarly, in mobile applications, we use categories and icons to invite users to explore with a click. In this way, browse complements search by getting folks started and helping them learn what to seek.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498534.png.jpg)

Figure 4-7. Browse options in Citysearch and Dopplr

## Best First
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498548.png.jpg)

Figure 4-14. The best first design pattern

It’s a safe bet that the top three results will draw 80 percent of the attention. The remaining results on the first page may each earn a few percentage points.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498540.png.jpg)

Figure 4-10. Best first with Google

Consequently, best first must be a top priority during search engine selection.The algorithms should account for:

- Relevance
  - These algorithms focus on topical relevance or aboutness. They aim to match the query keywords to the text of the content and metadata. Effective algorithms account for term order, proximity, location, frequency, and document length. An exact phrase match in a short title is worth more than an AND co-occurrence in a long body. A phrase that repeats on a page but is rare on the site merits extra weight. Relevance algorithms must also manage the transformation of text queries to account for plurals and other word variants (e.g., poet and poetry). Tuning may be required to get the right balance of precision and recall. Relevance is typically the default setting and is often in truth a hybrid that combines the inputs of multiple algorithms into a balanced solution.
- Popularity
  - In most contexts, social data can deliver a big boost to semantic algorithms. Google’s PageRank, which counts links as votes, was the first mainstream success. Today, popularity is typically a multialgorithmic measure. At Flickr, a photo’s interestingness derives from views, comments, notes, bookmarks, favorites, and so on. At Amazon, users can sort by Bestselling or Best Reviews, but even when they sort by relevance, social data influences the results.
- Date
  - Sorting by date is rarely a good default, but it is a useful option, especially for news and email applications in which reverse chronological order (newest first) is relatively common. In many cases, the date of publication or modification can serve as a valuable input into the general-purpose relevance algorithm by improving the freshness of top results.
- Format
  - In pure form, format and content type are most useful as filters, allowing users to view only images, videos, or news. However, they can also help to boost the best results. For instance, on an intranet, HTML and PDF documents may be more polished than .doc or .xls files. In such cases, application-specific tuning that brings the best formats to the top is extremely valuable.
- Personalization
  - A user’s search history, social network, or current location (online or off) are just a few inputs that might influence the order of results. We’ll delve into this topic when we explore the personalized search pattern. For now, let’s just note that personalization is at least as difficult as it is desirable.
- Diversity
  - In search, it’s easy to get too much of a good thing. Diversity algorithms guard against redundant results and support query clarification and refinement by surfacing distinct meanings (e.g., apple and AAPL) and formats. Application-specific tuning delivers the right balance and a nice blend of results.

## Federated Search
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498556.png.jpg)

Figure 4-18. The federated search design pattern

By definition, federated search involves the simultaneous search of multiple databases or collections.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498552.png.jpg)

Figure 4-16. Federated search at Kosmix

## Faceted Navigation
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498574.png)

Figure 4-27. The faceted navigation design pattern

Also called `guided navigation` and `faceted search`, the faceted navigation model leverages metadata fields and values to provide users with visible options for clarifying and refining queries.

Figure 4-19 illustrates a successful implementation of faceted navigation as a model for interacting with the catalogs of several academic libraries. Faceted navigation is not simply a feature to check off a list. Success requires painstaking attention to detail and an appreciation for the vast array of possibilities for interaction design. For instance, the libraries run collapsible facets down the left. Only the most relevant facets (subject, format, location) are open. Most are closed by default. Each open facet reveals only the top four or five most heavily populated values. This allows for a small facet footprint that frees up plenty of space on the main stage for the results themselves. The number of matching results for each value (shown within parentheses) is a key element of the map, as is the reformulation of search terms and selected values as stacking breadcrumbs, which let users view and modify their current search parameters.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498558.png.jpg)

Figure 4-19. Searching library catalogs with faceted navigation

For instance, applications rely on a mix of `scented widgets` for viewing and interacting with facet values, and some shift facet selectors to the top or right rather than the left.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498560.png.jpg)

Figure 4-20. A variety of scented widgets

Presenting facets along the top draws added attention to the narrowing facility. Given massive result sets, this is an effective way to highlight the data structure and draw users into filtering. 

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498562.png.jpg)

Figure 4-21. Faceted navigation puts metadata on the map

As shown in Figure 4-22, adaptive facets let controls conform to the content as users shift between categories and drill down within collections.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498564.png.jpg)

Figure 4-22. Amazon’s adaptive facets

In contrast to the relatively mature design space of the desktop Web, mobile is a platform where standards for faceted navigation have yet to emerge. Clearly, tiny screens preclude the established model. There’s insufficient space to present facets and values alongside results. Ever the pioneer, Amazon is among the first to design a mainstream application that adds faceted navigation to mobile search. As Figure 4-23 shows, it features an iterative model that requires more steps than ideal, but it’s a move in the right direction. As mobile search crosses the chasm, users will expect the features and functions to which they’ve become accustomed on the desktop, and first and foremost outside of the box, they will absolutely, positively need to narrow.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498566.png.jpg)

Figure 4-23. Faceted navigation on Amazon Mobile

Across all platforms, there are some qualifications and questions worth review. First, we’ve been using the term "faceted navigation” rather loosely. Formal definitions of facets may exclude simple fields and `filters`, but discrimination is unwarranted in practice, provided that filters operate independently and users can add or remove them in arbitrary order in concert with the updating of results.

On the other hand, the distinction between `faceted navigation` and `parametric search` is relevant. In parametric search applications, users specify their search parameters up front using a variety of controls such as checkboxes, pull-downs, and sliders to construct what effectively is an advanced `Boolean query`. Unfortunately, it’s hard for users to set several parameters at once, especially since many combinations will produce zero results.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498568.png.jpg)

Figure 4-24. Parametric problems at Snooth

## Advanced Search
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498584.png)

Figure 4-32. The advanced search design pattern

Is it a user-friendly query builder for novices or a power tool for experts? Many interfaces try (and fail) to be both. For instance, isn’t it fair to assume that users who understand what “exact phrase” means also know to use quotation marks to specify such a search? The main problem with Boolean isn’t the syntax, it’s the logic. And even the plain language shown in Figure 4-28 is unlikely to help the few novices who brave the intimidating realm of advanced search.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498576.png.jpg)

Figure 4-28. Advanced search at Genentech

Interestingly, Exalead, shown in Figure 4-29, combines help and advanced search without asking users to leave. A click on Advanced Search launches an interactive menu below the box. It’s unconventional and a little clumsy, but definitely worth a look.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498578.png.jpg)

Figure 4-29. Exalead’s integrated Help and Advanced Search

What’s the basic interface missing? How else might users wish to search? These are the questions that lead to innovations like Midomi’s search by singing, GazoPa’s discover by drawing, and Etsy’s fabulously fun feature, explore by color.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498582.png.jpg)

Figure 4-31. Etsy’s explore by color

## Personalization
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498598.png)

Figure 4-39. The personalization design pattern

In short, personalization is a dish best served simple. Only in limited contexts will past performance predict desired future results. The query is the clearest and most timely signal of intent. It’s a concise expression of what users need right now. History, social data, and location (online and off) can sometimes boost that signal, but for practical and ethical reasons, these personal algorithms should be transparent and open to override. When it works, personalization can play well with other patterns. In particular, it informs the suggestions of autocomplete and the algorithms of best first. Often, however, personalization must take a back seat to explicit, dynamic customization in the form of faceted navigation. 

## Pagination
![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498618.png)

Figure 4-49. The pagination design pattern

Google established the most popular pattern in the form of 10 blue links.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498600.png.jpg)

Figure 4-40. Ten blue links

`Snippets` are the heart and soul of search results. To pinch a phrase from multitouch, the content is the interface. The snippet reveals the aboutness of each result while also serving as the link to live and cached versions and to similar results. A purple link means you’ve already visited, an important and helpful clue for determining the next click. The two lines of text are selected for optimal scent. They provide a concise summary of the result or a brief excerpt with the keywords in context. A URL offers hints about the source and subject of the result. And throughout the snippet, query keywords are highlighted to reveal the reason for inclusion.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498602.png.jpg)

Figure 4-41. A Google snippet

Bing, shown in Figure 4-42, takes snippets a step further by presenting additional text and links from the destination site whenever a user hovers over a particular search result.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498604.png.jpg)

Figure 4-42. Bing’s preview feature

Of course, the anatomy of a snippet must adapt to fit each platform, format, and context. In mobile, snippets must be short. In reference and news and enterprise applications, URLs may be useless. And for images and video, a picture’s worth a thousand words.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498606.png.jpg)

Figure 4-43. Snippet diversity

At Yahoo! Shopping, users can choose whether they see 15, 30, or 45 results in list or grid view. They also have a wide variety of sort options and can select multiple items for a side-by-side comparison.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498610.png.jpg)

When users advance to the next set of results, the page refresh often disrupts flow. `Inline paging` is one solution. At Endless.com, for instance, when users advance to the next result page, the old snippets fade out and new ones appear. The rest of the interface stays stable.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498612.png.jpg)

Figure 4-46. Inline paging at Endless.com

Several solutions are currently employed in mobile. Apple’s iTunes offers to Show 25 More at the end of each list. Amazon abolishes paging with virtual scrolling. Progressive loading ensures that the first few results are shown immediately, then, as users scroll down, more results load automatically. Kayak appears to load all matching flights, but sort and filter options are available to refine results and avoid endless scrolling.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498614.png.jpg)

Figure 4-47. Mobile pagination patterns

`Infinite scroll` and `inline paging` offer clear benefits, but they come at a cost. First, they’re simply more expensive to implement. Second, they may initially confuse users who have become used to the standard model. Third, they may frustrate attempts to bookmark or share a link to a specific set of results.

We must find a balance between the richness of each snippet and the number of results per page. That is, unless our application affords the freedom to try something unorthodox, like a `zooming user interface` (ZUI) that positions all results within an infinite virtual desktop.

![](https://learning.oreilly.com/library/view/search-patterns/9781449380205/httpatomoreillycomsourceoreillyimages498616.png.jpg)

Figure 4-48. Hard Rock’s zooming user interface

## Structured Results


















