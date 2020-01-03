![cover](https://img9.doubanio.com/view/subject/l/public/s3086205.jpg)

    作者: Ｇrigoris Antoniou
    副标题: 语义网基础教程
    译者: 陈小平
    出版年: 2008-4
    页数: 184
    定价: 32.00元
    丛书: 计算机科学丛书
    ISBN: 9787111237341

[豆瓣链接](https://book.douban.com/subject/3061966/)

- [第3章 用RDF描述网络资源](#%e7%ac%ac3%e7%ab%a0-%e7%94%a8rdf%e6%8f%8f%e8%bf%b0%e7%bd%91%e7%bb%9c%e8%b5%84%e6%ba%90)
  - [RDF的基本思路](#rdf%e7%9a%84%e5%9f%ba%e6%9c%ac%e6%80%9d%e8%b7%af)
  - [RDF schema语言](#rdf-schema%e8%af%ad%e8%a8%80)
- [第4章 网络本体语言OWL](#%e7%ac%ac4%e7%ab%a0-%e7%bd%91%e7%bb%9c%e6%9c%ac%e4%bd%93%e8%af%ad%e8%a8%80owl)
  - [本体知识推理](#%e6%9c%ac%e4%bd%93%e7%9f%a5%e8%af%86%e6%8e%a8%e7%90%86)
  - [RDF schema局限性](#rdf-schema%e5%b1%80%e9%99%90%e6%80%a7)
  - [OWL语言](#owl%e8%af%ad%e8%a8%80)

# 第3章 用RDF描述网络资源
* RDF（Resource Description Framework），由一系列陈述（statement）即“对象-属性-值”三元组组成。p47
* RDF schema则定义RDF数据模型所使用的词汇（vocabulary）。RDFS可以定义词汇，规定什么属性可以作用于什么类型的对象，属性可以取什么值，也可以描述对象之间的关系。p48

## RDF的基本思路
* 资源：将资源视为一个对象，也就是打算谈论的“事物”。每个资源都有一个通用资源标识符URI。p49
* 属性：是一类特殊的资源，描述资源之间的关系，仍用URI标识。
* 陈述：一个陈述是一个“对象-属性-值”三元组，有一个资源、一个属性和一个值组成。值可以是资源，也可以是文字（literal）。文字是原子值（字符串）。

## RDF schema语言
核心类 p66
* rdfs:Resource 所有资源类的类
* rdfs:Class 所有类的类
* rdfs:Literal 所有文字的类
* rdf:Property 所有属性的类
* rdf:Statement 所有具体陈述的类

用于定义关系的核心属性 p66
* rdf:type 把一个资源和它所属的类联系起来
* rdfs:subClassOf 把一个类和它的父亲联系起来
* rdfs:subPropertyOf 把一个属性和它的一个父属性联系起来

用于约束属性的核心属性 p67
* rdfs:domain 限定属性P的定义域，即规定在谓词P的三元组中以主语身份出现的资源所属的类
* rdfs:range 限定属性P的值域，即规定在谓词P的三元组中以值的身份出现的那些资源所属的类

# 第4章 网络本体语言OWL
## 本体知识推理
p86
1. 类属关系
2. 类等价
3. 相容
4. 分类

## RDF schema局限性
p86
1. 属性的局部辖域
2. 类不相交性
3. 类的布尔组合
4. 基数约束
5. 属性的特殊性质

## OWL语言
* 类元素 p90
  * owl:Class
  * owl:disjoinWith 描述类不相交性
  * owl:equivalentClass
  * owl:Thing/owl:Nothing
* 属性元素 p90
  * 对象属性，将对象相互关联
  * 数据类型属性，将对象与数据类型值想关联
  * owl:inverseOf 逆属性
  * owl:equivalentProperty 属性等价
* 属性约束 p92
  * owl:Restriction
  * owl:allValuesFrom/owl:someValuesFrom
  * owl:onProperty
  * owl:hasValue
* 特殊性质 p94
  * owl:TransitiveProperty
  * owl:SymmetricProperty
  * owl:FunctionProperty
  * owl:InverseFunctionProperty
* 布尔组合 p95
  * owl:complementOf
  * owl:unionOf
  * owl:intersectionOf
* 枚举 p96
  * owl:oneOf