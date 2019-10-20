- [第八章 假设检验](#%e7%ac%ac%e5%85%ab%e7%ab%a0-%e5%81%87%e8%ae%be%e6%a3%80%e9%aa%8c)
  - [1 假设检验](#1-%e5%81%87%e8%ae%be%e6%a3%80%e9%aa%8c)
  - [2 状态总体均值的假设检验](#2-%e7%8a%b6%e6%80%81%e6%80%bb%e4%bd%93%e5%9d%87%e5%80%bc%e7%9a%84%e5%81%87%e8%ae%be%e6%a3%80%e9%aa%8c)
    - [（一）单个总体N(μ,σ2)均值μ的检验](#%e4%b8%80%e5%8d%95%e4%b8%aa%e6%80%bb%e4%bd%93n%ce%bc%cf%832%e5%9d%87%e5%80%bc%ce%bc%e7%9a%84%e6%a3%80%e9%aa%8c)
      - [1 σ2已知，关于μ的检验（Z检验）](#1-%cf%832%e5%b7%b2%e7%9f%a5%e5%85%b3%e4%ba%8e%ce%bc%e7%9a%84%e6%a3%80%e9%aa%8cz%e6%a3%80%e9%aa%8c)
      - [2 σ2未知，关于μ的检验（t检验）](#2-%cf%832%e6%9c%aa%e7%9f%a5%e5%85%b3%e4%ba%8e%ce%bc%e7%9a%84%e6%a3%80%e9%aa%8ct%e6%a3%80%e9%aa%8c)
    - [（二）两个正态总体均值差的检验（t检验）](#%e4%ba%8c%e4%b8%a4%e4%b8%aa%e6%ad%a3%e6%80%81%e6%80%bb%e4%bd%93%e5%9d%87%e5%80%bc%e5%b7%ae%e7%9a%84%e6%a3%80%e9%aa%8ct%e6%a3%80%e9%aa%8c)
    - [（三）基于成对数据的检验（t检验）](#%e4%b8%89%e5%9f%ba%e4%ba%8e%e6%88%90%e5%af%b9%e6%95%b0%e6%8d%ae%e7%9a%84%e6%a3%80%e9%aa%8ct%e6%a3%80%e9%aa%8c)
  - [3 正态总体方差的假设检验](#3-%e6%ad%a3%e6%80%81%e6%80%bb%e4%bd%93%e6%96%b9%e5%b7%ae%e7%9a%84%e5%81%87%e8%ae%be%e6%a3%80%e9%aa%8c)
    - [（一）单个总体的情况（χ2检验法）](#%e4%b8%80%e5%8d%95%e4%b8%aa%e6%80%bb%e4%bd%93%e7%9a%84%e6%83%85%e5%86%b5%cf%872%e6%a3%80%e9%aa%8c%e6%b3%95)
    - [正态总体均值、方差的检验法（显著性水平α）](#%e6%ad%a3%e6%80%81%e6%80%bb%e4%bd%93%e5%9d%87%e5%80%bc%e6%96%b9%e5%b7%ae%e7%9a%84%e6%a3%80%e9%aa%8c%e6%b3%95%e6%98%be%e8%91%97%e6%80%a7%e6%b0%b4%e5%b9%b3%ce%b1)
    - [（二）两个总体的情况（F检验法）](#%e4%ba%8c%e4%b8%a4%e4%b8%aa%e6%80%bb%e4%bd%93%e7%9a%84%e6%83%85%e5%86%b5f%e6%a3%80%e9%aa%8c%e6%b3%95)
  - [4 置信区间与假设检验之间的关系](#4-%e7%bd%ae%e4%bf%a1%e5%8c%ba%e9%97%b4%e4%b8%8e%e5%81%87%e8%ae%be%e6%a3%80%e9%aa%8c%e4%b9%8b%e9%97%b4%e7%9a%84%e5%85%b3%e7%b3%bb)
  - [5 样本容量的选取](#5-%e6%a0%b7%e6%9c%ac%e5%ae%b9%e9%87%8f%e7%9a%84%e9%80%89%e5%8f%96)
  - [6 分布拟合检验](#6-%e5%88%86%e5%b8%83%e6%8b%9f%e5%90%88%e6%a3%80%e9%aa%8c)
    - [（一）单个分布的χ2拟合检验法](#%e4%b8%80%e5%8d%95%e4%b8%aa%e5%88%86%e5%b8%83%e7%9a%84%cf%872%e6%8b%9f%e5%90%88%e6%a3%80%e9%aa%8c%e6%b3%95)
    - [（二）分布族的χ2拟合检验](#%e4%ba%8c%e5%88%86%e5%b8%83%e6%97%8f%e7%9a%84%cf%872%e6%8b%9f%e5%90%88%e6%a3%80%e9%aa%8c)
    - [（三）偏度、峰度检验](#%e4%b8%89%e5%81%8f%e5%ba%a6%e5%b3%b0%e5%ba%a6%e6%a3%80%e9%aa%8c)
  - [7 秩和检验](#7-%e7%a7%a9%e5%92%8c%e6%a3%80%e9%aa%8c)
  - [8 假设检验问题的p值检验法](#8-%e5%81%87%e8%ae%be%e6%a3%80%e9%aa%8c%e9%97%ae%e9%a2%98%e7%9a%84p%e5%80%bc%e6%a3%80%e9%aa%8c%e6%b3%95)

# 第八章 假设检验
## 1 假设检验
![Image0](hypothesis-testing1.png)
![Image1](hypothesis-testing2.png)

## 2 状态总体均值的假设检验
### （一）单个总体N(μ,σ2)均值μ的检验
#### 1 σ2已知，关于μ的检验（Z检验）
![Image0](hypothesis-testing3.png)

#### 2 σ2未知，关于μ的检验（t检验）
![Image0](hypothesis-testing4.png)

### （二）两个正态总体均值差的检验（t检验）
![Image0](hypothesis-testing5.png)

### （三）基于成对数据的检验（t检验）
![Image0](hypothesis-testing6.png)

## 3 正态总体方差的假设检验
### （一）单个总体的情况（χ2检验法）
![Image0](hypothesis-testing7.png)
![Image1](hypothesis-testing8.png)

### 正态总体均值、方差的检验法（显著性水平α）
![Image0](https://note.youdao.com/yws/res/58280/AC268D658D024CAC82A72CB2FB19B891)
![Image1](https://note.youdao.com/yws/res/58279/2A340A2F079140FAA580D36810AFD713)

### （二）两个总体的情况（F检验法）
![Image0](https://note.youdao.com/yws/res/58283/4EA43A27B0CE403D8CAE2E3136EBAA20)

## 4 置信区间与假设检验之间的关系
![Image0](https://note.youdao.com/yws/res/58286/DEE06134A4294B729AC97FF8DFEE28DB)
![Image1](https://note.youdao.com/yws/res/58287/F94239B461ED412D9F44946A57E2362B)
![Image2](https://note.youdao.com/yws/res/58289/F0ED2BB267264EB39CA67C0A40431199)

## 5 样本容量的选取
![Image0](https://note.youdao.com/yws/res/58292/DDAFB867D0404EA7BDD87266D0BCAC03)
![Image1](https://note.youdao.com/yws/res/58293/12FB460B9D9F48A4BFAABCE0FDF50158)
![Image2](https://note.youdao.com/yws/res/58295/FE2D9207B82B45878C0DD2CBA1D1CE82)
![Image3](https://note.youdao.com/yws/res/58294/A287D45B46E2480CA2C076FBCCACA331)
![Image0](https://note.youdao.com/yws/res/58299/D59B6EABEAA74C96BB57385244D44C57)
![Image1](https://note.youdao.com/yws/res/58298/68E9D12AD9E843F692A392382AC969F7)
![Image2](https://note.youdao.com/yws/res/58297/A64006C6C38A424D818EBEA708587896)

## 6 分布拟合检验
### （一）单个分布的χ2拟合检验法
![Image0](https://note.youdao.com/yws/res/58304/AF53AECEE9044142AADFF2A4CF388CDC)
![Image1](https://note.youdao.com/yws/res/58302/B4713832C70D4CF0AE47B1F9BE28B515)
![Image2](https://note.youdao.com/yws/res/58303/DB47447ABD954D51A187406A1FC17D54)

### （二）分布族的χ2拟合检验
![Image0](https://note.youdao.com/yws/res/58308/A791082D0ECA4A7880E42F8C4C5AA2E2)
![Image1](https://note.youdao.com/yws/res/58310/9AB741B2F02D43CC90D6D83833B9A0C5)

### （三）偏度、峰度检验
![Image0](https://note.youdao.com/yws/res/58313/50564849533D4E089D440B001DD3D8B2)
![Image1](https://note.youdao.com/yws/res/58314/07059137DDE84927B8274277A20BAF4D)
![Image2](https://note.youdao.com/yws/res/58315/2D9BE44A0639440DA583B367BA201781)
![Image3](https://note.youdao.com/yws/res/58317/B5A783C4431C4E38A48DE5D19A6A9812)

## 7 秩和检验
![Image0](https://note.youdao.com/yws/res/58321/8366BDE2C681406C881657BA48C49910)
![Image1](https://note.youdao.com/yws/res/58323/083CFA34A2384CC58530088CD7FE8B49)
![Image2](https://note.youdao.com/yws/res/58324/EC280A6CFA7D4B38B6C40154B09900F3)
![Image3](https://note.youdao.com/yws/res/58325/C1E89F0D55CB4CB5B0AF902C2DDBFE5D)

## 8 假设检验问题的p值检验法
![Image0](https://note.youdao.com/yws/res/58328/4B45465AB62B4348A063C4F0FA1E9856)
![Image1](https://note.youdao.com/yws/res/58330/586263A988BF442B9BC6F52129014203)
![Image2](https://note.youdao.com/yws/res/58332/5E67608B306D417A8D8575B8B799A5DF)
![Image3](https://note.youdao.com/yws/res/58331/085F09018F5A470CA78930CBBACCE019)
![Image0](https://note.youdao.com/yws/res/58334/08EE7BB9A278451089503BBBBBA35586)
![Image1](https://note.youdao.com/yws/res/58335/1423A3563A6A437B97CDAAA23276A8EA)
