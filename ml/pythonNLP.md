![cover](https://img3.doubanio.com/lpic/s27313176.jpg)

    作者: (美)Steven Bird Ewan Klein Edward Loper 
    出版社: 人民邮电出版社
    原作名: Natural Language Processing With Python
    译者: 张旭 / 崔阳 / 刘海平 
    出版年: 2014-6-25
    页数: 508
    定价: 89.00
    装帧: 平装
    ISBN: 9787115333681

[豆瓣链接](https://book.douban.com/subject/25916599/)

- [NLTK入门](#nltk%e5%85%a5%e9%97%a8)
  - [搜索文本](#%e6%90%9c%e7%b4%a2%e6%96%87%e6%9c%ac)
  - [计数词汇](#%e8%ae%a1%e6%95%b0%e8%af%8d%e6%b1%87)
  - [将文本当作词链表](#%e5%b0%86%e6%96%87%e6%9c%ac%e5%bd%93%e4%bd%9c%e8%af%8d%e9%93%be%e8%a1%a8)
    - [索引列表](#%e7%b4%a2%e5%bc%95%e5%88%97%e8%a1%a8)
  - [简单的统计](#%e7%ae%80%e5%8d%95%e7%9a%84%e7%bb%9f%e8%ae%a1)
    - [频率分布](#%e9%a2%91%e7%8e%87%e5%88%86%e5%b8%83)
    - [词语搭配和双连词](#%e8%af%8d%e8%af%ad%e6%90%ad%e9%85%8d%e5%92%8c%e5%8f%8c%e8%bf%9e%e8%af%8d)
    - [计算其他东西](#%e8%ae%a1%e7%ae%97%e5%85%b6%e4%bb%96%e4%b8%9c%e8%a5%bf)

# NLTK入门
从NLTK的book模块中加载所有的条目

```py
%matplotlib inline
from nltk.book import *

*** Introductory Examples for the NLTK Book ***
Loading text1, ..., text9 and sent1, ..., sent9
Type the name of the text or sentence to view it.
Type: 'texts()' or 'sents()' to list the materials.
text1: Moby Dick by Herman Melville 1851
text2: Sense and Sensibility by Jane Austen 1811
text3: The Book of Genesis
text4: Inaugural Address Corpus
text5: Chat Corpus
text6: Monty Python and the Holy Grail
text7: Wall Street Journal
text8: Personals Corpus
text9: The Man Who Was Thursday by G . K . Chesterton 1908
```

## 搜索文本
显示指定单词的出现情况，同时显示一些上下文。

```py
text1.concordance("monstrous")

Displaying 11 of 11 matches:
ong the former , one was of a most monstrous size . ... This came towards us , 
ON OF THE PSALMS . " Touching that monstrous bulk of the whale or ork we have r
ll over with a heathenish array of monstrous clubs and spears . Some were thick
d as you gazed , and wondered what monstrous cannibal and savage could ever hav
that has survived the flood ; most monstrous and most mountainous ! That Himmal
they might scout at Moby Dick as a monstrous fable , or still worse and more de
th of Radney .'" CHAPTER 55 Of the Monstrous Pictures of Whales . I shall ere l
ing Scenes . In connexion with the monstrous pictures of whales , I am strongly
ere to enter upon those still more monstrous stories of them which are to be fo
ght have been rummaged out of this monstrous cabinet there is no telling . But 
of Whale - Bones ; for Whales of a monstrous size are oftentimes cast up dead u
```

还有哪些词出现在相似的上下文中？

```py
text1.similar("monstrous")

imperial subtly impalpable pitiable curious abundant perilous
trustworthy untoward singular lamentable few determined maddens
horrible tyrannical lazy mystifying christian exasperate
```

研究共用两个或两个以上词汇的上下文。

```py
text2.common_contexts(["monstrous", "very"])

a_pretty is_pretty a_lucky am_glad be_glad
```

判断词在文本中的位置：dispersion plot。每一列代表一个单词，每一行代表整个文本。

```py
text4.dispersion_plot(["citizens", "democracy", "freedom", "duties", "America"])
```

![](pythonNLP1.png)

Figure 1-2. Lexical dispersion plot for words in U.S. Presidential Inaugural Addresses: This can be used to investigate changes in language use over time.

## 计数词汇
以文本中出现的单词和标点符号为单位算出文本从头到尾的长度。

```py
len(text3)
44764
```

《创世纪》有44764个单词和标点符号，也称作“token”。token是表示一组字符序列的术语。

有多少不同的单词？

```py
sorted(set(text3))[:10]
[u'!', u"'", u'(', u')', u',', u',)', u'.', u'.)', u':', u';']

len(set(text3))
2789
```

对文本词汇丰富度进行测量。

```py
from __future__ import division
len(text3) / len(set(text3))

16.050197203298673
```

计数一个单词在文本中出现的次数，再计算一个特定词在文本中占据的百分比。

```py
text3.count("smote")
5

100 * text4.count('a') / len(text4)
1.4643016433938312
```

做成函数：

```py
def lexical_diversity(text):
    return len(text) / len(set(text))

def percentage(count, total):
    return 100 * count / total
```

## 将文本当作词链表
### 索引列表
文本中这个索引处——例如文本中第173个词。

```py
text4[173]
u'awaken'
```

从大文本种任意抽取语言片段，术语叫做`slicing`。

```py
text5[16715:16735]
[u'U86',
 u'thats',
 u'why',
 u'something',
 u'like',
 u'gamefly',
 u'is',
 u'so',
 u'good',
 u'because',
 u'you',
 u'can',
 u'actually',
 u'play',
 u'a',
 u'full',
 u'game',
 u'without',
 u'buying',
 u'it']

text6[1600:1625]
[u'We',
 u"'",
 u're',
 u'an',
 u'anarcho',
 u'-',
 u'syndicalist',
 u'commune',
 u'.',
 u'We',
 u'take',
 u'it',
 u'in',
 u'turns',
 u'to',
 u'act',
 u'as',
 u'a',
 u'sort',
 u'of',
 u'executive',
 u'officer',
 u'for',
 u'the',
 u'week']
```

## 简单的统计
### 频率分布
![](pythonNLP2.png)

图1-3中的表被称为frequency distribution，显示的是每一个词项在文本中出现的频率。

```py
fdist1 = FreqDist(text1)
len(fdist1)
19317

vocabulary1 = fdist1.keys()
vocabulary1[:50]
[u'funereal',
 u'unscientific',
 u'divinely',
 u'foul',
 u'four',
 u'gag',
 u'prefix',
 u'woods',
 u'clotted',
 u'Duck',
 u'hanging',
 u'plaudits',
 u'woody',
 u'Until',
 u'marching',
 u'disobeying',
 u'canes',
 u'granting',
 u'advantage',
 u'Westers',
 u'insertion',
 u'DRYDEN',
 u'formless',
 u'Untried',
 u'superficially',
 u'Western',
 u'portentous',
 u'beacon',
 u'meadows',
 u'sinking',
 u'Ding',
 u'Spurn',
 u'treasuries',
 u'churned',
 u'oceans',
 u'powders',
 u'tinkerings',
 u'tantalizing',
 u'yellow',
 u'bolting',
 u'uncertain',
 u'stabbed',
 u'bringing',
 u'elevations',
 u'ferreting',
 u'believers',
 u'wooded',
 u'songster',
 u'uttering',
 u'scholar']

fdist1['whale']
906

fdist1.plot(50, cumulative=True)
```

![](pythonNLP3.png)

Figure 1-4. Cumulative frequency plot for the 50 most frequently used words in Moby Dick, which account for nearly half of the tokens.

whale出现超过900次。产生关于这些词汇的累积频率图，使用fdist1.plot(50, cumulative=True)产生图1-4。这50个词占了这本书的将近一半。

如果高频词对我们没有帮助，那么只出现一次的词（所谓的hapaxes）如何？

```py
fdist1.hapaxes()[:10]
[u'funereal',
 u'unscientific',
 u'prefix',
 u'plaudits',
 u'woody',
 u'disobeying',
 u'Westers',
 u'DRYDEN',
 u'Untried',
 u'superficially']
```

所有长度超过7个字符并且出现次数超过7次的词。

```py
fdist5 = FreqDist(text5)
sorted([w for w in set(text5) if len(w) > 7 and fdist5[w] > 7])
[u'#14-19teens',
 u'#talkcity_adults',
 u'((((((((((',
 u'........',
 u'Question',
 u'actually',
 u'anything',
 u'computer',
 u'cute.-ass',
 u'everyone',
 u'football',
 u'innocent',
 u'listening',
 u'remember',
 u'seriously',
 u'something',
 u'together',
 u'tomorrow',
 u'watching']
```

### 词语搭配和双连词
collocation是不经常在一起出现的词序列。要获取搭配，首先从提取文本词汇中的词对也就是bigrams开始。

```py
from nltk import bigrams
bigrams(['more', 'is', 'said', 'than', 'done'])
list(bigrams(['more', 'is', 'said', 'than', 'done']))
[('more', 'is'), ('is', 'said'), ('said', 'than'), ('than', 'done')]
```

collocation基本上是频繁的bigrams。找出出现频率比预期更频繁的bigrams:

```py
text4.collocations()
United States; fellow citizens; four years; years ago; Federal
Government; General Government; American people; Vice President; Old
World; Almighty God; Fellow citizens; Chief Magistrate; Chief Justice;
God bless; every citizen; Indian tribes; public debt; one another;
foreign nations; political parties
```

### 计算其他东西
查看文本中词长的分布：

```py
[len(w) for w in text1][:10]
[1, 4, 4, 2, 6, 8, 4, 1, 9, 1]

fdist = FreqDist([len(w) for w in text1])
fdist
FreqDist({1: 47933,
          2: 38513,
          3: 50223,
          4: 42345,
          5: 26597,
          6: 17111,
          7: 14399,
          8: 9966,
          9: 6428,
          10: 3528,
          11: 1873,
          12: 1053,
          13: 567,
          14: 177,
          15: 70,
          16: 22,
          17: 12,
          18: 1,
          20: 1})

fdist.keys()
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 20]
```

最频繁词的长度是3，长度为3的词有50000多个（约占书中全部词汇的20%）。

Table 1-2. Functions defined for NLTK’s frequency distributions

| Example | Description  |
 | ------- | -----------  |
 | fdist = FreqDist(samples) | Create a frequency distribution containing the given samples  |
 | fdist.inc(sample) | Increment the count for this sample  |
 | fdist['monstrous'] | Count of the number of times a given sample occurred  |
 | fdist.freq('monstrous') | Frequency of a given sample  |
 | fdist.N() | Total number of samples  |
 | fdist.keys() | The samples sorted in order of decreasing frequency  |
 | for sample in fdist: | Iterate over the samples, in order of decreasing frequency  |
 | fdist.max() | Sample with the greatest count  |
 | fdist.tabulate() | Tabulate the frequency distribution  |
 | fdist.plot() | Graphical plot of the frequency distribution  |
 | fdist.plot(cumulative=True) | Cumulative plot of the frequency distribution  |
 | fdist1 < fdist2 | Test if samples in fdist1 occur less frequently than in fdist2 |



















































































