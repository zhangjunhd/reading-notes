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
      - [From five senses to three modalities](#from-five-senses-to-three-modalities)
      - [Dual coding theory](#dual-coding-theory)
      - [Designing with overviews and previews](#designing-with-overviews-and-previews)
  - [2.Information Seeking](#2information-seeking)
    - [Models of Information Seeking](#models-of-information-seeking)
      - [The classic model](#the-classic-model)
      - [The standard model](#the-standard-model)
      - [The cognitive model](#the-cognitive-model)
      - [The dynamic model](#the-dynamic-model)
      - [The information journey model](#the-information-journey-model)
    - [Information Foraging](#information-foraging)
      - [A biological foundation](#a-biological-foundation)
      - [Man the informavore](#man-the-informavore)
      - [Information foraging theory](#information-foraging-theory)
      - [Designing with information scent](#designing-with-information-scent)
        - [Descriptive titles](#descriptive-titles)
        - [Hit highlighting](#hit-highlighting)
        - [Clear labeling](#clear-labeling)
    - [Sensemaking](#sensemaking)

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

#### From five senses to three modalities
We experience the world through five senses, distilled by psychologists into three “sensory modalities” relevant to learning: verbal, visual, and kinesthetic (Denig, 2004). Though everyone learns through all three modes, we each favor one over the others, resulting in three different styles of learning:

1. `Verbal` learners absorb written and spoken information more readily than visual concepts. Because most learning is either text-based (reading a book, searching online) or auditory (a classroom lecture or personal conversation), verbal learners have ready access to content in their preferred medium.
2. `Visual` learners, on the other hand, digest information from charts, diagrams, timelines, maps, and other concrete images more easily than from the written or spoken word. Visual learners have less access to appropriate content than their verbal counterparts.
3. `Kinesthetic` learners enjoy hands-on activities involving movement, from dancing to woodwork. Although kinesthetic learning is minimally involved in desktop computing, it plays a much more significant role in gestural and touch-based interfaces.

#### Dual coding theory
In the 1970s, psychologist Allan Paivio made an important observation: people learn best when information is presented in two modalities at the same time, which is now known as the `Dual-Coding Theory`. 

#### Designing with overviews and previews
Although dual coding theory has significant implications for website content, it’s also important for the search experience. In particular, `visual overviews` and `previews` can augment text-based lists to both describe the result set as a whole, as well as the individual result itself (Greene et al., 2000).

Mapumental, for example, distills transit times, house prices, and “scenicness” ratings into a composite map overlay that helps its users choose where to live. Crunching these numbers oneself would be an enormous task, yet the map in Figure 1.15 instantly shows which areas of London are no farther than a 45-minute commute from Waterloo Station, have an average house price of less than £400,000, and score at least 2 out of 10 in scenicness.

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-15-9780123969811.jpg)

Figure 1.15 Mapumental visualizes a synthesis of transit times, house prices, and “scenicness” ratings to help users choose where to live.

Google Finance’s stock screener, for example (shown in Figure 1.16), efficiently combines dual sliders with a histogram to provide contextual feedback for users searching for companies by financial criteria.

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-16-9780123969811.jpg)

Figure 1.16 Histograms, such as these from Google Finance’s stock screener, instantly convey the distribution of results.

While `overviews` provide a visual depiction of the result set as a whole, `previews` help the user examine an individual result in greater detail—augmenting verbal information with a visual component to help the user make better relevance judgments. In some cases—such as ecommerce—visual thumbnails can even be more important than the text (Figure 1.17).

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-17-9780123969811.jpg)

Figure 1.17 For many ecommerce websites, such as NorthFace.com, visual thumbnails are more important than textual descriptions.

Larger previews, rather than help the user quickly skim the results, gives the user a chance to verify the relevance of a result before committing to viewing the full item. Apple’s Spotlight search, for example (shown in Figure 1.18), previews a document as the user hovers over its title, reducing the inconvenience of opening a new document only to discover that it’s irrelevant.

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F00001Xf01-18-9780123969811.jpg)

Figure 1.18 Apple’s Spotlight search shows document previews as the user interacts with the search results.

## 2.Information Seeking
Mankind is an endless pursuer of knowledge.

We bridge this knowledge gap by asking those around us for advice, turning to books and encyclopedias, and, increasingly, searching the Internet. This journey between need and fulfillment is called `information seeking`.

### Models of Information Seeking
#### The classic model
The classic model is one of the first models of information retrieval, widely used in information science research for over 30 years (Robertson, 1977).

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F000021f02-01-9780123969811.jpg)

Figure 2.1 The classic model of information retrieval.

#### The standard model
In contrast with the classic model, the standard model places greater emphasis on the user. It portrays information seeking as a type of problem solving (Marchionini, 1995) involving a cycle of four activities (Sutcliffe & Ennis, 1998):

1. Identifying the problem
2. Articulating the information need
3. Formulating the query
4. Evaluating the results

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F000021f02-02-9780123969811.jpg)

Figure 2.2 The standard model of the search process.

#### The cognitive model
Like the standard model, Don Norman’s cognitive model of task performance (shown in Figure 2.3) also views search as a form of problem solving driven by an explicit user goal (Norman, 1988). But in this case, users apply a mental model—an internal representation of the problem situation and its context—to develop a plan of action to achieve that goal. These actions lead to changes in the external world that are evaluated to determine whether the goal has been achieved.

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F000021f02-03-9780123969811.jpg)

Figure 2.3 Don Norman’s cognitive model of task performance.

A key insight of Norman’s model over the previous two is that it recognizes the importance of domain knowledge (as discussed in Chapter 1): the greater the users’ knowledge, the more likely they are to articulate effective queries and accurately determine the relevance of results.

#### The dynamic model
Both the standard and cognitive models share an underlying assumption that the user’s information need remains unchanged throughout a given session. They view the process of information seeking as one of iteratively refining a given query until the ideal set of results is found. However, numerous studies have found that users’ information needs evolve as they interact with information and that they formulate new goals as they acquire domain knowledge. Far from being static, search is an interactive, iterative process in which the answer can change the question. As Peter Morville puts it, “what we find changes what we seek” (Morville, 2009).

Consequently, we need a model that accounts for changes in users’ information needs as they learn and respond to the information they encounter. The dynamic model proposed by Marcia Bates (1989) accomplishes just that (Figure 2.4).

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F000021f02-04-9780123969811.jpg)

Figure 2.4 Marcia Bates’ dynamic model.

#### The information journey model
Ann Blandford and Simon Attfield (2010) have further explored the unfolding journey of information seeking. Like the dynamic model, their information journey model (shown in Figure 2.5) has been derived from empirical studies of user behavior. The main activities in their framework are:

1. Recognizing an information need
2. Acquiring information
3. Interpreting and validating the information
4. Using the information

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F000021f02-05-9780123969811.jpg)

Figure 2.5 The information journey model.

These information encounters are what we commonly label serendipity. The information journey model, with its multiple entry points, acknowledges `serendipity` as part of the information seeking experience.

### Information Foraging
`Information foraging`, an instinct closely related to that found in animals hunting for food, interacts with `sensemaking`, the cognitive process for deriving meaning from new information. Together, information foraging and sensemaking form a feedback loop (Pirolli & Card, 2005) that underpins the information seeking process.

#### A biological foundation
Biologists in the 1960s observed that animals often eat a particular type of food in one environment but ignore the same food in other places. Ecologists Robert MacArthur and Eric Pianka set out to discover how animals decide what to eat. Their research, and their accompanying `optimal foraging theory` (MacArthur & Pianka, 1966), provides a foundation for understanding our own behavior when searching for information.

According to optimal foraging theory, animals live in environments consisting of many “patches,” each with a unique blend of potential food sources.

This principle of diminishing returns is known in ecology as the `marginal value theorem` (Charnov, 1976). The theory asserts that animals perform a cost/benefit analysis on staying in the current patch versus traveling to a new one—considering both current and potential food supplies as well as the transit time between the two patches (Figure 2.6).

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F000021f02-06-9780123969811.jpg)

Figure 2.6 Charnov’s marginal value theorem states that a forager should leave a given patch when the rate of gain within that patch drops below the rate of gain that could be achieved by traveling to a new patch.

#### Man the informavore
George Miller portrayed our species as `informavores`: creatures hungry for information (Miller, 1983). But just like the bear must be selective in its diet (digging all day for a few measly ants would hardly be worthwhile), so must informavores carefully navigate the glut of information in our modern environment. Herbert Simon spoke of this perilous balance in 1971:

>What information consumes is rather obvious: it consumes the attention of its recipients. Hence a wealth of information creates a poverty of attention, and a need to allocate that attention efficiently among the over-abundance of information sources that might consume it. (p. 40)

Although information is what we seek, our limited supply of attention forces us to make a tradeoff between comprehensiveness and timeliness. Simon coined the term satisficing—a combination of the words “satisfy” and “suffice”—to describe this pragmatic decision-making strategy that pervades human behavior (Simon, 1956).

#### Information foraging theory
Peter Pirolli and Stuart Card, researchers at the Palo Alto Research Center (PARC), began applying the principles of optimal foraging theory to information seeking in the early 1990s, establishing a new framework called `information foraging theory` (Pirolli & Card, 1999). Pirolli and Card drew a connection between users moving from one website to the next and animals traveling from patch to patch. They observed that users, in an effort to satisfice, heavily rely on certain cues known as `information scent` to guide them toward their destination.

As users traverse the Web, they encounter information scent when `“trigger words”`—terms they perceive as meaningful to their task—are used in the text of a hyperlink, as words in a heading, or in a search result’s description. The more trigger words that are present, the stronger the information scent (Spool et al., 2004). When information scent grows stronger from page to page, users are confident that they’re headed in the right direction. But when it’s weak, they may be uncertain about what to do or even give up.

In addition to information scent, Pirolli and Card’s research also helps explain `information snacking` (Nielsen, 2003). According to the marginal value theorem, the amount of time a user spends on a given website is proportional to the travel time between sites. As between-patch time decreases—thanks to Google and fast Internet connections—users spend less time on any one site. The result is that information seeking has become less of a sit-down banquet and more of an opportunistic buffet.

#### Designing with information scent
##### Descriptive titles
Before clicking on a search result—or even reading its two-line description—the title must first be deemed relevant. Obvious though it is, the presentation of clear, descriptive titles is the surest method for providing strong information scent when displaying search results.

Jared Spool found that reasonably long titles tend to work better than shorter ones, with links of 7 to 12 words being most likely to lead to a successful outcome (Figure 2.7).

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F000021f02-07-9780123969811.jpg)

Figure 2.7 Jared Spool found that 7- to 12-word links yield the greatest likelihood of a user finding what he or she is looking for.

##### Hit highlighting
When the user performs a query, he or she inputs the most important terms to his or her search—that is, the query’s `trigger words`. Hit highlighting (Figure 2.8) is the technique of emphasizing the words included in the query wherever they appear on the search results page. Using a bold font weight helps to draw the user’s eye to the trigger words, increasing information scent.

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F000021f02-08-9780123969811.jpg)

Figure 2.8 Bing uses a bold font weight to highlight the user’s query terms whenever they appear in the search result list, for both exact phrase matches (e.g., “artificial intelligence”) and partial matches (e.g., “intelligence”).

##### Clear labeling
When searching through online content, for instance, the user might be looking for business news and wish to skip over sport and entertainment articles (Figure 2.9). Clearly identifying which category a given result belongs to can help users ignore unwanted documents and focus on their genre of choice (Drori, 2002).

![](https://learning.oreilly.com/library/view/designing-the-search/9780123969811/images/F000021f02-09-9780123969811.jpg)

Figure 2.9 The BBC labels each news story with a category, such as “Europe” or “Business.”

### Sensemaking

















































