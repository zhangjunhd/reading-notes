# 中国互联网广告生态
## 参与者
- `广告主（advertiser）`显然是指想为自己的品牌或者产品做广告的人，例如宝马、Intel、蒙牛。
- `媒体（publisher）`则是提供广告位置的载体，例如电视台、网站、杂志、楼宇。
- `广告商（agency）`本质上其实就是中介，帮广告主找媒体广告位，帮媒体找广告主。
- 这个产业链还有一个不能忽略的部分，那就是“消费”广告的人，即`受众（audience）`。受众都是有特点的，被分成一类一类相近的人群（persona或segmentation）。

![1](http://www.chinawebanalytics.cn/wp-content/uploads/2014/10/adver-agency-pub-aud.png)

## SSP(sell-side platform)
publishers想要卖出自己空余广告位的地方，也就是google adsense的模式。

### Ad Network&Ad Exchange
Ad Network（广告网络）从Publishers（网站和apps）收购广告位，然后卖给Advertisers（广告主）。AdSense属于Ad Network。

与Ad Network联合publishers不同，Ad Exchange不仅仅联合publishers，它同样把Ad Network联合起来，这些拥有广告位的，被统一用“供应方”（supply side）一词来指代。

Ad Exchange比Ad Network先进的地方在于它的定价机制。Ad Network上，对于供需双方而言，其实都没有对广告位的定价权，而是由Ad Network这个“中央政府”定价的“计划经济”；而Ad Exchange，则是一个真正意义上按照供需关系来运转的“市场经济”。Ad Exchange为每一个商品（商品这里暂时指广告位）提供了“价高者得”的机制。

![3](http://www.chinawebanalytics.cn/wp-content/uploads/2014/10/network-and-exchange.png)

Ad Exchange对于广告位的竞价是实时进行。这种实时进行的广告位竞价，被称为`Real Time Bidding`，简称为`RTB`，即“实时竞价”。 实时竞价一般是按照CPM或者CPC出价的，简单说就是按照广告被展现在受众面前的次数出价，或是按照广告被点击的次数出价。

世界上著名的Ad Exchange有Google收购DoubleClick之后最近弄出来的AdX；还有Yahoo收购的Right Media，这也是老牌的Ad Exchange了；此外微软有AdECNNIC，OpenX也有自己的Ad Exchange。

![4](http://www.chinawebanalytics.cn/wp-content/uploads/2014/10/dsp.png)

## DSP(demand-side platform)
（DSP）是需求方平台就是advertisers竞价获得广告，也就是google adwords的模式。

DSP同时把主流的Ad Exchange的系统都与自己驳接，然后提供给广告主们一个统一的更加简单的操作界面，DSP把Ad Exchange中的广告位的展示方式做了一个巨大的改变。在Ad Exchange中，广告位可就是广告位，但在DSP中，广告位这个概念被移除或是被淡化了，而target audience的概念则被提出来。

![5](http://www.chinawebanalytics.cn/wp-content/uploads/2014/10/dsp-chart.png)

广告主在DSP的操作界面中，告诉我你需要哪些人群，愿意出多少钱获得这些人群，我来帮你在Ad Exchange中操作。过去，是购买广告位，现在有了Ad Exchange和DSP，是直接购买目标受众。

程序化购买依赖于两个重要事情：其一，需要受众数据，准确的，海量的；其二，强大的自动化算法，保证最合理的竞价。

DSP自己有可能有受众数据，市场上也有专业提供者，被称为`DMP`，即Data Management Platform，数据管理平台。数据管理平台，简单讲，它们手中握有受众数据，并且能够让DSP驳接到他们这里，利用它们所有的数据。

DMP为了获取受众的数据，它必须至少做几件事情 ：其一，它需要为所有的受众每一个做一个标记（它售卖给广告主的是目标受众标签，其实是帮助广告主屏蔽底层细节，由DSP负责把目标受众标签映射到媒体广告位），这个标记在目前的技术条件下，主要是通过一种叫做cookie的事物完成的。而在更新的技术条件下，可能又有能够比cookie更多（甚至更好）的东西。其二，它还需要能够实现跨域追踪。

## 中国广告产业链生态图
![6](http://www.rtbchina.com/wp-content/uploads/2012/06/China-RTB-Ad-Tech-Landscape_V-September_2014.jpg)
