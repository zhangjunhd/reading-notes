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

- [Chapter 1. Pattern Recognition](#chapter-1-pattern-recognition)
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
- [Chapter 2. The Anatomy of Search](#chapter-2-the-anatomy-of-search)
  - [Users](#users)

# Chapter 1. Pattern Recognition
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

# Chapter 2. The Anatomy of Search
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














