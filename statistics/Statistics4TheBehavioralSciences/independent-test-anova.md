- [平均数差异推论-双因素方差分析（独立测量）](#%e5%b9%b3%e5%9d%87%e6%95%b0%e5%b7%ae%e5%bc%82%e6%8e%a8%e8%ae%ba-%e5%8f%8c%e5%9b%a0%e7%b4%a0%e6%96%b9%e5%b7%ae%e5%88%86%e6%9e%90%e7%8b%ac%e7%ab%8b%e6%b5%8b%e9%87%8f)
  - [概述](#%e6%a6%82%e8%bf%b0)
  - [主效应与交互作用](#%e4%b8%bb%e6%95%88%e5%ba%94%e4%b8%8e%e4%ba%a4%e4%ba%92%e4%bd%9c%e7%94%a8)
    - [主效应](#%e4%b8%bb%e6%95%88%e5%ba%94)
    - [交互作用](#%e4%ba%a4%e4%ba%92%e4%bd%9c%e7%94%a8)
  - [符号与公式](#%e7%ac%a6%e5%8f%b7%e4%b8%8e%e5%85%ac%e5%bc%8f)
    - [测量双因素ANOVA的效应大小](#%e6%b5%8b%e9%87%8f%e5%8f%8c%e5%9b%a0%e7%b4%a0anova%e7%9a%84%e6%95%88%e5%ba%94%e5%a4%a7%e5%b0%8f)
  - [解释双因素ANOVA的结果](#%e8%a7%a3%e9%87%8a%e5%8f%8c%e5%9b%a0%e7%b4%a0anova%e7%9a%84%e7%bb%93%e6%9e%9c)
  - [双因素ANOVA的假设](#%e5%8f%8c%e5%9b%a0%e7%b4%a0anova%e7%9a%84%e5%81%87%e8%ae%be)

## 平均数差异推论-双因素方差分析（独立测量）
### 概述
![](independent-test-anova1.png)
![](independent-test-anova2.png)

### 主效应与交互作用
#### 主效应
![](independent-test-anova3.png)

一个因素的不同水平之间的平均数差异被称为这个因素的`主效应`。当研究的设计被表现为一个矩阵时，一个因素决定行，另一个因素决定列。那么行与行之间的平均数差异描述了一个因素的主效应。列与列之间的平均数差异描述了另一个因素的主效应。

对于我们讨论的这个例子，因素A包括两个不同的湿度水平的比较。虚无假设将陈述在两个水平之间没有差异；也就是说，湿度没有影响成绩。用符号表示：

$H_0:\mu_{A_1}=\mu_{A_2}$

备择假设是湿度的两个不同水平产生了不同的效应：

$H_0:\mu_{A_1} \ne \mu_{A_2}$

为了评估这些假设，我们将计算比较了两个湿度水平之间的实际平均数差异与期望出现的随机性或样本误差的F分数。

    F=因素A的平均数之间的方差（差异） / 期望的随机/误差方差（差异）

    F=行的平均数之间的方差（差异） / 期望的随机/误差方差（差异）

同样，因素B包括三种不同的温度条件的比较。虚无假设陈述了三种温度的平均数之间没有差异。用符号表示：

$H_0:\mu_{B_1}=\mu_{B_2}=\mu_{B_3}$

同样，备择假设陈述了存在差异：

H1：至少有一个平均数与其他的不同。

F分数将比较得到的三种温度条件之间平均数差异与期望的随机性导致的差异。

    F=因素B的平均数之间的方差（差异） / 期望的随机/误差方差（差异）

    F=列的平均数之间的方差（差异） / 期望的随机/误差方差（差异）

#### 交互作用
两个因素间的`交互作用`发生在单个处理条件的平均数差异与总的因素的主效应不同时，当一个因素的效应依赖于另一个因素的不同水平时，那么在因素间存在交互作用。

![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/61749979.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/59912277.jpg)

### 符号与公式
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/82253523.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/34803537.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/51256692.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/43590767.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/50218441.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/33504203.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/62828269.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/97063635.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/31321201.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/38808241.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/80648912.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/10740208.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/9741269.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/6809923.jpg)

#### 测量双因素ANOVA的效应大小
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/92788548.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/82994368.jpg)

### 解释双因素ANOVA的结果
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/54307783.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/88983427.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/81408493.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/49018531.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/27174838.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/26209496.jpg)
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/5979772.jpg)

### 双因素ANOVA的假设
![](http://ou8qjsj0m.bkt.clouddn.com//17-10-26/43975703.jpg)