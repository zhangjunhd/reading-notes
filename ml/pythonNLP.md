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
- [获取文本语料库](#%e8%8e%b7%e5%8f%96%e6%96%87%e6%9c%ac%e8%af%ad%e6%96%99%e5%ba%93)
  - [古腾堡语料库](#%e5%8f%a4%e8%85%be%e5%a0%a1%e8%af%ad%e6%96%99%e5%ba%93)
  - [网络和聊天文本](#%e7%bd%91%e7%bb%9c%e5%92%8c%e8%81%8a%e5%a4%a9%e6%96%87%e6%9c%ac)
  - [布朗语料库](#%e5%b8%83%e6%9c%97%e8%af%ad%e6%96%99%e5%ba%93)
  - [路透社语料库](#%e8%b7%af%e9%80%8f%e7%a4%be%e8%af%ad%e6%96%99%e5%ba%93)
  - [就职演说语料库](#%e5%b0%b1%e8%81%8c%e6%bc%94%e8%af%b4%e8%af%ad%e6%96%99%e5%ba%93)
  - [其他语言的语料库](#%e5%85%b6%e4%bb%96%e8%af%ad%e8%a8%80%e7%9a%84%e8%af%ad%e6%96%99%e5%ba%93)
  - [文本语料库的结构](#%e6%96%87%e6%9c%ac%e8%af%ad%e6%96%99%e5%ba%93%e7%9a%84%e7%bb%93%e6%9e%84)
  - [载入你自己的语料库](#%e8%bd%bd%e5%85%a5%e4%bd%a0%e8%87%aa%e5%b7%b1%e7%9a%84%e8%af%ad%e6%96%99%e5%ba%93)
- [条件频率分布](#%e6%9d%a1%e4%bb%b6%e9%a2%91%e7%8e%87%e5%88%86%e5%b8%83)
  - [条件与事件](#%e6%9d%a1%e4%bb%b6%e4%b8%8e%e4%ba%8b%e4%bb%b6)
  - [按文体计数词汇](#%e6%8c%89%e6%96%87%e4%bd%93%e8%ae%a1%e6%95%b0%e8%af%8d%e6%b1%87)
  - [绘制分布图和分布表](#%e7%bb%98%e5%88%b6%e5%88%86%e5%b8%83%e5%9b%be%e5%92%8c%e5%88%86%e5%b8%83%e8%a1%a8)
  - [使用Bigrams生成随机文本](#%e4%bd%bf%e7%94%a8bigrams%e7%94%9f%e6%88%90%e9%9a%8f%e6%9c%ba%e6%96%87%e6%9c%ac)
- [词典资源](#%e8%af%8d%e5%85%b8%e8%b5%84%e6%ba%90)
  - [词汇列表语料库](#%e8%af%8d%e6%b1%87%e5%88%97%e8%a1%a8%e8%af%ad%e6%96%99%e5%ba%93)
  - [发音的词典](#%e5%8f%91%e9%9f%b3%e7%9a%84%e8%af%8d%e5%85%b8)
  - [比较词表](#%e6%af%94%e8%be%83%e8%af%8d%e8%a1%a8)
  - [词汇工具：Toolbox](#%e8%af%8d%e6%b1%87%e5%b7%a5%e5%85%b7toolbox)
  - [WordNet](#wordnet)
    - [意义与同义词](#%e6%84%8f%e4%b9%89%e4%b8%8e%e5%90%8c%e4%b9%89%e8%af%8d)
    - [WordNet的层次结构¶](#wordnet%e7%9a%84%e5%b1%82%e6%ac%a1%e7%bb%93%e6%9e%84%c2%b6)
    - [更多的词汇关系](#%e6%9b%b4%e5%a4%9a%e7%9a%84%e8%af%8d%e6%b1%87%e5%85%b3%e7%b3%bb)
    - [语义相似度](#%e8%af%ad%e4%b9%89%e7%9b%b8%e4%bc%bc%e5%ba%a6)

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

# 获取文本语料库
## 古腾堡语料库
代表既定的文学。这个语料库中的文件标识符。

```py
%matplotlib inline
import nltk
from nltk.corpus import gutenberg
gutenberg.fileids()

[u'austen-emma.txt',
 u'austen-persuasion.txt',
 u'austen-sense.txt',
 u'bible-kjv.txt',
 u'blake-poems.txt',
 u'bryant-stories.txt',
 u'burgess-busterbrown.txt',
 u'carroll-alice.txt',
 u'chesterton-ball.txt',
 u'chesterton-brown.txt',
 u'chesterton-thursday.txt',
 u'edgeworth-parents.txt',
 u'melville-moby_dick.txt',
 u'milton-paradise.txt',
 u'shakespeare-caesar.txt',
 u'shakespeare-hamlet.txt',
 u'shakespeare-macbeth.txt',
 u'whitman-leaves.txt']
```

找出emma包含多少个词。

```py
emma = gutenberg.words('austen-emma.txt')
len(emma)
192427
```

统计每个文本的3个统计量：平均词长、平均句子长度和文本中每个词出现的平均次数（词汇多样性得分）。

```py
for fileid in gutenberg.fileids():
    num_chars = len(gutenberg.raw(fileid))
    num_words = len(gutenberg.words(fileid))
    num_sents = len(gutenberg.sents(fileid))
    num_vocab = len(set([w.lower() for w in gutenberg.words(fileid)]))
    print int(num_chars/num_words), int(num_words/num_sents), int(num_words/num_vocab), fileid
4 24 26 austen-emma.txt
4 26 16 austen-persuasion.txt
4 28 22 austen-sense.txt
4 33 79 bible-kjv.txt
4 19 5 blake-poems.txt
4 19 14 bryant-stories.txt
4 17 12 burgess-busterbrown.txt
4 20 12 carroll-alice.txt
4 20 11 chesterton-ball.txt
4 22 11 chesterton-brown.txt
4 18 10 chesterton-thursday.txt
4 20 24 edgeworth-parents.txt
4 25 15 melville-moby_dick.txt
4 52 10 milton-paradise.txt
4 11 8 shakespeare-caesar.txt
4 12 7 shakespeare-hamlet.txt
4 12 6 shakespeare-macbeth.txt
4 36 12 whitman-leaves.txt
```

sents()函数把文本划分成句子，其中每一个句子是一个词链表。

```py
macbeth_sentences = gutenberg.sents('shakespeare-macbeth.txt')
macbeth_sentences
[[u'[', u'The', u'Tragedie', u'of', u'Macbeth', u'by', u'William', u'Shakespeare', u'1603', u']'], [u'Actus', u'Primus', u'.'], ...]

macbeth_sentences[1037]
[u'Good',
 u'night',
 u',',
 u'and',
 u'better',
 u'health',
 u'Attend',
 u'his',
 u'Maiesty']

longest_len = max([len(s) for s in macbeth_sentences])
longest_len
158

[s for s in macbeth_sentences if len(s) == longest_len][0][:10]
[u'Doubtfull',
 u'it',
 u'stood',
 u',',
 u'As',
 u'two',
 u'spent',
 u'Swimmers',
 u',',
 u'that']
```

## 网络和聊天文本
非正式的语言。

```py
from nltk.corpus import webtext
for fileid in webtext.fileids():
    print fileid, webtext.raw(fileid)[:65], '...'
firefox.txt Cookie Manager: "Don't allow sites that set removed cookies to se ...
grail.txt SCENE 1: [wind] [clop clop clop] 
KING ARTHUR: Whoa there!  [clop ...
overheard.txt White guy: So, do you have any plans for this evening?
Asian girl ...
pirates.txt PIRATES OF THE CARRIBEAN: DEAD MAN'S CHEST, by Ted Elliott & Terr ...
singles.txt 25 SEXY MALE, seeks attrac older single lady, for discreet encoun ...
wine.txt Lovely delicate, fragrant Rhone wine. Polished leather and strawb ...
```

即时消息聊天会话语料库：

```py
from nltk.corpus import nps_chat
chatroom = nps_chat.posts('10-19-20s_706posts.xml')
chatroom[123]
[u'i',
 u'do',
 u"n't",
 u'want',
 u'hot',
 u'pics',
 u'of',
 u'a',
 u'female',
 u',',
 u'I',
 u'can',
 u'look',
 u'in',
 u'a',
 u'mirror',
 u'.']
```

## 布朗语料库
包含500个不同来源的文本，按照文体分类，如新闻、社论等。

```py
from nltk.corpus import brown
brown.categories()
[u'adventure',
 u'belles_lettres',
 u'editorial',
 u'fiction',
 u'government',
 u'hobbies',
 u'humor',
 u'learned',
 u'lore',
 u'mystery',
 u'news',
 u'religion',
 u'reviews',
 u'romance',
 u'science_fiction']

brown.words(categories='news')
[u'The', u'Fulton', u'County', u'Grand', u'Jury', ...]

brown.words(fileids=['cg22'])
[u'Does', u'our', u'society', u'have', u'a', ...]

brown.sents(categories=['news', 'editorial', 'reviews'])
[[u'The', u'Fulton', u'County', u'Grand', u'Jury', u'said', u'Friday', u'an', u'investigation', u'of', u"Atlanta's", u'recent', u'primary', u'election', u'produced', u'``', u'no', u'evidence', u"''", u'that', u'any', u'irregularities', u'took', u'place', u'.'], [u'The', u'jury', u'further', u'said', u'in', u'term-end', u'presentments', u'that', u'the', u'City', u'Executive', u'Committee', u',', u'which', u'had', u'over-all', u'charge', u'of', u'the', u'election', u',', u'``', u'deserves', u'the', u'praise', u'and', u'thanks', u'of', u'the', u'City', u'of', u'Atlanta', u"''", u'for', u'the', u'manner', u'in', u'which', u'the', u'election', u'was', u'conducted', u'.'], ...]
```

布朗语料库是一个研究文体之间的系统性差异（又叫做stylistics文体学的语言学研究）的资源。第一步：对特定文体进行计数。

```py
from nltk.corpus import brown
news_text = brown.words(categories='news')
fdist = nltk.FreqDist([w.lower() for w in news_text])
modals = ['can', 'could', 'may', 'might', 'must', 'will']
for m in modals:
    print m + ':', fdist[m],
can: 94 could: 87 may: 93 might: 38 must: 53 will: 389
```

统计每一个感兴趣的文体。

```py
cfd = nltk.ConditionalFreqDist(
    (genre, word)
    for genre in brown.categories()
    for word in brown.words(categories=genre))
genres = ['news', 'religion', 'hobbies', 'science_fiction', 'romance', 'humor']
modals = ['can', 'could', 'may', 'might', 'must', 'will']
cfd.tabulate(conditions=genres, samples=modals)

                  can could   may might  must  will 
           news    93    86    66    38    50   389 
       religion    82    59    78    12    54    71 
        hobbies   268    58   131    22    83   264 
science_fiction    16    49     4    12     8    16 
        romance    74   193    11    51    45    43 
          humor    16    30     8     8     9    13 
```

观察发现新闻文体中最常见的情态动词是will，而言情文体中最常见的情态动词是could。

## 路透社语料库
路透社语料库包含10788个新闻文档，共计130万字。这些文档分成90个主题，按照“训练”和“测试”分为两组。

```py
from nltk.corpus import reuters
reuters.fileids()[:10]
['test/14826',
 'test/14828',
 'test/14829',
 'test/14832',
 'test/14833',
 'test/14839',
 'test/14840',
 'test/14841',
 'test/14842',
 'test/14843']

reuters.categories()
[u'acq',
 u'alum',
 u'barley',
 u'bop',
 u'carcass',
 u'castor-oil',
 u'cocoa',
 u'coconut',
 u'coconut-oil',
 u'coffee',
 u'copper',
 u'copra-cake',
 u'corn',
 u'cotton',
 u'cotton-oil',
 u'cpi',
 u'cpu',
 u'crude',
 u'dfl',
 u'dlr',
 u'dmk',
 u'earn',
 u'fuel',
 u'gas',
 u'gnp',
 u'gold',
 u'grain',
 u'groundnut',
 u'groundnut-oil',
 u'heat',
 u'hog',
 u'housing',
 u'income',
 u'instal-debt',
 u'interest',
 u'ipi',
 u'iron-steel',
 u'jet',
 u'jobs',
 u'l-cattle',
 u'lead',
 u'lei',
 u'lin-oil',
 u'livestock',
 u'lumber',
 u'meal-feed',
 u'money-fx',
 u'money-supply',
 u'naphtha',
 u'nat-gas',
 u'nickel',
 u'nkr',
 u'nzdlr',
 u'oat',
 u'oilseed',
 u'orange',
 u'palladium',
 u'palm-oil',
 u'palmkernel',
 u'pet-chem',
 u'platinum',
 u'potato',
 u'propane',
 u'rand',
 u'rape-oil',
 u'rapeseed',
 u'reserves',
 u'retail',
 u'rice',
 u'rubber',
 u'rye',
 u'ship',
 u'silver',
 u'sorghum',
 u'soy-meal',
 u'soy-oil',
 u'soybean',
 u'strategic-metal',
 u'sugar',
 u'sun-meal',
 u'sun-oil',
 u'sunseed',
 u'tea',
 u'tin',
 u'trade',
 u'veg-oil',
 u'wheat',
 u'wpi',
 u'yen',
 u'zinc']
```

与布朗语料库不同，路透社语料库的类别时候互相重叠的，因为新闻报道往往涉及多个主题。

```py
reuters.categories('training/9865')
[u'barley', u'corn', u'grain', u'wheat']

reuters.categories(['training/9865', 'training/9880'])
[u'barley', u'corn', u'grain', u'money-fx', u'wheat']

reuters.fileids('barley')
[u'test/15618',
 u'test/15649',
 u'test/15676',
 u'test/15728',
 u'test/15871',
 u'test/15875',
 u'test/15952',
 u'test/17767',
 u'test/17769',
 u'test/18024',
 u'test/18263',
 u'test/18908',
 u'test/19275',
 u'test/19668',
 u'training/10175',
 u'training/1067',
 u'training/11208',
 u'training/11316',
 u'training/11885',
 u'training/12428',
 u'training/13099',
 u'training/13744',
 u'training/13795',
 u'training/13852',
 u'training/13856',
 u'training/1652',
 u'training/1970',
 u'training/2044',
 u'training/2171',
 u'training/2172',
 u'training/2191',
 u'training/2217',
 u'training/2232',
 u'training/3132',
 u'training/3324',
 u'training/395',
 u'training/4280',
 u'training/4296',
 u'training/5',
 u'training/501',
 u'training/5467',
 u'training/5610',
 u'training/5640',
 u'training/6626',
 u'training/7205',
 u'training/7579',
 u'training/8213',
 u'training/8257',
 u'training/8759',
 u'training/9865',
 u'training/9958']

reuters.fileids(['barley', 'corn'])[:10]
[u'test/14832',
 u'test/14858',
 u'test/15033',
 u'test/15043',
 u'test/15106',
 u'test/15287',
 u'test/15341',
 u'test/15618',
 u'test/15648',
 u'test/15649']

reuters.words('training/9865')[:14]
[u'FRENCH',
 u'FREE',
 u'MARKET',
 u'CEREAL',
 u'EXPORT',
 u'BIDS',
 u'DETAILED',
 u'French',
 u'operators',
 u'have',
 u'requested',
 u'licences',
 u'to',
 u'export']

reuters.words(['training/9865', 'training/9880'])
[u'FRENCH', u'FREE', u'MARKET', u'CEREAL', u'EXPORT', ...]

reuters.words(categories='barley')
[u'FRENCH', u'FREE', u'MARKET', u'CEREAL', u'EXPORT', ...]

reuters.words(categories=['barley', 'corn'])
[u'THAI', u'TRADE', u'DEFICIT', u'WIDENS', u'IN', ...]
```

## 就职演说语料库
语料库实际上是55个文本的集合，每个文本都是一个总统的演说。这个集合的一个显著特性是时间维度。

```py
from nltk.corpus import inaugural
inaugural.fileids()
[u'1789-Washington.txt',
 u'1793-Washington.txt',
 u'1797-Adams.txt',
 u'1801-Jefferson.txt',
 u'1805-Jefferson.txt',
 u'1809-Madison.txt',
 u'1813-Madison.txt',
 u'1817-Monroe.txt',
 u'1821-Monroe.txt',
 u'1825-Adams.txt',
 u'1829-Jackson.txt',
 u'1833-Jackson.txt',
 u'1837-VanBuren.txt',
 u'1841-Harrison.txt',
 u'1845-Polk.txt',
 u'1849-Taylor.txt',
 u'1853-Pierce.txt',
 u'1857-Buchanan.txt',
 u'1861-Lincoln.txt',
 u'1865-Lincoln.txt',
 u'1869-Grant.txt',
 u'1873-Grant.txt',
 u'1877-Hayes.txt',
 u'1881-Garfield.txt',
 u'1885-Cleveland.txt',
 u'1889-Harrison.txt',
 u'1893-Cleveland.txt',
 u'1897-McKinley.txt',
 u'1901-McKinley.txt',
 u'1905-Roosevelt.txt',
 u'1909-Taft.txt',
 u'1913-Wilson.txt',
 u'1917-Wilson.txt',
 u'1921-Harding.txt',
 u'1925-Coolidge.txt',
 u'1929-Hoover.txt',
 u'1933-Roosevelt.txt',
 u'1937-Roosevelt.txt',
 u'1941-Roosevelt.txt',
 u'1945-Roosevelt.txt',
 u'1949-Truman.txt',
 u'1953-Eisenhower.txt',
 u'1957-Eisenhower.txt',
 u'1961-Kennedy.txt',
 u'1965-Johnson.txt',
 u'1969-Nixon.txt',
 u'1973-Nixon.txt',
 u'1977-Carter.txt',
 u'1981-Reagan.txt',
 u'1985-Reagan.txt',
 u'1989-Bush.txt',
 u'1993-Clinton.txt',
 u'1997-Clinton.txt',
 u'2001-Bush.txt',
 u'2005-Bush.txt',
 u'2009-Obama.txt']

[fileid[:4] for fileid in inaugural.fileids()]
[u'1789',
 u'1793',
 u'1797',
 u'1801',
 u'1805',
 u'1809',
 u'1813',
 u'1817',
 u'1821',
 u'1825',
 u'1829',
 u'1833',
 u'1837',
 u'1841',
 u'1845',
 u'1849',
 u'1853',
 u'1857',
 u'1861',
 u'1865',
 u'1869',
 u'1873',
 u'1877',
 u'1881',
 u'1885',
 u'1889',
 u'1893',
 u'1897',
 u'1901',
 u'1905',
 u'1909',
 u'1913',
 u'1917',
 u'1921',
 u'1925',
 u'1929',
 u'1933',
 u'1937',
 u'1941',
 u'1945',
 u'1949',
 u'1953',
 u'1957',
 u'1961',
 u'1965',
 u'1969',
 u'1973',
 u'1977',
 u'1981',
 u'1985',
 u'1989',
 u'1993',
 u'1997',
 u'2001',
 u'2005',
 u'2009']

cfd = nltk.ConditionalFreqDist(
    (target, fileid[:4])
    for fileid in inaugural.fileids()
    for w in inaugural.words(fileid)
    for target in ['america', 'citizen'] if w.lower().startswith(target))
cfd.plot()
```

![](pythonNLP4.png)

Figure 2-1. Plot of a conditional frequency distribution: All words in the Inaugural Address Corpus that begin with america or citizen are counted; separate counts are kept for each address; these are plotted so that trends in usage over time can be observed; counts are not normalized for document length.

## 其他语言的语料库
多国语言的语料库。

```py
nltk.corpus.cess_esp.words()
[u'El', u'grupo', u'estatal', ...]

nltk.corpus.floresta.words()
[u'Um', u'revivalismo', u'refrescante', u'O', ...]

nltk.corpus.indian.words('hindi.pos')
[u'\u092a\u0942\u0930\u094d\u0923', u'\u092a\u094d\u0930\u0924\u093f\u092c\u0902\u0927', ...]

nltk.corpus.udhr.fileids()[:10]
[u'Abkhaz-Cyrillic+Abkh',
 u'Abkhaz-UTF8',
 u'Achehnese-Latin1',
 u'Achuar-Shiwiar-Latin1',
 u'Adja-UTF8',
 u'Afaan_Oromo_Oromiffa-Latin1',
 u'Afrikaans-Latin1',
 u'Aguaruna-Latin1',
 u'Akuapem_Twi-UTF8',
 u'Albanian_Shqip-Latin1']

nltk.corpus.udhr.words('Javanese-Latin1')[11:]
[u'Saben', u'umat', u'manungsa', u'lair', u'kanthi', ...]
```

udhr包含有超过300种语言的世界人权宣言。利用条件频率分布研究udhr语料库中不同语言版本中之长的差异。

```py
from nltk.corpus import udhr
languages = ['Chickasaw', 'English', 'German_Deutsch',
             'Greenlandic_Inuktikut', 'Hungarian_Magyar', 'Ibibio_Efik']
cfd = nltk.ConditionalFreqDist(
    (lang, len(word))
    for lang in languages
    for word in udhr.words(lang + '-Latin1'))
cfd.plot(cumulative=True)
```

![](pythonNLP5.png)

Figure 2-2. Cumulative word length distributions: Six translations of the Universal Declaration of Human Rights are processed; this graph shows that words having five or fewer letters account for about 80% of Ibibio text, 60% of German text, and 25% of Inuktitut text.

## 文本语料库的结构
![](pythonNLP6.png)

Figure 2-3. Common structures for text corpora: The simplest kind of corpus is a collection of isolated texts with no particular organization; some corpora are structured into categories, such as genre (Brown Corpus); some categorizations overlap, such as topic categories (Reuters Corpus); other corpora represent language use over time (Inaugural Address Corpus).

Table 2-3. Basic corpus functionality defined in NLTK: More documentation can be found using help(nltk.corpus.reader) and by reading the online Corpus HOWTO at http://www.nltk.org/howto.

| Example | Description |
|------- | ----------- |
|fileids() | The files of the corpus |
|fileids([categories]) | The files of the corpus corresponding to these categories |
|categories() | The categories of the corpus |
|categories([fileids]) | The categories of the corpus corresponding to these files |
|raw() | The raw content of the corpus |
|raw(fileids=[f1,f2,f3]) | The raw content of the specified files |
|raw(categories=[c1,c2]) | The raw content of the specified categories |
|words() | The words of the whole corpus |
|words(fileids=[f1,f2,f3]) | The words of the specified fileids |
|words(categories=[c1,c2]) | The words of the specified categories |
|sents() | The sentences of the specified categories |
|sents(fileids=[f1,f2,f3]) | The sentences of the specified fileids |
|sents(categories=[c1,c2]) | The sentences of the specified categories |
|abspath(fileid) | The location of the given file on disk |
|encoding(fileid) | The encoding of the file (if known) |
|open(fileid) | Open a stream for reading the given corpus file |
|root() | The path to the root of locally installed corpus |
|readme() | The contents of the README file of the corpus |

## 载入你自己的语料库
txt文件载入。

```py
from nltk.corpus import PlaintextCorpusReader
corpus_root = '/usr/share/dict'
wordlists = PlaintextCorpusReader(corpus_root, '.*')
wordlists.fileids()
['README', 'connectives', 'propernames', 'web2', 'web2a', 'words']

wordlists.words('connectives')
[u'the', u'of', u'and', u'to', u'a', u'in', u'that', ...]
```

载入宾州树库的副本。

```py
from nltk.corpus import BracketParseCorpusReader
corpus_root = r"C:\corpora\penntreebank\parsed\mrg\wsj"
file_pattern = r".*/wsj_.*\.mrg"
ptb = BracketParseCorpusReader(corpus_root, file_pattern)
ptb.fileids()
['00/wsj_0001.mrg', '00/wsj_0002.mrg', '00/wsj_0003.mrg', '00/wsj_0004.mrg', ...]

len(ptb.sents())
49208

ptb.sents(fileids='20/wsj_2013.mrg')[19]
['The', '55-year-old', 'Mr.', 'Noriega', 'is', "n't", 'as', 'smooth', 'as', 'the',
'shah', 'of', 'Iran', ',', 'as', 'well-born', 'as', 'Nicaragua', "'s", 'Anastasio',
'Somoza', ',', 'as', 'imperial', 'as', 'Ferdinand', 'Marcos', 'of', 'the', 'Philippines',
'or', 'as', 'bloody', 'as', 'Haiti', "'s", 'Baby', Doc', 'Duvalier', '.']
```

# 条件频率分布
conditional frequency distribution 是频率分布的集合，每个频率分布有一个不同的“条件”。这个条件通常是文本的类别。

![](pythonNLP7.png)

Figure 2-4. Counting words appearing in a text collection (a conditional frequency distribution).

## 条件与事件
条件频率分布需要给每个事件关联一个条件。每对的形式是：（条件，事件）。如果我们按文体处理整个布朗语料库，将有15个条件（一个文体一个条件）和1161192个事件（一个词一个事件）。

## 按文体计数词汇
只看两个文体：新闻和言情。对于每个文体，遍历文体中的每个词以产生与词的配对。

```py
%matplotlib inline
from nltk.corpus import brown

genre_word = [(genre, word)
              for genre in ['news', 'romance']
              for word in brown.words(categories=genre)]
len(genre_word)
170576

import nltk

cfd = nltk.ConditionalFreqDist(genre_word)
len(cfd)
2

cfd.conditions()
['romance', 'news']
```

访问这两个条件，它们每一个都只有一个频率分布。

```py
list(cfd['romance'])[:10]
[u'raining',
 u'belligerence',
 u'yellow',
 u'factory',
 u'four',
 u'Does',
 u'railing',
 u'ringlets',
 u'self-pity',
 u'attracted']

cfd['romance']['could']
193
```

## 绘制分布图和分布表
在plot()和tabulate()方法中，可以使用conditions=参数来指定显示哪些条件。如果忽略，所有条件都会显示出来。同样，可以使用sample=参数来限制要显示的样本。

例如为两种语言和长度少于10个字符的词汇绘制累计频率数据表。

```py
from nltk.corpus import udhr
languages = ['Chickasaw', 'English', 'German_Deutsch',
             'Greenlandic_Inuktikut', 'Hungarian_Magyar', 'Ibibio_Efik']
cfd = nltk.ConditionalFreqDist(
    (lang, len(word))
    for lang in languages
    for word in udhr.words(lang + '-Latin1'))
cfd.tabulate(conditions=['English', 'German_Deutsch'],
             samples=range(10), cumulative=True)

                  0    1    2    3    4    5    6    7    8    9 
       English    0  185  525  883  997 1166 1283 1440 1558 1638 
German_Deutsch    0  171  263  614  717  894 1013 1110 1213 1275 
```

## 使用Bigrams生成随机文本
bigrams()函数能接受一个词汇链表，并建立起一个连续的词对链表。

```py
sent = ['In', 'the', 'beginning', 'God', 'created', 'the', 'heaven',
        'and', 'the', 'earth', '.']
for pair in nltk.bigrams(sent):
    print pair
('In', 'the')
('the', 'beginning')
('beginning', 'God')
('God', 'created')
('created', 'the')
('the', 'heaven')
('heaven', 'and')
('and', 'the')
('the', 'earth')
('earth', '.')
```

产生随机文本：此程序获得了《创世纪》文本中所有的双连词，然后构造一个条件频率分布来记录哪些词汇最有可能会跟在给定词的后面。例如：living后面最可能的词是creature。generate_model()函数使用这些数据和种子词来产生随机文本。

```py
def generate_model(cfdist, word, num=15):
    for i in range(num):
        print word,
        word = cfdist[word].max()

text = nltk.corpus.genesis.words('english-kjv.txt')
bigrams = nltk.bigrams(text)
cfd = nltk.ConditionalFreqDist(bigrams)
cfd['living']
FreqDist({u',': 1,
          u'.': 1,
          u'creature': 7,
          u'soul': 1,
          u'substance': 2,
          u'thing': 4})

generate_model(cfd, 'living')
living creature that he said , and the land of the land of the land
```

Table 2-4. NLTK’s conditional frequency distributions: Commonly used methods and idioms for defining, accessing, and visualizing a conditional frequency distribution of counters

| Example | Description |
| ------- | ----------- |
| cfdist = ConditionalFreqDist(pairs) | Create a conditional frequency distribution from a list of pairs |
| cfdist.conditions() | Alphabetically sorted list of conditions |
| cfdist[condition] | The frequency distribution for this condition |
| cfdist[condition][sample] | Frequency for the given sample for this condition |
| cfdist.tabulate() | Tabulate the conditional frequency distribution |
| cfdist.tabulate(samples, conditions) | Tabulation limited to the specified samples and conditions |
| cfdist.plot() | Graphical plot of the conditional frequency distribution |
| cfdist.plot(samples, conditions) | Graphical plot limited to the specified samples and conditions |
| cfdist1 < cfdist2 | Test if samples in cfdist1 occur less frequently than in cfdist2 |\n"

# 词典资源
词典(Lexical)或词典资源是一个词和/或短语及其相关信息的集合，例如：词性(part-of-speech)和词意(sense)定义等相关信息。

图2-5中描述了词汇相关的标准术语。词项(lexical entry)包括词目(headword)（也叫词条(lemma)）及其他附加信息，例如：词性和词意定义。两个含义不同但拼写相同的分词被称为同音异义词(homonyms)。

![](pythonNLP8.png)

Figure 2-5. Lexicon terminology: Lexical entries for two lemmas having the same spelling (homonyms), providing part-of-speech and gloss information.

## 词汇列表语料库
过滤文本：此程序计算文本的词汇表，然后删除所有在现有的词汇列表中出现的元素，只留下罕见的或拼写错误的词汇。

```py
%matplotlib inline
import nltk

def unusual_words(text):
    text_vocab = set(w.lower() for w in text if w.isalpha())
    english_vocab = set(w.lower() for w in nltk.corpus.words.words())
    unusual = text_vocab.difference(english_vocab)
    return sorted(unusual)

unusual_words(nltk.corpus.gutenberg.words('austen-sense.txt'))[:30]
[u'abbeyland',
 u'abhorred',
 u'abilities',
 u'abounded',
 u'abridgement',
 u'abused',
 u'abuses',
 u'accents',
 u'accepting',
 u'accommodations',
 u'accompanied',
 u'accounted',
 u'accounts',
 u'accustomary',
 u'aches',
 u'acknowledging',
 u'acknowledgment',
 u'acknowledgments',
 u'acquaintances',
 u'acquiesced',
 u'acquitted',
 u'acquitting',
 u'acted',
 u'actions',
 u'adapted',
 u'adding',
 u'additions',
 u'addressed',
 u'addresses',
 u'addressing']

unusual_words(nltk.corpus.nps_chat.words())[:30]
[u'aaaaaaaaaaaaaaaaa',
 u'aaahhhh',
 u'abortions',
 u'abou',
 u'abourted',
 u'abs',
 u'ack',
 u'acros',
 u'actualy',
 u'adams',
 u'adds',
 u'adduser',
 u'adjusts',
 u'adoted',
 u'adreniline',
 u'ads',
 u'adults',
 u'afe',
 u'affairs',
 u'affari',
 u'affects',
 u'afk',
 u'agaibn',
 u'ages',
 u'aggravated',
 u'agurlwithbigguns',
 u'ahah',
 u'ahahah',
 u'ahahh',
 u'ahahha']
```

停用词(stopwords)语料库：

```py
from nltk.corpus import stopwords
stopwords.words('english')[:30]
[u'i',
 u'me',
 u'my',
 u'myself',
 u'we',
 u'our',
 u'ours',
 u'ourselves',
 u'you',
 u'your',
 u'yours',
 u'yourself',
 u'yourselves',
 u'he',
 u'him',
 u'his',
 u'himself',
 u'she',
 u'her',
 u'hers',
 u'herself',
 u'it',
 u'its',
 u'itself',
 u'they',
 u'them',
 u'their',
 u'theirs',
 u'themselves',
 u'what']
```

定义一个函数来计算文本中不包含在停用词表中的词所占的比例。

```py
from __future__ import division

def content_fraction(text):
    stopwords = nltk.corpus.stopwords.words('english')
    content = [w for w in text if w.lower() not in stopwords]
    return len(content) / len(text)
content_fraction(nltk.corpus.reuters.words())
0.735240435097661
```

在停用词的帮助下，筛选掉文本中三分之一的词。

词谜。检查必须出现的字母（2）和长度限制（1）（这里只查找6个或6个以上字母的词）。利用FreqDist比较法（3）检查候选词中的每个字母出现的频率是否小于或等于其相应在词谜中出现的频率。

```py
puzzle_letters = nltk.FreqDist('egivrvonl')
obligatory = 'r'
wordlist = nltk.corpus.words.words()
[w for w in wordlist if len(w) >= 6 #1
                        and obligatory in w #2
                        and nltk.FreqDist(w) <= puzzle_letters] #3
[u'glover',
 u'gorlin',
 u'govern',
 u'grovel',
 u'ignore',
 u'involver',
 u'lienor',
 u'linger',
 u'longer',
 u'lovering',
 u'noiler',
 u'overling',
 u'region',
 u'renvoi',
 u'revolving',
 u'ringle',
 u'roving',
 u'violer',
 u'virole']
```

![](pythonNLP9.png)

Figure 2-6. A word puzzle: A grid of randomly chosen letters with rules for creating words out of the letters; this puzzle is known as “Target.”

名字语料库。基于名字尾字母的男性/女性统计。

```py
names = nltk.corpus.names
names.fileids()
[u'female.txt', u'male.txt']

male_names = names.words('male.txt')
female_names = names.words('female.txt')
[w for w in male_names if w in female_names][:30cfd = nltk.ConditionalFreqDist()]
[u'Abbey',
 u'Abbie',
 u'Abby',
 u'Addie',
 u'Adrian',
 u'Adrien',
 u'Ajay',
 u'Alex',
 u'Alexis',
 u'Alfie',
 u'Ali',
 u'Alix',
 u'Allie',
 u'Allyn',
 u'Andie',
 u'Andrea',
 u'Andy',
 u'Angel',
 u'Angie',
 u'Ariel',
 u'Ashley',
 u'Aubrey',
 u'Augustine',
 u'Austin',
 u'Averil',
 u'Barrie',
 u'Barry',
 u'Beau',
 u'Bennie',
 u'Benny']

cfd = nltk.ConditionalFreqDist(
    (fileid, name[-1])
    for fileid in names.fileids()
    for name in names.words(fileid))
cfd.plot()
```

![](pythonNLP10.png)

Figure 2-7. Conditional frequency distribution: This plot shows the number of female and male names ending with each letter of the alphabet; most names ending with a, e, or i are female; names ending in h and l are equally likely to be male or female; names ending in k, o, r, s, and t are likely to be male.

## 发音的词典
美国英语的CMU发音词典。

```py
entries = nltk.corpus.cmudict.entries()
len(entries)
133737

for entry in entries[39943:39951]:
    print entry
(u'explorer', [u'IH0', u'K', u'S', u'P', u'L', u'AO1', u'R', u'ER0'])
(u'explorers', [u'IH0', u'K', u'S', u'P', u'L', u'AO1', u'R', u'ER0', u'Z'])
(u'explores', [u'IH0', u'K', u'S', u'P', u'L', u'AO1', u'R', u'Z'])
(u'exploring', [u'IH0', u'K', u'S', u'P', u'L', u'AO1', u'R', u'IH0', u'NG'])
(u'explosion', [u'IH0', u'K', u'S', u'P', u'L', u'OW1', u'ZH', u'AH0', u'N'])
(u'explosions', [u'IH0', u'K', u'S', u'P', u'L', u'OW1', u'ZH', u'AH0', u'N', u'Z'])
(u'explosive', [u'IH0', u'K', u'S', u'P', u'L', u'OW1', u'S', u'IH0', u'V'])
(u'explosively', [u'EH2', u'K', u'S', u'P', u'L', u'OW1', u'S', u'IH0', u'V', u'L', u'IY0'])
```

对任意一个词，词典资源都有语音的代码——不同的声音有着不同的标签——称作音素(phones)。

扫描词典中发音包含三个音素的条目。

```py
for word, pron in entries:
    if len(pron) == 3:
        ph1, ph2, ph3 = pron
        if ph1 == 'P' and ph3 == 'T':
            print word, ph2,
pait EY1 pat AE1 pate EY1 patt AE1 peart ER1 peat IY1 peet IY1 peete IY1 pert ER1 pet EH1 pete IY1 pett EH1 piet IY1 piette IY1 pit IH1 pitt IH1 pot AA1 pote OW1 pott AA1 pout AW1 puett UW1 purt ER1 put UH1 putt AH1
```

找到所有发音结尾与nicks相似的词汇。通过此方法也可以找到押韵的词。

```py
syllable = ['N', 'IH0', 'K', 'S']
[word for word, pron in entries if pron[-4:] == syllable]
[u"atlantic's",
 u'audiotronics',
 u'avionics',
 u'beatniks',
 u'calisthenics',
 u'centronics',
 u'chamonix',
 u'chetniks',
 u"clinic's",
 u'clinics',
 u'conics',
 u'conics',
 u'cryogenics',
 u'cynics',
 u'diasonics',
 u"dominic's",
 u'ebonics',
 u'electronics',
 u"electronics'",
 u"endotronics'",
 u'endotronics',
 u'enix',
 u'environics',
 u'ethnics',
 u'eugenics',
 u'fibronics',
 u'flextronics',
 u'harmonics',
 u'hispanics',
 u'histrionics',
 u'identics',
 u'ionics',
 u'kibbutzniks',
 u'lasersonics',
 u'lumonics',
 u'mannix',
 u'mechanics',
 u"mechanics'",
 u'microelectronics',
 u'minix',
 u'minnix',
 u'mnemonics',
 u'mnemonics',
 u'molonicks',
 u'mullenix',
 u'mullenix',
 u'mullinix',
 u'mulnix',
 u"munich's",
 u'nucleonics',
 u'onyx',
 u'organics',
 u"panic's",
 u'panics',
 u'penix',
 u'pennix',
 u'personics',
 u'phenix',
 u"philharmonic's",
 u'phoenix',
 u'phonics',
 u'photronics',
 u'pinnix',
 u'plantronics',
 u'pyrotechnics',
 u'refuseniks',
 u"resnick's",
 u'respironics',
 u'sconnix',
 u'siliconix',
 u'skolniks',
 u'sonics',
 u'sputniks',
 u'technics',
 u'tectonics',
 u'tektronix',
 u'telectronics',
 u'telephonics',
 u'tonics',
 u'unix',
 u"vinick's",
 u"vinnick's",
 u'vitronics']
```

音素包含数字表示主重音（1）、次重音（2）和无重音（0）。定义一个函数来提取重音数字，然后扫描词典，找到具有特定重音模式的词汇。

```py
def stress(pron):
    return [char for phone in pron for char in phone if char.isdigit()]

[w for w, pron in entries if stress(pron) == ['0', '1', '0', '2', '0']][:30]
[u'abbreviated',
 u'abbreviated',
 u'abbreviating',
 u'accelerated',
 u'accelerating',
 u'accelerator',
 u'accelerators',
 u'accentuated',
 u'accentuating',
 u'accommodated',
 u'accommodating',
 u'accommodative',
 u'accumulated',
 u'accumulating',
 u'accumulative',
 u'accumulator',
 u'accumulators',
 u'accusatory',
 u'adenovirus',
 u'adjudicated',
 u'adjudicating',
 u'administrating',
 u'administrative',
 u'administrator',
 u"administrators'",
 u"administrator's",
 u'administrators',
 u'adulterated',
 u'adventurism',
 u'adventurism']
```

## 比较词表
表格词典的另外一个例子是comparative wordlist。NLTK中包含了所谓的Swadesh wordlists，包括几种语言的约200个常用词的列表。

```py
from nltk.corpus import swadesh
swadesh.fileids()
[u'be',
 u'bg',
 u'bs',
 u'ca',
 u'cs',
 u'cu',
 u'de',
 u'en',
 u'es',
 u'fr',
 u'hr',
 u'it',
 u'la',
 u'mk',
 u'nl',
 u'pl',
 u'pt',
 u'ro',
 u'ru',
 u'sk',
 u'sl',
 u'sr',
 u'sw',
 u'uk']

swadesh.words('en')[:30]
[u'I',
 u'you (singular), thou',
 u'he',
 u'we',
 u'you (plural)',
 u'they',
 u'this',
 u'that',
 u'here',
 u'there',
 u'who',
 u'what',
 u'where',
 u'when',
 u'how',
 u'not',
 u'all',
 u'many',
 u'some',
 u'few',
 u'other',
 u'one',
 u'two',
 u'three',
 u'four',
 u'five',
 u'big',
 u'long',
 u'wide',
 u'thick']

fr2en = swadesh.entries(['fr', 'en'])
fr2en[:30]
[(u'je', u'I'),
 (u'tu, vous', u'you (singular), thou'),
 (u'il', u'he'),
 (u'nous', u'we'),
 (u'vous', u'you (plural)'),
 (u'ils, elles', u'they'),
 (u'ceci', u'this'),
 (u'cela', u'that'),
 (u'ici', u'here'),
 (u'l\xe0', u'there'),
 (u'qui', u'who'),
 (u'quoi', u'what'),
 (u'o\xf9', u'where'),
 (u'quand', u'when'),
 (u'comment', u'how'),
 (u'ne...pas', u'not'),
 (u'tout', u'all'),
 (u'plusieurs', u'many'),
 (u'quelques', u'some'),
 (u'peu', u'few'),
 (u'autre', u'other'),
 (u'un', u'one'),
 (u'deux', u'two'),
 (u'trois', u'three'),
 (u'quatre', u'four'),
 (u'cinq', u'five'),
 (u'grand', u'big'),
 (u'long', u'long'),
 (u'large', u'wide'),
 (u'\xe9pais', u'thick')]

translate = dict(fr2en)
translate['chien']
u'dog'

translate['jeter']
u'throw'

de2en = swadesh.entries(['de', 'en'])    # German-English
es2en = swadesh.entries(['es', 'en'])    # Spanish-English
translate.update(dict(de2en))
translate.update(dict(es2en))
translate['Hund']
u'dog'

translate['perro']
u'dog'
```

比较德语族和拉丁语族的不同。

```py
languages = ['en', 'de', 'nl', 'es', 'fr', 'pt', 'la']
for i in [139, 140, 141, 142]:
    print swadesh.entries(languages)[i]
(u'say', u'sagen', u'zeggen', u'decir', u'dire', u'dizer', u'dicere')
(u'sing', u'singen', u'zingen', u'cantar', u'chanter', u'cantar', u'canere')
(u'play', u'spielen', u'spelen', u'jugar', u'jouer', u'jogar, brincar', u'ludere')
(u'float', u'schweben', u'zweven', u'flotar', u'flotter', u'flutuar, boiar', u'fluctuare')
```

## 词汇工具：Toolbox
目前最流行的语言学家用来管理数据的工具是Toolbox。Toolbox文件由一些条目的集合组成，其中每个条目由一个或多个字段组成。

下面是Rotokas语的词典。只看第一个条目，词kaa，意思是“窒息”。

```py
from nltk.corpus import toolbox
toolbox.entries('rotokas.dic')[1][:30]
(u'kaa',
 [(u'ps', u'V'),
  (u'pt', u'B'),
  (u'ge', u'strangle'),
  (u'tkp', u'pasim nek'),
  (u'arg', u'O'),
  (u'vx', u'2'),
  (u'dt', u'07/Oct/2006'),
  (u'ex', u'Rera rauroro rera kaarevoi.'),
  (u'xp', u'Em i holim pas em na nekim em.'),
  (u'xe', u'He is holding him and strangling him.'),
  (u'ex', u'Iroiro-ia oirato okoearo kaaivoi uvare rirovira kaureoparoveira.'),
  (u'xp', u'Ol i pasim nek bilong man long rop bikos em i save bikhet tumas.'),
  (u'xe',
   u"They strangled the man's neck with rope because he was very stubborn and arrogant."),
  (u'ex',
   u'Oirato okoearo kaaivoi iroiro-ia. Uva viapau uvuiparoi ra vovouparo uva kopiiroi.'),
  (u'xp',
   u'Ol i pasim nek bilong man long rop. Olsem na em i no pulim win olsem na em i dai.'),
  (u'xe',
   u"They strangled the man's neck with a rope. And he couldn't breathe and he died.")])
```

条目包括一系列“属性-值”对，如('ps', 'V')，表示词性是'V'（动词），('ge', 'gag')表示英文注释是'gag'。

## WordNet
WordNet是面向语义的英语词典。

汉语开放词网:[Chinese Open WordNet](http://openkg.cn/dataset/wordnet)

- OpenKG收集和整理国内国外重要的开放知识库和知识图谱项目，并组织整理相关的中文资料免费对外开放。
- 汉语开放词网是受 Princeton WordNet 和 Global WordNet Grid 启发由 NTU Computational Linguistics Lab 构建的，含有42315 synsets，79812 senses， 61536 unique words

### 意义与同义词
```
Benz is credited with the invention of the motorcar.
Benz is credited with the invention of the automobile.
```

motorcar和automobile是synonyms。

```py
from nltk.corpus import wordnet as wn
wn.synsets('motorcar')
[Synset('car.n.01')]
```

motorcar只有一个可能的含义，它被定义为car.n.01，car的第一个名词意义car.n.01被称为synset或"synonym set"，即意义相同的词（或“词条”）的集合。

```py
wn.synset('car.n.01').lemma_names()
[u'car', u'auto', u'automobile', u'machine', u'motorcar']
```

同义词集也有一些一般的定义和例句。

```py
wn.synset('car.n.01').definition()
u'a motor vehicle with four wheels; usually propelled by an internal combustion engine'

wn.synset('car.n.01').examples()
[u'he needs a car to get to work']
```

为了消除同义词集歧义，将这些词标注为car.n.01.automobile、car.n.01.motocar等。这种同义词集和词的配对叫做lemma。可以得到指定同义词集的所有lemma（1），查找特定的lemma（2），得到一个词条所对应的同义词集（3），也可以得到一个词条的“名字”（4）。

```py
wn.synset('car.n.01').lemmas() #1
[Lemma('car.n.01.car'),
 Lemma('car.n.01.auto'),
 Lemma('car.n.01.automobile'),
 Lemma('car.n.01.machine'),
 Lemma('car.n.01.motorcar')]

wn.lemma('car.n.01.automobile') #2
Lemma('car.n.01.automobile')

wn.lemma('car.n.01.automobile').synset() #3
Synset('car.n.01')

wn.lemma('car.n.01.automobile').name() #4
u'automobile'
```

词car共有5个同义词集。

```py
wn.synsets('car')
[Synset('car.n.01'),
 Synset('car.n.02'),
 Synset('car.n.03'),
 Synset('car.n.04'),
 Synset('cable_car.n.01')]

for synset in wn.synsets('car'):
    print synset.lemma_names()
[u'car', u'auto', u'automobile', u'machine', u'motorcar']
[u'car', u'railcar', u'railway_car', u'railroad_car']
[u'car', u'gondola']
[u'car', u'elevator_car']
[u'cable_car', u'car']
```

访问所有包含词car的lemmas：

```py
wn.lemmas('car')
[Lemma('car.n.01.car'),
 Lemma('car.n.02.car'),
 Lemma('car.n.03.car'),
 Lemma('car.n.04.car'),
 Lemma('cable_car.n.01.car')]
```

### WordNet的层次结构¶
一些概念综合性很强，如实体、状态、事件：这些被称为unique beginners。

![](pythonNLP11.png)

Figure 2-8. Fragment of WordNet concept hierarchy: Nodes correspond to synsets; edges indicate the hypernym/hyponym relation, i.e., the relation between superordinate and subordinate concepts.

WordNet使我们能容易驾驭各种概念。例如：motorcar，可以看到更加具体（直接）的概念——hyponyms。

```py
motorcar = wn.synset('car.n.01')
types_of_motorcar = motorcar.hyponyms()
types_of_motorcar[26]
Synset('stanley_steamer.n.01')

sorted([lemma.name() for synset in types_of_motorcar for lemma in synset.lemmas()])
[u'Model_T',
 u'S.U.V.',
 u'SUV',
 u'Stanley_Steamer',
 u'ambulance',
 u'beach_waggon',
 u'beach_wagon',
 u'bus',
 u'cab',
 u'compact',
 u'compact_car',
 u'convertible',
 u'coupe',
 u'cruiser',
 u'electric',
 u'electric_automobile',
 u'electric_car',
 u'estate_car',
 u'gas_guzzler',
 u'hack',
 u'hardtop',
 u'hatchback',
 u'heap',
 u'horseless_carriage',
 u'hot-rod',
 u'hot_rod',
 u'jalopy',
 u'jeep',
 u'landrover',
 u'limo',
 u'limousine',
 u'loaner',
 u'minicar',
 u'minivan',
 u'pace_car',
 u'patrol_car',
 u'phaeton',
 u'police_car',
 u'police_cruiser',
 u'prowl_car',
 u'race_car',
 u'racer',
 u'racing_car',
 u'roadster',
 u'runabout',
 u'saloon',
 u'secondhand_car',
 u'sedan',
 u'sport_car',
 u'sport_utility',
 u'sport_utility_vehicle',
 u'sports_car',
 u'squad_car',
 u'station_waggon',
 u'station_wagon',
 u'stock_car',
 u'subcompact',
 u'subcompact_car',
 u'taxi',
 u'taxicab',
 u'tourer',
 u'touring_car',
 u'two-seater',
 u'used-car',
 u'waggon',
 u'wagon']
```

通过访问hypernyms来操纵层次结构。

```py
motorcar.hypernyms()
[Synset('motor_vehicle.n.01')]

paths = motorcar.hypernym_paths()
len(paths)
2

[synset.name() for synset in paths[0]]
[u'entity.n.01',
 u'physical_entity.n.01',
 u'object.n.01',
 u'whole.n.02',
 u'artifact.n.01',
 u'instrumentality.n.03',
 u'container.n.01',
 u'wheeled_vehicle.n.01',
 u'self-propelled_vehicle.n.01',
 u'motor_vehicle.n.01',
 u'car.n.01']

[synset.name() for synset in paths[1]]
[u'entity.n.01',
 u'physical_entity.n.01',
 u'object.n.01',
 u'whole.n.02',
 u'artifact.n.01',
 u'instrumentality.n.03',
 u'conveyance.n.03',
 u'vehicle.n.01',
 u'wheeled_vehicle.n.01',
 u'self-propelled_vehicle.n.01',
 u'motor_vehicle.n.01',
 u'car.n.01']
```

得到一个最笼统的hypernyms同义词集。

```py
motorcar.root_hypernyms()
[Synset('entity.n.01')]
```

### 更多的词汇关系
Hypernyms 和 hyponyms 被称为词汇关系(lexical relations)。这两者的关系为上下定位“is-a”层次。一棵树可以分成树干、树冠等部分，这些都是part_meronyms()。一棵树的实质是由心材和边材组成的，即substance_meronyms()。树木的集合形成了一个森林，即member_holonyms()。

```py
wn.synset('tree.n.01').part_meronyms()
[Synset('burl.n.02'),
 Synset('crown.n.07'),
 Synset('limb.n.02'),
 Synset('stump.n.01'),
 Synset('trunk.n.01')]

wn.synset('tree.n.01').substance_meronyms()
[Synset('heartwood.n.01'), Synset('sapwood.n.01')]

wn.synset('tree.n.01').member_holonyms()
[Synset('forest.n.01')]
```

mint.n.04是mint.n.02的一部分，同时也是组成mint.n.05的材料。

```py
for synset in wn.synsets('mint', wn.NOUN):
    print synset.name() + ':', synset.definition()
batch.n.02: (often followed by `of') a large number or amount or extent
mint.n.02: any north temperate plant of the genus Mentha with aromatic leaves and small mauve flowers
mint.n.03: any member of the mint family of plants
mint.n.04: the leaves of a mint plant used fresh or candied
mint.n.05: a candy that is flavored with a mint oil
mint.n.06: a plant where money is coined by authority of the government

wn.synset('mint.n.04').part_holonyms()
[Synset('mint.n.02')]

wn.synset('mint.n.04').substance_holonyms()
[Synset('mint.n.05')]
```

走路蕴含(entails)着抬脚。

```py
wn.synset('walk.v.01').entailments()
[Synset('step.v.01')]

wn.synset('eat.v.01').entailments()
[Synset('chew.v.01'), Synset('swallow.v.01')]

wn.synset('tease.v.03').entailments()
[Synset('arouse.v.07'), Synset('disappoint.v.01')]
```

词条之间反义词(antonymy)关系。

```py
wn.lemma('supply.n.02.supply').antonyms()
[Lemma('demand.n.02.demand')]

wn.lemma('rush.v.01.rush').antonyms()
[Lemma('linger.v.04.linger')]

wn.lemma('horizontal.a.01.horizontal').antonyms()
[Lemma('inclined.a.02.inclined'), Lemma('vertical.a.01.vertical')]

wn.lemma('staccato.r.01.staccato').antonyms()
[Lemma('legato.r.01.legato')]
```

### 语义相似度
如果两个同义词集共用一个特定的hypernym——在hypernym层次结构中处于较低层——它们一定有密切的联系。

```py
right = wn.synset('right_whale.n.01')
orca = wn.synset('orca.n.01')
minke = wn.synset('minke_whale.n.01')
tortoise = wn.synset('tortoise.n.01')
novel = wn.synset('novel.n.01')
right.lowest_common_hypernyms(minke)
[Synset('baleen_whale.n.01')]

right.lowest_common_hypernyms(orca)
[Synset('whale.n.02')]

right.lowest_common_hypernyms(tortoise)
[Synset('vertebrate.n.01')]

right.lowest_common_hypernyms(novel)
[Synset('entity.n.01')]
```

鲸鱼是非常具体的（须鲸更是如此），脊椎动物是更具一般化，而实体完全是抽象的。可以通过查找每个同义词集的深度来量化这个普遍性概念。

```py
wn.synset('baleen_whale.n.01').min_depth()
14

wn.synset('whale.n.02').min_depth()
13

wn.synset('vertebrate.n.01').min_depth()
8

wn.synset('entity.n.01').min_depth()
0
```

path_similarity基于hypernym层次结构概念中相互关联的最短路径下，在0~1范围内的相似度（两者之间没有路径返回-1）。同义词集与自身比较将返回1。

```py
right.path_similarity(minke)
0.25

right.path_similarity(orca)
0.16666666666666666

right.path_similarity(tortoise)
0.07692307692307693

right.path_similarity(novel)
0.043478260869565216
```




















































































































































