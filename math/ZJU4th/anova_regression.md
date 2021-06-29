- [第九章 方差分析及回归分析](#%e7%ac%ac%e4%b9%9d%e7%ab%a0-%e6%96%b9%e5%b7%ae%e5%88%86%e6%9e%90%e5%8f%8a%e5%9b%9e%e5%bd%92%e5%88%86%e6%9e%90)
  - [1 单因素试验的方差分析](#1-%e5%8d%95%e5%9b%a0%e7%b4%a0%e8%af%95%e9%aa%8c%e7%9a%84%e6%96%b9%e5%b7%ae%e5%88%86%e6%9e%90)
    - [（一）单因素试验](#%e4%b8%80%e5%8d%95%e5%9b%a0%e7%b4%a0%e8%af%95%e9%aa%8c)
    - [（二）平方和的分解](#%e4%ba%8c%e5%b9%b3%e6%96%b9%e5%92%8c%e7%9a%84%e5%88%86%e8%a7%a3)
    - [（三）SE，SA的统计特性](#%e4%b8%89sesa%e7%9a%84%e7%bb%9f%e8%ae%a1%e7%89%b9%e6%80%a7)
    - [（四）假设检验问题的拒绝域](#%e5%9b%9b%e5%81%87%e8%ae%be%e6%a3%80%e9%aa%8c%e9%97%ae%e9%a2%98%e7%9a%84%e6%8b%92%e7%bb%9d%e5%9f%9f)
    - [（五）未知参数估计](#%e4%ba%94%e6%9c%aa%e7%9f%a5%e5%8f%82%e6%95%b0%e4%bc%b0%e8%ae%a1)
  - [2 双因素方差分析表](#2-%e5%8f%8c%e5%9b%a0%e7%b4%a0%e6%96%b9%e5%b7%ae%e5%88%86%e6%9e%90%e8%a1%a8)
    - [（一）双因素等重复试验的方差分析](#%e4%b8%80%e5%8f%8c%e5%9b%a0%e7%b4%a0%e7%ad%89%e9%87%8d%e5%a4%8d%e8%af%95%e9%aa%8c%e7%9a%84%e6%96%b9%e5%b7%ae%e5%88%86%e6%9e%90)
    - [（二）双因素无重复试验的方差分析](#%e4%ba%8c%e5%8f%8c%e5%9b%a0%e7%b4%a0%e6%97%a0%e9%87%8d%e5%a4%8d%e8%af%95%e9%aa%8c%e7%9a%84%e6%96%b9%e5%b7%ae%e5%88%86%e6%9e%90)
  - [3 一元线性回归](#3-%e4%b8%80%e5%85%83%e7%ba%bf%e6%80%a7%e5%9b%9e%e5%bd%92)
    - [（一）一元线性回归](#%e4%b8%80%e4%b8%80%e5%85%83%e7%ba%bf%e6%80%a7%e5%9b%9e%e5%bd%92)
    - [（二）a，b的估计](#%e4%ba%8cab%e7%9a%84%e4%bc%b0%e8%ae%a1)
    - [（三）σ2的估计](#%e4%b8%89%cf%832%e7%9a%84%e4%bc%b0%e8%ae%a1)
    - [（四）线性假设的显著性检验](#%e5%9b%9b%e7%ba%bf%e6%80%a7%e5%81%87%e8%ae%be%e7%9a%84%e6%98%be%e8%91%97%e6%80%a7%e6%a3%80%e9%aa%8c)
    - [（五）系数b的置信区间](#%e4%ba%94%e7%b3%bb%e6%95%b0b%e7%9a%84%e7%bd%ae%e4%bf%a1%e5%8c%ba%e9%97%b4)
    - [（六）回归函数μ(x)=ax+b函数值的点估计和置信区间](#%e5%85%ad%e5%9b%9e%e5%bd%92%e5%87%bd%e6%95%b0%ce%bcxaxb%e5%87%bd%e6%95%b0%e5%80%bc%e7%9a%84%e7%82%b9%e4%bc%b0%e8%ae%a1%e5%92%8c%e7%bd%ae%e4%bf%a1%e5%8c%ba%e9%97%b4)
    - [（七）Y的观察值的点预测和预测区间](#%e4%b8%83y%e7%9a%84%e8%a7%82%e5%af%9f%e5%80%bc%e7%9a%84%e7%82%b9%e9%a2%84%e6%b5%8b%e5%92%8c%e9%a2%84%e6%b5%8b%e5%8c%ba%e9%97%b4)
    - [（八）可化为一元线性回归的例子](#%e5%85%ab%e5%8f%af%e5%8c%96%e4%b8%ba%e4%b8%80%e5%85%83%e7%ba%bf%e6%80%a7%e5%9b%9e%e5%bd%92%e7%9a%84%e4%be%8b%e5%ad%90)
  - [4 多元线性回归](#4-%e5%a4%9a%e5%85%83%e7%ba%bf%e6%80%a7%e5%9b%9e%e5%bd%92)

# 第九章 方差分析及回归分析
## 1 单因素试验的方差分析
### （一）单因素试验
![Image0](anova_regression1.png)
![Image1](anova_regression2.png)
![Image2](anova_regression3.png)

### （二）平方和的分解
![Image0](anova_regression4.png)

上述$S_E$的各项$(X_{ij}-\bar{X}_{\cdot j})^2$表示在水平$A_j$下，样本观察值与样本均值的差异，这是由随机误差所引起的。$S_E$叫做`误差平方和`。$S_A$的各项$n_j(\bar{X}_{\cdot j}-\bar{X})^2$表示$A_j$水平下的样本平均值与数据总平均值的差异，这是由水平$A_j$的效应的差异以及随机误差引起的。$S_A$叫做因素A的`效应平方和`。(1.8)式就是我们所需要的平方和分解式。

### （三）SE，SA的统计特性
![Image0](anova_regression5.png)
![Image1](anova_regression6.png)

### （四）假设检验问题的拒绝域
![Image0](anova_regression7.png)
![Image1](anova_regression8.png)

### （五）未知参数估计
上面已讲过，不管H0是否为真，

$\hat{\sigma^2}=\frac{S_E}{n-s}$

是$\sigma^2$的无偏估计。

![Image0](anova_regression9.png)

## 2 双因素方差分析表
### （一）双因素等重复试验的方差分析
![Image0](anova_regression10.png)
![Image1](anova_regression11.png)
![Image2](anova_regression12.png)
![Image3](anova_regression13.png)
![Image4](anova_regression14.png)
![Image5](anova_regression15.png)

### （二）双因素无重复试验的方差分析
![Image0](anova_regression16.png)
![Image1](anova_regression17.png)
![Image2](anova_regression18.png)

## 3 一元线性回归
### （一）一元线性回归
![Image0](anova_regression19.png)

### （二）a，b的估计
![Image0](anova_regression20.png)
![Image1](anova_regression21.png)
![Image2](anova_regression22.png)

### （三）σ2的估计
![Image0](anova_regression23.png)
![Image1](anova_regression24.png)

### （四）线性假设的显著性检验
![Image0](anova_regression25.png)
![Image1](anova_regression26.png)

### （五）系数b的置信区间
![Image0](anova_regression27.png)

### （六）回归函数μ(x)=ax+b函数值的点估计和置信区间
![Image0](anova_regression28.png)

### （七）Y的观察值的点预测和预测区间
![Image0](anova_regression29.png)
![Image1](anova_regression30.png)

### （八）可化为一元线性回归的例子
![Image0](anova_regression31.png)
![Image1](anova_regression32.png)

## 4 多元线性回归
![Image0](anova_regression33.png)
![Image1](anova_regression34.png)
![Image2](anova_regression35.png)
