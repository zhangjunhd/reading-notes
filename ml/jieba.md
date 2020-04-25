# 结巴中文分词
https://github.com/fxsjy/jieba

- [结巴中文分词](#%e7%bb%93%e5%b7%b4%e4%b8%ad%e6%96%87%e5%88%86%e8%af%8d)
  - [1.分词](#1%e5%88%86%e8%af%8d)

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
```

输出：

```
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








