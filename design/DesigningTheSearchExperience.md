![cover](https://img9.doubanio.com/view/subject/s/public/s24920254.jpg)

    作者: Tony Russell-Rose / Tyler Tate
    出版社: Morgan Kaufmann
    副标题: The Information Architecture of Discovery
    出版年: 2013-1-2
    页数: 320
    定价: USD 39.95
    装帧: Paperback
    ISBN: 9780123969811

- [豆瓣](https://book.douban.com/subject/11638263/)
- [oreilly](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/)

---

- [1.A Framework for Search and Discovery](#1a-framework-for-search-and-discovery)
  - [1.The User](#1the-user)
    - [Novices and Experts](#novices-and-experts)
      - [Domain expertise versus technical expertise](#domain-expertise-versus-technical-expertise)
      - [Double novices orienteer](#double-novices-orienteer)
      - [Double experts teleport](#double-experts-teleport)
      - [The in-betweeners](#the-in-betweeners)
      - [Serial and holistic thinkers](#serial-and-holistic-thinkers)
      - [The rod-and-frame test](#the-rod-and-frame-test)
      - [Serialists: brick-by-brick craftsmen](#serialists-brick-by-brick-craftsmen)
      - [Holists: big-picture visionaries](#holists-big-picture-visionaries)
      - [The performance gap](#the-performance-gap)
      - [Designing for learnability](#designing-for-learnability)
    - [Verbal and Visual Learners](#verbal-and-visual-learners)

# 1.A Framework for Search and Discovery
The most fundamental step is to recognize that the opinions are themselves based on a set of **assumptions**—in particular, assumptions about **who** is doing the searching, **what** they are trying to achieve and under **what circumstances**, and **how** they are going about it. Each of these assumptions corresponds to a separate `dimension` by which we can define the search experience.

**The Dimensions of Search User Experience**

The first of these dimensions is the `type of user`, in particular his or her level of **knowledge and expertise**.
For example, consider the users of an online retail store: are they knowledgeable enthusiasts or novice shoppers? Likewise, for an electronic component supplier: are the users expert engineers or purchasing agents with limited domain knowledge?

Once we understand the user, we can move on to the second dimension: his or her `goal`. This goal can vary from simple fact checking to more complex explorations and analyses. For example, are users searching for a specific item such as the latest Harry Potter book? Or are they looking to choose from a broader range of possibilities, such as finding shoes to match a business suit? Or are they unsure of what they are looking for in the first place, knowing only that they would like to find a suitable gift?

Knowing the users and their goals, we can now consider the third dimension: the `context`. Context includes a range of influences, from the physical to the intangible. For example, is the user at the workplace, where the task and the organizational setting dominate? Or is the user at home, where `social context` might become more important? Perhaps he or she is using a mobile device while travelling, during which `physical context` shapes the search experience.

Finally, based on our understanding of the users, their task and the wider context, we can consider the fourth dimension: their `search mode`. Search isn’t just about finding things—on the contrary, most finding tasks are but a small part of a much larger overall task. Consequently, our focus must be on understanding the complete task life cycle and helping users complete their overall information goals. This includes activities such as comparing, exploring, evaluating, analyzing, and much more.

## 1.The User
### Novices and Experts
Expertise plays a significant role in how people seek information. Understanding the differences between novices and experts will enable us to design better search experiences for everyone. But first, it’s worth distinguishing between two dimensions of expertise.

#### Domain expertise versus technical expertise
`Domain expertise` defines one’s familiarity with a given subject matter; a professional photographer, for instance, has substantial domain expertise in the field of photography. `Technical expertise`, on the other hand, indicates one’s proficiency at using computers, the Internet, search engines, and the like.

In combination, the domain and technical dimensions of expertise describe four types of users (Figure 1.1):

- Double experts
- Domain expert/technical novices
- Domain novice/technical experts
- Double novices

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-01-9780123969811.jpg)

Figure 1.1 Two dimensions of expertise: domain and technical.

#### Double novices orienteer
Double novices share three main characteristics (Hölscher and Strube, 2000):

1. **Frequent query reformulation**. Novices perform more queries than experts but look at fewer pages. Although they frequently reformulate their query, double novices often make only small, inconsequential changes to their search phrase.
2. **Going back**. When novices do click on a search result, they are much more likely than experts to then navigate back to the search page. With a fear of venturing too far from safety, double novices practice a hub-and-spoke pattern of information seeking with the search page firmly at the center.
3. **More time spent**. The many queries and frequent backward-oriented behavior of double novices causes them to spend more time on a given search task than would an expert.

Because novices frequently refine their original query but often don’t make radical enough changes, showing a list of related searches (as demonstrated by Foodily in Figure 1.2) can help users make more successful query reformulations. In addition, breadcrumbs accomplish the dual purpose of communicating the user’s current location, while also providing a path to go back (Figure 1.3).

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-02-9780123969811.jpg)

Figure 1.2 Foodily’s iPhone application places related searches at the bottom of the page, after the search results.

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-03-9780123969811.jpg)

Figure 1.3 The breadcrumbs on Zappos.com indicate which filters the user has applied and provide the means to remove them.

#### Double experts teleport
Double experts are characterized by three tendencies (Hölscher and Strube, 2000):

1. **More pages examined**. Double experts click on more search results than do novices.
2. **Going deeper**. Double novices tend to retreat from the pages they examine; double experts rarely go back. Instead, experts follow links from one page to the next, progressing deeper into the information space with each step.
3. **Less time spent**. Double experts are time-efficient in their search tasks. Not only do they reformulate their queries less often, but they can also determine the relevancy of a given page more rapidly than novices.

Expert-friendly search user interfaces should support advanced syntax and filtering to help users quickly narrow their search. Although the Boolean operators AND, OR, and NOT are certainly worth supporting, Wolfram Alpha (shown in Figure 1.4) goes a step further and allows users to input domain-specific terminology and retrieve computed answers. Similarly, a faceted search interface for filtering by format, selecting ranges, or excluding certain categories—such as Getty’s Moodstream, shown in Figure 1.5—can help users pinpoint content that’s relevant to their information needs.

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-04-9780123969811.jpg)

Figure 1.4 Wolfram Alpha is designed to return computed answers using advanced syntax and domain-specific terminology.

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-05-9780123969811.jpg)

Figure 1.5 Getty Image’s Moodstream lets users search for stock photos using slider controls.

#### The in-betweeners
Domain expert/technical novices, for instance, use their knowledge to enter effective queries and quickly evaluate pages, but they lack the technical confidence to explore unknown territory (Jenkins et al., 2003). Their traits include:

1. **Advanced terminology**. Domain experts are able to rely on their extensive vocabulary to construct more topical queries than are domain novices.
2. **Effective evaluation**. Similarly, high domain knowledge makes the process of evaluating a page more meaningful and timely.
3. **Going back**. A lack of technical expertise, however, contributes to a sense of disorientation, preventing users from venturing too far away from the search page.

Domain novice/technical experts, on the other hand, brim with confidence, but have trouble discerning relevant content (Hölscher and Strube, 2000). They are characterized by:

1. **Advanced formatting**. Technical experts are much more likely to use query formatting techniques—such as double quotes and Boolean operators—than are technical novices.
2. **Confident exploration**. Despite their lack of domain expertise, technical experts exude confidence and never worry about becoming disoriented.
3. **Difficulty with evaluation**. Technical expertise doesn’t compensate for a lack of domain knowledge when it comes to evaluating the relevance of a page.

#### Serial and holistic thinkers
Psychologists call these `cognitive styles`—the stable attitudes, preferences, and habits that determine how an individual processes and represents information. We’ll begin by looking at the `serial-holistic style` of information processing.

#### The rod-and-frame test
Here it is: draw a vertical line inside the rectangle.

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-06-9780123969811.jpg)

Figure 1.6 Complete a simplified version of the rod-and-frame test by drawing a vertical line in the rectangle.

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-07-9780123969811.jpg)

Figure 1.7 Serialists complete the rod-and-frame test by drawing the line aligned with the edges of the rectangle (left). Holists, on the other hand, draw the line along the global north–south axis (right).

#### Serialists: brick-by-brick craftsmen
Like skilled craftsmen, serialists are highly attuned to the details. When learning, serialists tend to drill down to narrow subtopics and follow a logical progression from one to the next. Despite being skilled at analyzing the component parts (Figure 1.8), serialists have greater difficulty combining the parts into a whole (Kim, 2001).

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-08-9780123969811.jpg)

Figure 1.8 Serialists concentrate on the individual parts rather than the whole.

#### Holists: big-picture visionaries
Holists are visionaries with a bird’s-eye view (Figure 1.9). Operating with an intrinsic motivation that is independent of their surroundings, holists flourish in flexible environments where they are free to pursue their own interests at the pace of their choice. When approaching a topic, they immediately set out to comprehend the big picture, giving holists a more balanced view and helping them put situations into context. However, holists are also prone to oversimplification, sometimes glossing over important details (Ford et al., 2002).

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-09-9780123969811.jpg)

Figure 1.9 Holists focus on the cohesive whole rather than on component parts.

#### The performance gap
Holists are more efficient at satisfying their information needs. Serialists, by comparison, find it more difficult to discern the relevance of information and consequently spend more time searching for the same answers.

Although there is a wide gap in performance between serialists and holists who are `technical novices`, the gap all but disappears between the two cognitive styles when `technical expertise` is high. In other words, user interfaces can become more effective by helping serialist novices—or all novices, for that matter—increase their level of technical expertise.

#### Designing for learnability
`Learnability`—the ease with which users gain awareness of available software functions and comprehend how to act on them—can be accomplished using `contextual instructions`, `immersive overlays`, and `subtle visual design`.

A simple contextual instruction, for example, can be achieved by adding descriptive placeholder text to the search box (Figure 1.10). The text can inform users about the type of query that the system expects—whether it’s the name of a restaurant, an area of a city, or a postal code.

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-10-9780123969811.jpg)

Figure 1.10 Toptable’s iPhone application combines the use of placeholder text and a three-option segmented control to clearly indicate the type of input that the application expects from the user.

`Contextual popovers`, like the ones used by Foodily in Figure 1.11, can augment a well-designed interface and reduce the guesswork required by the user. `Immersive, full-screen overlays` —such as the welcome screen to the TapTu iPad app shown in Figure 1.12—can serve a similar purpose. Caution is required in both situations, however; providing tips for new users must be balanced with concern for more experienced users (both Foodily and TapTu, for instance, show the “getting started” advice only on a user’s first visit).

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-11-9780123969811.jpg)

Figure 1.11 Foodily, a recipe search site, uses small popovers to introduce first-time users to a few of the features unique to Foodily’s website.

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-12-9780123969811.jpg)

Figure 1.12 TapTu, a news-reading application, uses an overlay to provide a tutorial for new users.

A more nuanced method for enhancing learnability is to use subtle animation and tactile textures to suggest gestures, hint at off-screen content, and indicate which elements on the screen are interactive. When a user first views a list of search results using Airbnb’s iPhone application (shown in Figure 1.13), for instance, an animation reveals a star behind each result before quickly disappearing, hinting that a swipe from left to right will “favorite” that particular item. Such tactics are especially useful on mobile devices where screen space is scarce.

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-13-9780123969811.jpg)

Figure 1.13 On the first use, Airbnb’s iPhone application reveals a star behind each search result before quickly sliding away, training users to use a left-to-right gesture to “favorite” a result.

### Verbal and Visual Learners
![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-14-9780123969811.jpg)

Figure 1.14 Two dimensions of cognitive style: serial–holistic and verbal–visual.
















