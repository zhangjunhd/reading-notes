# 结巴中文分词
https://github.com/fxsjy/jieba

- [结巴中文分词](#%e7%bb%93%e5%b7%b4%e4%b8%ad%e6%96%87%e5%88%86%e8%af%8d)
  - [1.分词](#1%e5%88%86%e8%af%8d)
  - [2.添加自定义词典](#2%e6%b7%bb%e5%8a%a0%e8%87%aa%e5%ae%9a%e4%b9%89%e8%af%8d%e5%85%b8)
    - [2.1 载入词典](#21-%e8%bd%bd%e5%85%a5%e8%af%8d%e5%85%b8)
    - [2.2 调整词典](#22-%e8%b0%83%e6%95%b4%e8%af%8d%e5%85%b8)

## 1.分词
1. `jieba.cut`方法接受三个输入参数: 需要分词的字符串；`cut_all`参数用来控制是否采用全模式；`HMM`参数用来控制是否使用 HMM 模型
2. `jieba.cut_for_search`方法接受两个参数：需要分词的字符串；是否使用 HMM 模型。该方法适合用于搜索引擎构建倒排索引的分词，粒度比较细
3. 待分词的字符串可以是 unicode 或 UTF-8 字符串、GBK 字符串。注意：不建议直接输入 GBK 字符串，可能无法预料地错误解码成 UTF-8
4. `jieba.cut`以及`jieba.cut_for_search`返回的结构都是一个可迭代的 generator，可以使用 for 循环来获得分词后得到的每一个词语(unicode)，或者用
5. `jieba.lcut`以及`jieba.lcut_for_search`直接返回 list
6. `jieba.Tokenizer(dictionary=DEFAULT_DICT)`新建自定义分词器，可用于同时使用不同词典。`jieba.dt`为默认分词器，所有全局分词相关函数都是该分词器的映射。

```py
# encoding=utf-8
from __future__ import print_function, unicode_literals
import jieba

seg_list = jieba.cut("我来到北京清华大学", cut_all=True, HMM=False)
print("Full Mode(HMM=False): " + "/ ".join(seg_list))

seg_list = jieba.cut("我来到北京清华大学", cut_all=True, HMM=True)
print("Full Mode(HMM=True): " + "/ ".join(seg_list))

seg_list = jieba.cut("我来到北京清华大学", cut_all=False)
print("Default Mode: " + "/ ".join(seg_list))  # 精确模式

seg_list = jieba.cut("他来到了网易杭研大厦")  # 默认是精确模式
print("Default Mode: " + ", ".join(seg_list))

seg_list = jieba.cut_for_search("小明硕士毕业于中国科学院计算所，后在日本京都大学深造")  # 搜索引擎模式
print("Search Engine Mode: " + ", ".join(seg_list))

Building prefix dict from the default dictionary ...
Loading model from cache /var/folders/pb/0wpsfs4x5cq3l5jrspxp9v4r0000gn/T/jieba.cache
Loading model cost 0.469 seconds.
Prefix dict has been built succesfully.

Full Mode(HMM=False): 我/ 来到/ 北京/ 清华/ 清华大学/ 华大/ 大学
Full Mode(HMM=True): 我/ 来到/ 北京/ 清华/ 清华大学/ 华大/ 大学
Default Mode: 我/ 来到/ 北京/ 清华大学
Default Mode: 他, 来到, 了, 网易, 杭研, 大厦
Search Engine Mode: 小明, 硕士, 毕业, 于, 中国, 科学, 学院, 科学院, 中国科学院, 计算, 计算所, ，, 后, 在, 日本, 京都, 大学, 日本京都大学, 深造
```

## 2.添加自定义词典
### 2.1 载入词典
- 开发者可以指定自己自定义的词典，以便包含 jieba 词库里没有的词。虽然 jieba 有新词识别能力，但是自行添加新词可以保证更高的正确率
- 用法： `jieba.load_userdict(file_name)` # file_name 为文件类对象或自定义词典的路径
- 词典格式和 dict.txt 一样，一个词占一行；每一行分三部分：词语、词频（可省略）、词性（可省略），用空格隔开，顺序不可颠倒。file_name 若为路径或二进制方式打开的文件，则文件必须为 UTF-8 编码。
- 词频省略时使用自动计算的能保证分出该词的词频。

例如：

```
创新办 3 i
云计算 5
凱特琳 nz
台中
```

### 2.2 调整词典
- 使用 `add_word(word, freq=None, tag=None)`和`del_word(word)`可在程序中动态修改词典。
- 使用`suggest_freq(segment, tune=True)`可调节单个词语的词频，使其能（或不能）被分出来。

注意：自动计算的词频在使用 HMM 新词发现功能时可能无效。

使用默认分词，“创新办”、“云计算”、“八一双鹿”、“韩玉赏鉴”、“凱特琳”是分错的：

```py
test_sent = (
"李小福是创新办主任也是云计算方面的专家; 什么是八一双鹿\n"
"例如我输入一个带“韩玉赏鉴”的标题，在自定义词库中也增加了此词为N类\n"
"「台中」正確應該不會被切開。mac上可分出「石墨烯」；此時又可以分出來凱特琳了。"
)

words = jieba.cut(test_sent)
print('/'.join(words))

李小福/是/创新/办/主任/也/是/云/计算/方面/的/专家/;/ /什么/是/八/一双/鹿/
/例如/我/输入/一个/带/“/韩玉/赏鉴/”/的/标题/，/在/自定义词/库中/也/增加/了/此/词为/N/类/
/「/台/中/」/正確/應該/不會/被/切開/。/mac/上/可/分出/「/石墨/烯/」/；/此時/又/可以/分出/來凱/特琳/了/。
```

加入“凱特琳”后：

```py
jieba.add_word('凱特琳')  
words = jieba.cut(test_sent)
print('/'.join(words))

李小福/是/创新/办/主任/也/是/云/计算/方面/的/专家/;/ /什么/是/八/一双/鹿/
/例如/我/输入/一个/带/“/韩玉/赏鉴/”/的/标题/，/在/自定义词/库中/也/增加/了/此/词为/N/类/
/「/台/中/」/正確/應該/不會/被/切開/。/mac/上/可/分出/「/石墨/烯/」/；/此時/又/可以/分出/來/凱特琳/了/。
```

删除“凱特琳”后：

```py
jieba.del_word('凱特琳')
words = jieba.cut(test_sent)
print('/'.join(words))

李小福/是/创新/办/主任/也/是/云/计算/方面/的/专家/;/ /什么/是/八/一双/鹿/
/例如/我/输入/一个/带/“/韩玉/赏鉴/”/的/标题/，/在/自定义词/库中/也/增加/了/此/词为/N/类/
/「/台/中/」/正確/應該/不會/被/切開/。/mac/上/可/分出/「/石墨/烯/」/；/此時/又/可以/分出/來/凱特琳/了/。
```

加入“石墨烯”后：

```py
jieba.add_word('石墨烯')
words = jieba.cut(test_sent)
print('/'.join(words))

李小福/是/创新/办/主任/也/是/云/计算/方面/的/专家/;/ /什么/是/八/一双/鹿/
/例如/我/输入/一个/带/“/韩玉/赏鉴/”/的/标题/，/在/自定义词/库中/也/增加/了/此/词为/N/类/
/「/台/中/」/正確/應該/不會/被/切開/。/mac/上/可/分出/「/石墨烯/」/；/此時/又/可以/分出/來/凱特琳/了/。
```

载入词典：

```bsh
!cat userdict.txt

云计算 5
李小福 2 nr
创新办 3 i
easy_install 3 eng
好用 300
韩玉赏鉴 3 nz
八一双鹿 3 nz
台中
凱特琳 nz
Edu Trust认证 2000
```

```py
jieba.load_userdict("userdict.txt")
words = jieba.cut(test_sent)
print('/'.join(words))

李小福/是/创新办/主任/也/是/云计算/方面/的/专家/;/ /什么/是/八一双鹿/
/例如/我/输入/一个/带/“/韩玉赏鉴/”/的/标题/，/在/自定义词/库中/也/增加/了/此/词为/N/类/
/「/台中/」/正確/應該/不會/被/切開/。/mac/上/可/分出/「/石墨烯/」/；/此時/又/可以/分出/來/凱特琳/了/。
```

调节单个词语的词频:

```py
print('/'.join(jieba.cut('如果放到post中将出错。', HMM=False)))

如果/放到/post/中将/出错/。
```





