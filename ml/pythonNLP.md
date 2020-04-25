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
































































































































































