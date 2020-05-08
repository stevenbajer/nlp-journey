# 工程实践笔记

## 1、有监督和无监督问题

目前有监督模型明显比无监督模型效果更好。工业界总有办法标注一批数据出来，哪怕招聘一批数据标注实习生人工标注也不是什么难事。

实际操作过程中，可以先借助无监督的办法，如聚类算法，先将数据大致聚一下类，然后花费一点时间，人工标注一下数据，把无监督问题变为有监督问题进行处理。

## 2、模型的选择

工业界在NLP方面对模型的选择，要考虑的因素很多。大致可以分为以下几个方面：

1. 数据量的大小。如果是创业公司或者较小的公司，早期可能没有那么多数据，这时候就要考虑传统的机器学习方法，比如用SVM来对文本进行分类。后期数据量积累了之后，可以切换到深度学习的方法。如果数据量更少，可以用一些规则的方式来处理，用规则的方式积累数据。比如正则，正则其实非常强大，在项目的初期阶段，正则往往能收到奇效。
2. 倾向于简单的模型。工业界中，越简单的模型越容易被采用，原因在于，复杂的模型容易失控，尤其是深度学习模型。而越简单的模型，可解释性往往越好。
3. 运行速度很重要。在一个模型的推理阶段，越深的模型耗时越多。数据预处理的耗时加上推理的耗时，往往会导致输出的延时，影响用户体验。

## 3、CPC、CPA、CVR、CTR、ROI

**CPC**：“Cost Per Click”的英文缩写。每次点击付费广告，当用户点击某个网站上的CPC广告后，站长就会获得相应的收入。

**CPA**：按照行为（Action）作为指标来计费，这个行为可以是注册、咨询、放入购物车等等。

**CVR**：转化率。是一个衡量CPA广告效果的指标，简言之:用户点击广告到成为一个有效激活或者注册甚至付费用户的转化率。

**CTR**：Click-Through-Rate, 即点击通过率，是常用的网络广告是指在线广告的点击率(图片广告排名/文本广告/关键字广告/广告/视频广告,等等),也就是说,点击广告的实际数量(严格地说,打到目标页面的数量)除以广告(显示内容)的数量。

**ROI**：投入产出比。即每获得一个有效转化所花费的成本，该指标就是衡量效果广告的投入产出比。

## 4、错别字纠错

使用语言模型对句子中的错别字进行判别的几个步骤：

1. 使用kenlm训练自己的语言模型。
2. 对测试集中存在敏感错别字的句子中的错别字进行替换，得到一个新的句子。
3. 导入训练好的语言模型，分别对原来的句子和替换后新得到的句子进行打分。
4. 如果新得到的句子的分数比原来的句子高，就说明原来的句子出现了问题，该单词应该修改为需要替换后的那个单词。

> 来自[`使用kenlm模型判别a/an错别字`](https://zhuanlan.zhihu.com/p/39722203)