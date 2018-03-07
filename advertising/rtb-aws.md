# Building a Real-Time Bidding Platform on AWS
https://d0.awsstatic.com/whitepapers/Building_a_Real_Time_Bidding_Platform_on_AWS_v1_Final.pdf

## Real-Time Bidding Explained
![](http://ou8qjsj0m.bkt.clouddn.com//18-2-1/94825847.jpg)

## Components of a RTB Platform
![](http://ou8qjsj0m.bkt.clouddn.com//18-2-1/45058526.jpg)

### Bid Traffic Ingestion and Processing
1. As a user goes to a website, that website will contact an ad exchange that will then send out bid traffic to RTB platforms for bids on this impression.
    - The bid traffic includes just the website URL that is being browsed, ad/size, and location on that website, and demographic information about the user that the publisher knows.
1. This data must be ingested in real time and a decision must be made on whether you want to bid on this impression and the amount you’re willing to bid.
    - Each ad request comes with some form of `user identification (ID)` from the ad exchange.
    - The bidder needs to be able to leverage this user ID and all available data for that user. The bidder must map this user ID to another source of information (e.g., a cookie store) to match the user, calculate the value of the bid, and probability of winning the auction.
1. Then, the bidder sends the bid, along with the ad link tied to that bid, so that the ad creative can be displayed to the end user in the case of an auction win.

### Analysis Traffic Ingestion and Processing
Analysis traffic is usually not as time-sensitive as bidding traffic, but it provides valuable information, which can be used to make the real-time bidding decision on future bid traffic.

This data is critical to making an intelligent decision on how much any given impression is worth to the advertiser and how likely it is that this impression will stick with the website user or lead to a direct action like a click-through.

### Low Latency Data Repository
The primary purpose of a low latency data repository is to look up and make decisions very quickly on not only if you wish to bid on an impression but also how much you are willing to pay for that impression. This decision is based on three key factors: 
1. knowledge about the user (user profile) 
1. how well the user matches a set of pre-determined advertising campaigns with specific budget objectives
1. how often the user has a specific ad

### Durable Data Repository for Long-Term Storage
The durable data repository is a storage platform built to hold large amounts of data inexpensively. It will hold all historical data for the analytical pipelines for data transformation, enrichment, and preparation for rich analytics.

### Analytics Platform
An analytics platform is used to run computation models, such as machine learning, to calculate the likelihood of specific campaigns getting the desired result from specific demographics and users. This platform will keep track of users across multiple devices, record their activities, and update user profiles and audience segments. It will run the analytics off the different data feeds and the long term durable data repository, It will take the analytical results and store them an indexed manner in the low-latency data store, so that bid processing can quickly find the data it needs to make its bidding decisions.

### Campaign Management
Campaign management is typically a multi-tenant web application that manages the advertising campaigns and controls the budgets for different advertisers. This web application provides detailed statistics of the bids that have already taken place in the campaigns and the audiences that have provided the best response.

## Reference Architecture Example
![](http://ou8qjsj0m.bkt.clouddn.com//18-2-1/88586644.jpg)
