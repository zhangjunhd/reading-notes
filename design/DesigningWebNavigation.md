![cover](https://img9.doubanio.com/view/subject/s/public/s7715845.jpg)

    作者: James Kalbach
    出版社: O'Reilly Media
    副标题: Web Navigation
    出版年: 2007-8-15
    页数: 416
    定价: USD 49.99
    装帧: Paperback
    ISBN: 9780596528102

- [豆瓣链接](https://book.douban.com/subject/2146224/)
- [safari链接](https://learning.oreilly.com/library/view/designing-web-navigation/9780596528102/)

---

- [I.Foundations of Web Navigation](#ifoundations-of-web-navigation)
  - [1.Introducing Web Navigation](#1introducing-web-navigation)
    - [Considering Navigation](#considering-navigation)
    - [Defining Web Navigation](#defining-web-navigation)
    - [Navigation Provides Access To Information](#navigation-provides-access-to-information)
      - [The content-linking-only model](#the-content-linking-only-model)
      - [The “liquid information” model](#the-liquid-information-model)
      - [The filter model](#the-filter-model)
      - [The search model](#the-search-model)
      - [The structural-browse model](#the-structural-browse-model)
    - [Navigation Shows Location](#navigation-shows-location)
    - [Web Navigation Design](#web-navigation-design)
      - [Why are you building the site?](#why-are-you-building-the-site)
      - [Who will use the site?](#who-will-use-the-site)
      - [What does the navigation provide access to?](#what-does-the-navigation-provide-access-to)
      - [How is the site content organized?](#how-is-the-site-content-organized)
      - [How will users navigate to the content they need?](#how-will-users-navigate-to-the-content-they-need)
  - [2.Understanding Navigation](#2understanding-navigation)

# I.Foundations of Web Navigation
## 1.Introducing Web Navigation
### Considering Navigation
Figure 1-1 shows a news article from the international version of the BBC web site (www.bbc.co.uk). 

![](https://learning.oreilly.com/library/view/designing-web-navigation/9780596528102/httpatomoreillycomsourceoreillyimages27460.png)

Figure 1-1. An article from BBC news

Overall, the various elements come together to create `system` of navigation. Though visitors might perceive this system as whole, we can dissect its individual components. For instance, the tabs at the top center of the page (starting with Home) are referred to as the `main navigation`. This page is in the News section. Within News, the `local navigation` is represented by a vertical menu on the left, which indicates where you are (Science/Nature is highlighted) and where else you can go, such as to articles about Africa or the business news section.

### Defining Web Navigation
Web navigation is defined three ways:

1. The theory and practice of how people move from page to page on the Web.
2. The process of goal-directed seeking and locating hyperlinked information; browsing the Web.
3. All of the links, labels, and other elements that provide access to pages and help people orient themselves while interacting with a given web site.

### Navigation Provides Access To Information
#### The content-linking-only model
Imagine a collection of pages linked to one another with no particular hierarchical organization or pattern of linking. All the links are embedded in the text. They aren’t isolated in a way that serves as a navigational scheme, and there’s no concept of a traditional home page. The site is just a big web of related information. Conceptually, it might look like Figure 1-2.

![](https://learning.oreilly.com/library/view/designing-web-navigation/9780596528102/httpatomoreillycomsourceoreillyimages27462.png)

Figure 1-2. The content-linking-only model

You might argue this would provide strong relationships between documents. A linked term or phrase on one page has a close association with the content on the destination page. But overall findability is low with this model. People wouldn’t have a sense of beginning or end in their search for information, and orientation would be difficult. Also, access time would be much longer. You’d have to scan the text in its entirety to get a sense of all related content. This is certainly not the most efficient way to access information.

#### The “liquid information” model
This is similar to the content-linking model, but there are no links. Instead, each and every word is interactive for all texts. There is no distinction between text and hypertext, or between content and navigation. All texts are links, and all links are texts. Figure 1-3 depicts this model. From a single word on a given page, any number of navigation actions is possible, leading to new content pages.

![](https://learning.oreilly.com/library/view/designing-web-navigation/9780596528102/httpatomoreillycomsourceoreillyimages27464.png)

Figure 1-3. The “liquid information” model

#### The filter model
Imagine accessing all the content of a web site through a single page. This page contains controls for filtering and sorting to present different chunks of material at a time. It would be highly interactive, for sure. A list of documents in the collection shrinks and expands with each interaction. Clicking on an individual item in the list would reveal its full text and images. Figure 1-5 shows this concept. A single control on a given page leads to new content, but that content is presented within the same page. The motion is therefore circular: you never leave the page, just continuously update its content.

![](https://learning.oreilly.com/library/view/designing-web-navigation/9780596528102/httpatomoreillycomsourceoreillyimages27468.png)

Figure 1-5. The filter model

First-time visitors would not get a good overview of the type of content available on the site. It might also be difficult for users to know when a search is completed: you could potentially filter and sort all day and still arrive at new lists of content. Bookmarking and general accessibility are also complicated.

#### The search model
In this model of access, there is no navigation or linking to internal documents. Instead, visitors to the site can only perform keyword searches for information. Users type a keyword or two into a box and click the Search button. This produces a list of pages they can access. On the individual content pages, the only option is to return to the list or conduct a new search. Figure 1-7 shows these three steps from left to right.

![](https://learning.oreilly.com/library/view/designing-web-navigation/9780596528102/httpatomoreillycomsourceoreillyimages27472.png)

Figure 1-7. The search model

Search is certainly an efficient way to get to content. We search on the Web all the time. But keyword searching is effective only if the item being sought is known in advance. It assumes that people will be able to accurately and completely express their information needs as a query. However, this may not always be the case.

#### The structural-browse model
In this model, there is only a set of links, perhaps on the side of each page, that provide access to information on a web site. This area is visually separated from the page content in the layout. You can click through a hierarchy of navigation options, refreshing the page content each time, as shown graphically in Figure 1-8. To get to a page in another area of the site, you’d have to navigate back up the tree and back down another branch. There are no embedded links within the text and no search function. Compare this with the content-only linking model, in which associations can be made in any direction from any page.

![](https://learning.oreilly.com/library/view/designing-web-navigation/9780596528102/httpatomoreillycomsourceoreillyimages27474.png)

Figure 1-8. The structural browse model

In reality, web navigation might look more like something depicted in Figure 1-9, where various types of access are blended together. Navigation design is about creating a `system` of access to information. It is this system that gives rise to the web navigation experience.

![](https://learning.oreilly.com/library/view/designing-web-navigation/9780596528102/httpatomoreillycomsourceoreillyimages27476.png)

Figure 1-9. Web navigation: multiple forms of access to information

### Navigation Shows Location
While navigating a site, users generally need to know:

- Where am I?
- What’s here?
- Where can I go from here?

Location is often indicated by highlighting the currently selected option in a navigation menu or displaying the path with a `breadcrumb trail`. 

Beyond orientation, knowing your location in a site has other implications:

- Comprehension of a given page may improve—or even require—understanding its relationship to other pages.
- Pages that are deeper in a site structure may be seen as more precise. Knowing how deep you are in a site can give cues as to granularity and detail of information encountered. The natural expectation is that pages higher in a site are more general in nature, and the detail comes out as you move further down the structure.
- Knowing where you are in a site gives cues into exhaustiveness in seeking information. Location can signify if you should keep looking or not. The site navigation, then, potentially provides a sense of closure while looking for information.

For instance, Figure 1-10 shows the page for financial support for students in Europe on the Open University web site (www.open.ac.uk). To get to this page, you have to make several clicks: Becoming a student > Financial Support > Students Resident in Continental Europe. The relatively deep location of this page indicates that there isn’t more on this subject on the site, and to find more information you’d have to call the phone number or write to the email address provided. Additionally, by itself, Students Resident in Continental Europe could refer to many things. Knowing that this is within the category Financial Support gives it a clear meaning.

![](https://learning.oreilly.com/library/view/designing-web-navigation/9780596528102/httpatomoreillycomsourceoreillyimages27478.png)

Figure 1-10. Location information in the navigation of the Open University web site

### Web Navigation Design
When considering a navigation design, ask yourself these fundamental questions:

#### Why are you building the site?
The first step in navigation design is understanding the purpose and motivation for the web site as a whole, as well as in the broader business context.

#### Who will use the site?
User research is the process of systematically investigating the visitors to a given site. It not only gives insight into the types of people visiting your site, but also into their needs and behaviors.

#### What does the navigation provide access to?
People come to a site to find answers or to perform a task. You must be providing the right content for the site to have value.

#### How is the site content organized?
Information architecture represents the underlying structures that give shape and meaning to the content and functionality on your site. It also has a major and direct impact on the navigation. As the designer, you must understand the content and how it is organized.

#### How will users navigate to the content they need?
Page layout and graphic design give the navigation its final form. This is more than just cosmetic window dressing, however. Aspects such as the order of options, their arrangement on the page, the font type and size used, and color, can be critical elements. They can make or break the navigation system.

## 2.Understanding Navigation





















