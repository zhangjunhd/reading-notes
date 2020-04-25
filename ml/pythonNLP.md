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



























