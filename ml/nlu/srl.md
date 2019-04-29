语义角色标注 (Semantic Role Labeling, SRL) 是一种浅层的语义分析技术，标注句子中某些短语为给定谓词的论元 (语义角色) ，如施事、受事、时间和地点等。其能够对问答系统、信息抽取和机器翻译等应用产生推动作用。

语义标注的不足之处

- 仅仅对于特定谓词进行论元标注，那多谓词呢？没有涉及到。
- 不会补出句子所省略的部分语义。信息有所缺失。

核心的语义角色: A0-5 六种，A0 通常表示动作的施事，A1通常表示动作的影响等，A2-5 根据谓语动词不同会有不同的语义含义。

附加语义角色(15种)：

- ADV adverbial, default tag ( 附加的，默认标记 )
- BNE beneﬁciary ( 受益人 )
- CND condition ( 条件 )
- DIR direction ( 方向 )
- DGR degree ( 程度 )
- EXT extent ( 扩展 )
- FRQ frequency ( 频率 )
- LOC locative ( 地点 )
- MNR manner ( 方式 )
- PRP purpose or reason ( 目的或原因 )
- TMP temporal ( 时间 )
- TPC topic ( 主题 )
- CRD coordinated arguments ( 并列参数 )
- PRD predicate ( 谓语动词 )
- PSR possessor ( 持有者 )
- PSE possessee ( 被持有 )