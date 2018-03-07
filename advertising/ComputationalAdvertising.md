# Computational Advertising: Techniques for Targeting Relevant Ads
## Introduction
### Introduction to Computational Advertising
The core problem addressed in Computational Advertising is to find the best matching ads for a given context.

![](http://ou8qjsj0m.bkt.clouddn.com//18-2-6/65396779.jpg)

Figure 1.1: A typical ad system for Sponsored Search and Contextual Advertising: Once the ads are retrieved, they are ranked based on the probability of a click given the query, ad and the user

First, the top-k ads are retrieved. Next, they are ranked based on the click-through rate of the ad and the bid amount for the ad.

#### Anatomy of a Textual Ad
A typical textual ad contains following fields Bendersky et al. [2010]:

- **Bid term/phrase**: The term bid by the advertiser for the ad. This is invisible to the user, and it is used to indicate what content the ad should be shown against. For each bid term bid by the advertiser, they have to pay the bid amount.
- **Bid amount**: The amount bid by the advertiser for the bid phrase. This too is invisible to the user.
- **Title**: This is the title of the ad.
- **Description/Creative**: The description is the text displayed below the title. It typically consists of a short description of the ad and is usually written to attract the user. It is also known as **creative**.
- **Display URL**: The URL displayed in the ad. To improve the presentation of ads and to reduce the space, the display URL is usually different from that of the original/landing page URL. The **landing page** for an ad is the page where a user lands after clicking on an ad as shown in Figure 1.3.

![](http://ou8qjsj0m.bkt.clouddn.com//18-2-6/2431497.jpg)

Figure 1.2: Structure of a typical textual Ad

![](http://ou8qjsj0m.bkt.clouddn.com//18-2-6/73983040.jpg)

Figure 1.3: Landing page for the ad shown in Figure 1.2 (Notice the original/landing page URL is different from the display URL)

### Matching Strategies and Pricing
Regardless of the matching strategy, every advertiser has to bid some amount on their bid phrase as shown in Figure 1.2. Next, the advertiser needs to choose the matching strategy. In the case of exact match, an ad is retrieved only if there is an exact match between the bid phrase of the ad and the text(query or Web page).

Broad match allow advertisers to choose initial bid phrase, and the ad placement engine takes care of finding relevant content for the ad even if there is no exact match.

In an online advertising ecosystem, one of the following pricing schemes is adopted: **Pay-per-Click (PPC)**, **Pay-per-Impression (PPI)**, and **Pay-per-Transaction (PPT)** Broder et al. [2007]. 
- In PPC model, the advertiser pays some amount each time a user clicks their ad. 
- In PPI model, the advertiser pays every time their ad is displayed against the content. 
- While in a PPT model the advertiser has to pay only when a user does a transaction after clicking on the ad.

First, the top k ads are fetched from the ad database based on the extent to which they match the content.

Once these top ads are retrieved they are ranked so as to maximize the overall expected revenue. Ranking in such a two-step fashion caters to the need of all the four parties involved – User, Advertiser, Publisher and Ad engine.

### Scenarios in Online Advertising
#### Contextual Advertising
Content targeting involves targeting websites ranging from blogs, forums, news pages, home pages to products sites and beyond. A user’s visit on a page typically indicates their implicit interest in Web page’s topic Broder et al. [2007]. This implicit interest can be exploited by placing relevant ads next to the content as there is a higher chance of user visiting the ad if it is relevant to the content.

Contextual Advertising can be seen as an interaction between the publisher, advertiser, ad placement engine, and the user. The **publisher** is the owner of content/Web page being targeted. The **advertiser** seeks to place their ad on the Web page. The **ad placement engine** acts as a mediator between the publisher and the advertiser. The ad placement engine decides which advertisement to be shown to which user. The **user** visits a Web page and is served the advertisements.

![](http://ou8qjsj0m.bkt.clouddn.com//18-2-6/35494073.jpg)

Figure 1.4: A typical Contextual Advertising scenario. Permission to use the image taken from the source: http://www.ezmoneyon.net/wp-content/uploads/2008/01.

#### Sponsored Search
In Sponsored Search, relevant advertisements are shown in response to a search query. A typical Sponsored Search scenario is illustrated in Figure 1.5.

![](http://ou8qjsj0m.bkt.clouddn.com//18-2-6/95201101.jpg)

Figure 1.5: A typical Sponsored Search scenario

Sponsored Search can be seen as an interaction between three par- ties - search engine, user and the advertiser. The **user** issues a query to search engine related to the topic on which he/she seeks information. **Advertisers** and **search engines** try to exploit the immediate interest of the user in the topic by displaying ads relevant to the query topic. In a typical setting, advertisers bid on certain keywords known as bid terms and choose either advance or broad match. The advertiser’s ad may get displayed based on the match between ad’s bid term and the search query and the amount bid by the advertiser. Search engines try to rank the ads in a way that maximizes their revenue.

#### Display Advertising
Display ads (also called banner ads) usually come in a rich multimedia form – image, video, flash and audio. In addition to direct response, display ads are also used for brand building Li and Jhang-Li [2009]. Also unlike Sponsored Search and Contextual Advertising, display ads are charged on a per impression basis Ghosh et al. [2009]. Almost 90% of the ads are billed on PPI basis in Display Advertising Shen [2002].

![](http://ou8qjsj0m.bkt.clouddn.com//18-2-6/32376661.jpg)

Figure 1.6: Showing Display Advertising scenario

As in the **PPI model**, bidding in Display Advertising happens on a per impression basis. Predominantly, the sale of the impression slots on the publisher's page can happen in two ways – (a) Bulk sale of impressions and (b) Auction individual impressions in real time. In the case of bulk sale of impressions, the advertiser buys n number of impressions on the publisher's page. The ad is shown on the page until the advertiser's budget is exhausted. In a bulk sale, all the impressions are bought at a flat price. In the second type, the impressions are auctioned similar to a share market. For each impression, a separate auction takes place where a variety of advertisers bid for the impression slot. This entire process of auction happens in real time – the user visits a site, the publisher raises a bid request for the ad slot, the advertisers bid for the impression and the winner of the auction is allowed to display their ad on the page. 

### Issues and Challenges
Following are the impediments and challenges in CA:

- **Short Ad text**: Ad text is short and is intended to attract the user, hence it contains short non-grammatical English phrases. This poses a lot of challenges in content level targeting Choi et al. [2010], Ribeiro Neto et al. [2005], Broder et al. [2007]. Traditional retrieval algorithms are not mainly designed to handle short text.
- **Sparse queries (Vocabulary mismatch)**: In case of Sponsored Search, the query is issued by the user and ads are submitted by the advertiser and both are short, this often induces a problem called vocabulary mis-match Ribeiro Neto et al. [2005] between the ads and the queries Radlinski et al. [2008], Raghavan and Iyer [2010], Jones et al. [2006]. As the name suggests, vocabulary mismatch implies that the ad and query are semantically related but there is no syntactic similarity (word overlap) between them. For example, a query ‘Camera’ should also retrieve ads bidding on terms like ‘Sony Cyber-shot’ or ‘Sony EOS’.
- **Noisy Web content**: Web pages usually contain noisy data. The application of traditional information retrieval algorithm to retrieve ads from such noisy pages may lead to irrelevant ads. Therefore, the noisy content of the Web page needs to be dealt with in a more sophisticated manner Yih et al. [2006], Dave and Varma [2010a], Wu and Bolivar [2008].
- **No Page Rank!**: Unlike Web search, there is no link structure among the documents (ads) that can be exploited to apply algorithms like Page Rank or HITS to serve authoritative and relevant ads.
- **Ad Spam and Click Spam**: Advertisers bid on false keywords or highly frequent keywords that are not related to their business. Identifying such spam ads is one of the biggest challenges. Click spam is the fraudulent spam by the user with no real intention of exploring the ad. If such clicks are not detected, advertisers can get falsely billed for such clicks Dave et al. [2012b].
- **Opinionated Content**: Some of the Web page content like forums and in particular microblogs are highly opinionated. Targeting ads on opinionated posts involves dealing with negative sentiments. Negative sentiments demand a separate treatment. Intuitively, targeting ads on negative sentiments may defeat the intended purpose of advertising. Imagine an ad for a fast food product, on a Web page talking about health concerns caused by fast food Fan and Chang [2009], Liu et al. [2008].
- **Dealing with new Ads in Ranking**: In order to maximize the expected revenue, the search engine must predict the probability of a click on an ad, more commonly known as click-through rate (CTR) of an ad. Historical click- through log is the most obvious proxy for estimating the CTR of the ads. However, for new ads entering into the system and infrequent/rare ads, it is very difficult to estimate the CTR as there is a very little or no information available through the click-through logs Dave and Varma [2010b], Richardson et al. [2007], Shaparenko et al. [2009], Regelson and Fain [2006], Ashkan et al. [2009], Debmbsczynski et al. [2008].
- **How much can behavioral targeting help online advertising?** : One big question in the case of content level targeting is whether user behavior can also be incorporated to retrieve more relevant ads. If incorporating user behavior helps, it evokes second-order questions, what kind of data should be used to profile the user behavior and what should be the time frame from which the data is considered for user modeling Yan et al. [2009], Cheng and Cantú-Paz [2010b], Ahmed et al. [2011]. Display Advertising leverage user behavioral information for showing their ads. Hence modeling user information is critical to Display Advertising.
- **What to consider while targeting users?**: In the case of user level targeting, one of the challenges is to profile the user for targeting them. Advertisers gather information about the user from the cookies. User modeling is more challenging than content modeling, as unlike the content, the user behavior changes with time. In the case of user targeting based on their social circle, formulating a user’s influence on their contacts for various actions (like clicking on ads) is a big challenge Cheng and Cantú-Paz [2010b], Dave et al. [2011], Kempe et al. [2003], Hartline et al. [2008].
