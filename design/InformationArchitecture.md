![cover](https://img9.doubanio.com/view/subject/l/public/s29451535.jpg)

    作者: Louis Rosenfeld / Peter Morville / Jorge Arango
    出版社: O'Reilly Media
    副标题: For the Web and Beyond
    出版年: 2015-10-11
    页数: 486
    定价: USD 44.99
    装帧: Paperback
    ISBN: 9781491911686

- [豆瓣](https://book.douban.com/subject/26632545/)
- [oreilly](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/)

---

- [I.Introducing Information Architecture](#iintroducing-information-architecture)
  - [1.The Problems That Information Architecture Addresses](#1the-problems-that-information-architecture-addresses)
    - [Recap](#recap)
  - [2.Defining Information Architecture](#2defining-information-architecture)
    - [Definitions](#definitions)
    - [Toward a Damned Good Information Architecture](#toward-a-damned-good-information-architecture)
  - [3.Design for Finding](#3design-for-finding)
    - [The “Too-Simple” Information Model](#the-too-simple-information-model)
    - [Information Needs](#information-needs)
    - [Information-Seeking Behaviors](#information-seeking-behaviors)
    - [Recap](#recap-1)
  - [4.Design for Understanding](#4design-for-understanding)
    - [A Sense of Place](#a-sense-of-place)
    - [Places Made of Information](#places-made-of-information)
    - [Recap](#recap-2)
- [II.Basic Principles of Information Architecture](#iibasic-principles-of-information-architecture)
  - [5.The Anatomy of an Information Architecture](#5the-anatomy-of-an-information-architecture)
    - [Visualizing Information Architecture](#visualizing-information-architecture)
    - [Top-Down Information Architecture](#top-down-information-architecture)
    - [Bottom-Up Information Architecture](#bottom-up-information-architecture)
    - [Invisible Information Architecture](#invisible-information-architecture)
    - [Information Architecture Components](#information-architecture-components)
      - [Browsing Aids](#browsing-aids)
      - [Search Aids](#search-aids)
      - [Content and Tasks](#content-and-tasks)
      - [“Invisible” Components](#invisible-components)
    - [Recap](#recap-3)
  - [6.Organization Systems](#6organization-systems)
    - [Challenges of Organizing Information](#challenges-of-organizing-information)
      - [Ambiguity](#ambiguity)
      - [Heterogeneity](#heterogeneity)
      - [Differences in Perspectives](#differences-in-perspectives)
      - [Internal Politics](#internal-politics)
    - [Organizing Information Environments](#organizing-information-environments)
    - [Organization Schemes](#organization-schemes)
      - [Exact Organization Schemes](#exact-organization-schemes)
        - [Alphabetical schemes](#alphabetical-schemes)
        - [Chronological schemes](#chronological-schemes)
        - [Geographical schemes](#geographical-schemes)
      - [Ambiguous Organization Schemes](#ambiguous-organization-schemes)
        - [Topical organization schemes](#topical-organization-schemes)
        - [Task-oriented schemes](#task-oriented-schemes)
        - [Audience-specific schemes](#audience-specific-schemes)
        - [Metaphor-driven schemes](#metaphor-driven-schemes)
        - [Hybrid schemes](#hybrid-schemes)
    - [Organization Structures](#organization-structures)
      - [The Hierarchy: A Top-Down Approach](#the-hierarchy-a-top-down-approach)
        - [Designing hierarchies](#designing-hierarchies)
      - [The Database Model: A Bottom-Up Approach](#the-database-model-a-bottom-up-approach)
      - [Hypertext](#hypertext)
    - [Social Classification](#social-classification)
    - [Recap](#recap-4)
  - [7.Labeling Systems](#7labeling-systems)
    - [Varieties of Labels](#varieties-of-labels)
      - [Labels as Contextual Links](#labels-as-contextual-links)
    - [Labels as Headings](#labels-as-headings)
      - [Labels Within Navigation Systems](#labels-within-navigation-systems)

# I.Introducing Information Architecture
`Information architecture` (IA) is a design discipline that is focused on making information findable and understandable.

## 1.The Problems That Information Architecture Addresses
### Recap
- Historically, information has shown a tendency to dematerialize, going from having a one-to-one relationship with its containers to being completely detached from its containers (as is the case with our digital information).
- This has had two important effects in our time: information is more abundant than ever before, and we have more ways of interacting with it than ever before.
- Information architecture is focused on making information findable and understandable. Because of this, it is uniquely well suited to address these issues.
- It does this by asking the designer to think about problems through two important perspectives: that our products and services are perceived as places made of information, and that they function as ecosystems that can be designed for maximum effectiveness.
- That said, information architecture doesn’t operate solely at the level of abstractions: for it to be effective, it needs to be defined at various levels.

## 2.Defining Information Architecture
### Definitions
Let’s start by clarifying what we mean by information architecture:

1. The structural design of shared information environments
2. The synthesis of organization, labeling, search, and navigation systems within digital, physical, and cross-channel ecosystems
3. The art and science of shaping information products and experiences to support usability, findability, and understanding
4. An emerging discipline and community of practice focused on bringing principles of design and architecture to the digital landscape

### Toward a Damned Good Information Architecture
![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0206.png)

Figure 2-6. The infamous three circles of information architecture

## 3.Design for Finding
### The “Too-Simple” Information Model
![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0301.png)

Figure 3-1. The “too-simple” model of information needs

Or, expressed as a simple algorithm:		

1. User asks a question.			
2. Something happens (i.e., searching or browsing).			
3. User receives the answer.			
4. Fin.

### Information Needs
When you’re hoping to make the perfect catch, you usually know what you’re looking for, what to call it, and where you’ll find it—this is called `known-item` seeking. An example is when you search the staff directory to find a colleague’s phone number.

When you’re hoping to find a few useful items in your traps, you’re doing something called `exploratory seeking`. In this case, you’re not exactly sure what you’re looking for. In fact, whether you realize it or not, you’re looking to learn something from the process of searching and browsing. For example, a user may go to his employer’s human resources site to learn something about retirement plans that the company offers.

When you want everything, you’re performing `exhaustive research`. You’re looking for everything available on a particular topic, hoping to leave no stone unturned. In this case, the user often has many ways to express what she’s looking for, and may have the patience to construct her search using all those varied terms. For example, someone who is trying to learn more about a friend’s medical condition might execute multiple searches for “AIDS,” “HIV,” “acquired immuno-deficiency syndrome,” and so forth.

Finally, our failing memories and busy schedules continually force us to engage in `refinding pieces` of useful information that we’ve happened upon before. For example, while you’re at work, you might surf for a few minutes and stumble on a great but long explanation of Django Reinhardt’s guitar technique. Naturally, you won’t read it now and risk losing your job. You’ll refind it later instead, or use a “read later” service such as Instapaper to return to it at a more convenient time.

Figure 3-2 illustrates these four different types of information needs.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0302.png)

Figure 3-2. Four common information needs

### Information-Seeking Behaviors
`Searching`, `browsing`, and `asking` are all methods for finding, and these are the basic building blocks of information-seeking behavior.

There are two other major aspects to seeking behaviors: `integration` and `iteration`. We often integrate searching, browsing, and asking in the same finding session. Figure 3-3 shows how you might search your corporate intranet for guidelines on traveling abroad.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0303.png)

Figure 3-3. Integrated browsing, searching, and asking over many iterations

In this model (shown in Figure 3-4), users start with an information need, formulate an information request (a query), and then move iteratively through an information system along potentially complex paths, picking bits of information (“berries”) along the way. In the process, they modify their information requests as they learn more about what they need and what information is available from the system.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0304.png)

Figure 3-4. The `“berry-picking”` model of how users move through an information system

Another useful model is the `“pearl-growing”` approach. Users start with one or a few good documents that are exactly what they need. They want to get “more like this one.” 

Corporate websites and intranets often utilize a `“two-step”` model. Confronted with a site consisting of links to perhaps hundreds of departmental subsites, users first need to know where to look for the information they need. They might search or browse through a directory until they find a good candidate or two, and then perform the second step: looking for information within those subsites.

### Recap

- IA starts with people and the reason they use your product or service: they have an information need.
- There are different models of what happens when people look for information.
- The most simple of these is problematic, because it doesn’t accurately represent what actually happens when people have an information need.
- Information needs are like fishing: sometimes people know exactly what they’re looking for, but often they’re casting a wider net.
- People act on these information needs through various information-seeking behaviors.
- There are various research methods that allow us to learn about these behaviors.

## 4.Design for Understanding
### A Sense of Place
When we talk about digital media, we use metaphors that betray a sense of place: we “go” online, “visit” a website, “browse” Amazon.com. Increasingly, these environments are also taking over many of the functions we’ve traditionally associated with physical places: we meet with our friends in WhatsApp, pay our bills in our bank’s website, learn in Khan Academy. As with physical places, we experience them as contexts that differ from one another, supporting different needs.

### Places Made of Information
![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0402.png)

Figure 4-2. Banks and hospitals serve different information needs; their website navigation structures highlight the differences between them, and you understand the information they present in the context of the roles and functions these organizations serve in society

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0403.png)

Figure 4-3. The content-centric “How to Cook Everything” iPad app feels more like a recipe book than like a place

Building architecture aims to produce physical environments that can serve and communicate their `social functions` effectively, and information architecture aims to do the same for information environments. The main difference is that instead of defining compositions of forms, spaces, and objects such as walls, roofs, and furniture, information architecture defines compositions of semantic elements such as navigation labels, section headings, and keywords, and produces the design principles, goals, and guidelines that capture the intended feeling of the place (e.g., is this a serious, solitary place, or a fun, social space?).

### Recap

- The structure of information environments influences more than how we find stuff: it also changes how we understand it.
- We experience information environments as places where we go to transact, learn, and connect with other people, among many other activities.
- When designing information environments, we can learn from the design of physical environments.
- Some organizing principles that carry over to information environments from physical environments include `structure` and `order`, `rhythm`, `typologies`, and `modularity` and `extensibility`.

# II.Basic Principles of Information Architecture
## 5.The Anatomy of an Information Architecture
### Visualizing Information Architecture

- `Organization systems` present the site’s information to us in a variety of ways, such as content categories that pertain to the entire campus (e.g., the top bar and its “Academics” and “Admission” choices), or to specific audiences (the block on the middle left, with such choices as “Future Students” and “Staff”).
- `Navigation systems` help users move through the content, such as with the custom organization of the individual drop-down menus in the main navigation bar.
- `Search systems` allow users to search the content; when the user starts typing in the site’s search bar, a list of suggestions is shown with possible matches for the user’s search term.
- `Labeling systems` describe categories, options, and links in language that (hopefully) is meaningful to users; you’ll see examples throughout the page (e.g., “Admission,” “Alumni,” “Events”).

### Top-Down Information Architecture
We refer to this as `top-down information` architecture (Figure 5-3), and the Gustavus main page addresses many common “top-down” questions that users have when they land on a site, including:

- Where am I? (1)
- I know what I’m looking for; how do I search for it? (2)
- How do I get around this site? (3)
- What’s important and unique about this organization? (4)
- What’s available on this site? (5)
- What’s happening there? (6)
- How do I engage with them via various other popular digital channels? (7)
- How can I contact a human? (8)
- What’s their address? (9)
- How can I access my account? (10)

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0503.png)

Figure 5-3. The Gustavus site’s main page is crammed with answers to users’ questions

### Bottom-Up Information Architecture
This is `bottom-up information architecture`; content structure, sequencing, and tagging help you answer such questions as:

- Where am I?
- What’s here?
- Where can I go from here?

Figure 5-5 shows a slightly different example of a bottom-up information architecture: images stored in one of this book’s authors’ iCloud account, as displayed in the iOS Photos app.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0505.png)

Figure 5-5. Image collections in the iOS Photos app

It provides context for the content, and tells us what we can do while we’re here:

- The information architecture tells us where we are (in the Photos app, looking at “Collections,” which are defined as ranges of dates in a particular geographic region).
- It helps us move to other closely related views (e.g., by switching to “Albums,” collections of photos we’ve defined).
- It helps us move through the information hierarchically (e.g., we can choose to view collections of images grouped by the year they were saved, instead of by more granular ranges of dates and locations) and contextually (e.g., by clicking on the city in which they were shot, we can see them arranged spatially over a map).
- It allows us to search the content based on various criteria, such as different time periods and locations.
- It allows us to share the content with others.

### Invisible Information Architecture
![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0506.png)

Figure 5-6. BBC search results include three “Editor’s Choice” links

What’s different is that the “Editor’s Choice” results are manually created: some people at the BBC decided that “ukraine” is an important term and that some of the BBC’s best content is not news stories, which normally come up at the top of most retrieval sets. So they applied some editorial expertise to identify three highly relevant pages and associated them with the term “ukraine,” thereby ensuring that these three items are displayed when someone searches for “ukraine.” Users might assume these search results are automatically generated, but humans are manually modifying the information architecture in the background; this is another example of `invisible information architecture`.

### Information Architecture Components

- `Organization systems`:How we categorize information (e.g., by subject or chronology); see Chapter 6
- `Labeling systems`:How we represent information—for example, using scientific terminology (“Acer”) or lay terminology (“maple”); see Chapter 7
- `Navigation systems`:How we browse or move through information (e.g., clicking through a hierarchy); see Chapter 8
- `Searching systems`:How we search information (e.g., executing a search query against an index); see Chapter 9

#### Browsing Aids

- `Organization systems`:Also known as taxonomies and hierarchies, these are the main way of categorizing or grouping content (e.g., by topic, by task, by audiences, or by chronology); user-generated tags are also a form of organization system
- `General navigation systems`:Primary navigation systems that help users understand where they are and where they can go within an information environment
- `Local navigation systems`:Primary navigation systems that help users understand where they are and where they can go within a portion of an information environment (e.g., a subsite)
- `Sitemaps/tables of contents`:Navigation systems that supplement primary navigation systems; provide a condensed overview of and links to major content areas within the environment, usually in outline form
- `Indices`:Supplementary navigation systems that provide an alphabetized list of links to the contents of the environment
- `Guides`:Supplementary navigation systems that provide specialized information on specific topics, as well as links to related subsets of content
- `Walkthroughs and wizards`:Supplementary navigation systems that lead users through sequential sets of steps; may also link to related subsets of content
- `Contextual navigation systems`:Consistently presented links to related content; often embedded in text and generally used to connect highly specialized content within an information environment

#### Search Aids

- `Search interface`:The means of entering and revising a search query, typically with information on how to improve your query, as well as other ways to configure your search (e.g., selecting from specific search zones)
- `Query language`:The grammar of a search query; query languages might include Boolean operators (e.g., AND, OR, NOT), proximity operators (e.g., ADJACENT, NEAR), or ways of specifying which field to search (e.g., AUTHOR=“Shakespeare”)
- `Query builders`:Ways of enhancing a query’s performance; common examples include spell checkers, stemming, concept searching, and drawing in synonyms from a thesaurus
- `Retrieval algorithms`:The part of a search engine that determines which content matches a user’s query; Google’s PageRank is perhaps the best-known example
- `Search zones`:Subsets of site content that have been separately indexed to support narrower searching (e.g., searching the tech support area within a software vendor’s site)
- `Search results`:Presentation of content that matches the user’s search query; involves decisions about what types of content should make up each individual result, how many results to display, and how sets of results should be ranked, sorted, and clustered

#### Content and Tasks

- `Headings`:Labels for the content that follows them
- `Embedded links`:Links within text; these label (i.e., represent) the content they link to
- `Embedded metadata`:Information that can be used as metadata but must first be extracted (e.g., in a recipe, if an ingredient is mentioned, this information can be indexed to support searching by ingredient)
- `Chunks`:Logical units of content; these can vary in granularity (e.g., sections and chapters are both chunks) and can be nested (e.g., a section is part of a book)
- `Lists`:Groups of chunks or links to chunks; these are important because they’ve been grouped together (e.g., they share some trait in common) and have been presented in a particular order (e.g., chronologically)
- `Sequential aids`:Clues that suggest where the user is in a process or task, and how far he has to go before completing it (e.g., “step 3 of 8”)
- `Identifiers`:Clues that suggest where the user is in an information system (e.g., a logo specifying what site she is using, or a breadcrumb explaining where she is)

#### “Invisible” Components

- `Controlled vocabularies and thesauri`:Predetermined vocabularies of preferred terms that describe a specific domain (e.g., auto racing or orthopedic surgery); typically include variant terms (e.g., “brewski” is a variant term for “beer”). Thesauri are controlled vocabularies that generally include links to broader and narrower terms, related terms, and descriptions of preferred terms (aka “scope notes”). Search systems can enhance queries by extracting a query’s synonyms from a controlled vocabulary.
- `Retrieval algorithms`:Used to rank search results by relevance; retrieval algorithms reflect their programmers’ judgments on how to determine relevance.
- `Best bets`:Preferred search results that are manually coupled with a search query; editors and subject matter experts determine which queries should retrieve best bets and which documents merit best bet status.

### Recap

- You’ll probably need to explain information architecture to others, so it’s important that you help them visualize it.
- You can visualize information architecture from the top down, or from the bottom up.
- There are various ways of categorizing IA components, but here we’ll be looking at four categories: organization systems, labeling systems, navigation systems, and searching systems.

## 6.Organization Systems
### Challenges of Organizing Information
#### Ambiguity
Classification systems are made of language, and language is `ambiguous`: words are capable of being understood in more than one way.

#### Heterogeneity
`Heterogeneity` refers to an object or collection of objects composed of unrelated or unlike parts.

An old-fashioned library `card catalog` is relatively homogeneous. It organizes and provides access to books. It does not provide access to chapters in books or collections of books. It may not provide access to magazines or videos. This homogeneity allows for a structured classification system. Each book has a record in the catalog. Each record contains the same fields: author, title, and subject.

Most digital information environments, on the other hand, are highly heterogeneous in many respects. For example, websites often provide access to documents and their components at varying levels of `granularity`. A site might present articles and journals and journal databases side by side. Links might lead to pages, sections of pages, or other websites. And websites typically provide access to documents in multiple formats.

**The heterogeneous nature of information environments makes it difficult to impose any single structured organization system on the content**.

#### Differences in Perspectives
The fact is that labeling and organization systems are intensely affected by their creators’ perspectives. We see this at the corporate level with websites organized according to internal divisions or org charts, with groupings such as marketing, sales, customer support, human resources, and information systems. How does a customer visiting this website know where to go for technical information about a product she just purchased? To design usable organization systems, **we need to escape from our own mental models of content labeling and organization.**

#### Internal Politics
As a designer, you must be sensitive to your organization’s political environment. In certain cases, you must remind your colleagues to focus on creating an architecture that works for the users. In others, you may need to make compromises to avoid serious political conflict. Politics raise the complexity and difficulty of creating usable information architectures.

### Organizing Information Environments
Organization systems are composed of `organization schemes` and `organization structures`. 

- An organization scheme defines the shared characteristics of content items and influences the logical grouping of those items. 
- An organization structure defines the types of relationships between content items and groups. Both organization schemes and structures have an important impact on the ways information is found and understood.

Organization is closely related to `navigation`, `labeling`, and `indexing`. 

- The organization structures of information environments often play the part of the primary navigation system. 
- The labels of categories play a significant role in defining the contents of those categories. 
- Manual indexing or metadata tagging is ultimately a tool for organizing content items into groups at a very detailed level.

### Organization Schemes
#### Exact Organization Schemes
For example, country names are usually listed in alphabetical order. If you know the name of the country you are looking for, navigating the scheme is easy. “Chile” is in the Cs, which are after the Bs but before the Ds. This is called `known-item searching`.

##### Alphabetical schemes
Most address book applications organize contacts alphabetically by last name, as shown in Figure 6-2.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0602.png)

Figure 6-2. The OS X Contacts application (image: https://www.apple.com/osx/apps/#contacts)

##### Chronological schemes
Press release archives are obvious candidates for chronological organization schemes (see Figure 6-3). The date of announcement provides important context for the release. However, keep in mind that users may also want to browse the releases by title, product category, or geography, or to search by keyword. A complementary combination of organization schemes is often necessary.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0603.png)

Figure 6-3. Press releases in reverse chronological order

##### Geographical schemes
Figure 6-4 shows an example of a geographical organization scheme from Craigslist. The user can select her nearest local directory. If her browser supports geolocation, the site navigates directly to it.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0604.png)

Figure 6-4. A geographical organization scheme with geolocation

#### Ambiguous Organization Schemes
There’s a simple reason why people find ambiguous organization schemes so useful: **we don’t always know what we’re looking for**. As we mentioned in Chapter 3, information seeking is often `iterative` and `interactive`.

##### Topical organization schemes
While few information environments are organized solely by topic, most should provide some sort of topical access to content. In designing a topical organization scheme, **it is important to define the breadth of coverage**. 

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0605.png)

Figure 6-5. A topical taxonomy showing categories and subcategories

##### Task-oriented schemes
Task-oriented schemes organize content and applications into collections of processes, functions, or tasks.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0606.png)

Figure 6-6. Like many apps, Microsoft Word on iOS features a task-oriented organization scheme

Task-oriented schemes are usually embedded within specific subsites or integrated into hybrid task/topic navigation systems, as we see in Figure 6-7.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0607.png)

Figure 6-7. Task, topic, and audience coexist on the Smithsonian home page

##### Audience-specific schemes
Audience-oriented schemes break a site into smaller, audience-specific mini-sites, thereby allowing for clutter-free pages that present only the options of interest to that particular audience. CERN, shown in Figure 6-8, presents an audience-oriented organization scheme that invites users to self-identify.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0608.png)

Figure 6-8. CERN invites users to self-identify

##### Metaphor-driven schemes
You need not look further than your desktop computer with its folders, files, and trash can or recycle bin for an example. 

##### Hybrid schemes
![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0610.png)

Figure 6-10. A hybrid organization scheme

In cases where multiple schemes must be presented on one page, you should communicate to designers the importance of preserving the integrity of each scheme. As long as the schemes are presented separately on the page, they will retain the powerful ability to suggest a mental model for users. For example, a look at the main menu in the Stanford University website in Figure 6-11 reveals a topical scheme, an audience-oriented scheme, and a search function. By presenting them separately, Stanford provides flexibility without causing confusion.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0611.png)

Figure 6-11. Stanford provides multiple organization schemes

### Organization Structures
#### The Hierarchy: A Top-Down Approach
##### Designing hierarchies
1. You should be aware of, but not bound by, the idea that hierarchical categories should be mutually exclusive.Within a single organization scheme, you will need to balance the tension between exclusivity and inclusivity. Hierarchies that allow cross-listing are known as `polyhierarchical`. Ambiguous organization schemes in particular make it challenging to divide content into mutually exclusive categories. 
1. It is important to consider the balance between breadth and depth in your hierarchy. `Breadth` refers to the number of options at each level of the hierarchy. `Depth` refers to the number of levels in the hierarchy.

#### The Database Model: A Bottom-Up Approach
They consisted of rolls of physical cards, with each card representing an individual contact: a `record` in the system. Each record contains several `fields`, such as name, address, and telephone number. Each field may contain data specific to that contact. The collection of records is a `database`.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0615.png)

Figure 6-15. The printed card Rolodex is a simple database

Most of the heavy-duty databases we use are built upon the `relational database model`. In relational database structures, data is stored within a set of relations or `tables`. `Rows` in the tables represent `records`, and `columns` represent `fields`.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0616.png)

Figure 6-16. A relational database schema (image: http://bit.ly/relational_model).

So why are database structures important to information architects? In a word, `metadata`.

For example, the `entity relationship diagram` (`ERD`) in Figure 6-17 illustrates a structured approach to defining a `metadata schema`. Each `entity` (e.g., Resource) has `attributes` (e.g., Name, URL). These entities and attributes become records and fields.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0617.png)

Figure 6-17. An entity relationship diagram showing a structured approach to defining a metadata schema (courtesy of Peter Wyngaard of Interconnect of Ann Arbor)

#### Hypertext
A `hypertext` system involves two primary types of components: the items or `chunks` of information that will be linked, and the `links` between those chunks.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0618.png)

Figure 6-18. A network of hypertextual connections

### Social Classification
`Free tagging`, also known as collaborative categorization, mob indexing, and ethnoclassification, is a simple yet powerful tool.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0619.png)

Figure 6-19. The “Discover” and “Trending” features in Twitter, which allow you to discover new and potentially interesting content, are driven by user-generated tags

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0620.png)

Figure 6-20. LinkedIn allows you to “endorse” your contacts as having certain professional skills, from a set of predefined tags

### Recap

- Our understanding of the world is informed by how we classify things.
- Classifying things is not easy; we have to deal with ambiguity, heterogeneity, differences in perspective, and internal politics, among other challenges.
- We can organize things using exact organization schemes or ambiguous organization schemes.
- Exact organization schemes include alphabetical, chronological, and geographical groupings.
- Ambiguous organization schemes include topical, task-based, audience-based, metaphorical, and hybrid groupings.
- The structure of organization schemes also plays an important role in the design of information environments.
- Social classification has emerged as an important tool for organizing information in shared digital environments.

## 7.Labeling Systems
### Varieties of Labels

- `Contextual links`:Hyperlinks to chunks of information on other pages or to other locations on the same page
- `Headings`:Labels that simply describe the content that follows them, just as print headings do
- `Navigation system choices`:Labels representing the options in navigation systems
- `Index terms`:Keywords, tags, and subject headings that represent content for searching or browsing

#### Labels as Contextual Links
Labels describe the hypertext links within the body of a document or chunk of information, and naturally occur within the descriptive context of their surrounding text. 

Because GOV.UK (Figure 7-4) is a site dedicated to providing information to the entire population of the UK, contextual links need to be straightforward and meaningful. GOV.UK’s contextual link labels, such as “Benefits,” “Money and tax,” and “Disabled people,” are representational, and draw on surrounding text and headings to make it clear what type of help you’ll receive if you click through. These highly representational labels are made even clearer by their context: **explanatory text, clear headings, and a site that itself has a few straightforward uses**.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0704.png)

Figure 7-4. The contextual links on the GOV.UK home page are straightforward and meaningful

On the other hand, contextual links on a blog aren’t necessarily so clear. The author is among friends and can assume that her regular readers possess a certain level of background (or, really, contextual) knowledge.

In Figure 7-5, the author expects us to know who “Dr. Drang” is—perhaps s/he’s been mentioned in this blog before. Or the author knows that we’ll recognize the label “Dr. Drang” as a person, and provides some mysterious context—“Your favorite snowman and mine”—to entice the user to click through. 

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0705.png)

Figure 7-5. These contextual links aren’t very representational, but that’s acceptable when there is a high degree of trust in the author

### Labels as Headings
`Headings`, as shown in Figure 7-6, are often used to establish a hierarchy within content.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0706.png)

Figure 7-6. Layout, typographic treatment, and whitespace help the reader distinguish labels and hierarchy in the Windows Store

To successfully navigate a process, it’s typically necessary for users to complete each step along the way, so heading labels have to be obvious and must also convey sequence. Figure 7-8 shows a page in the process to sign up to become a Google Play Developer, which clearly describes the actions required in each step.

![](https://learning.oreilly.com/library/view/information-architecture-4th/9781491913529/assets/inar_0708.png)

Figure 7-8. Clear sequential labeling in the Google Play Developer signup process

#### Labels Within Navigation Systems
















































