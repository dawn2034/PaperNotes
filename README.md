# PaperNotes

A collection of notes for my paper reading.

* Content
  * [Relation Extraction](#RelationExtraction)



# RelationExtraction

1. Contextualised Graph Attention for Improved Relation Extraction. 2020/04/22 [arxiv:2004.10624](https://arxiv.org/abs/2004.10624)

    最新的一篇用GNN做句子级实体关系抽取的文章, 核心思想是根据整个句子的依存树得到多个子图, 包括: (1)头尾实体的最短依存路径 (2)分别与头、尾实体直接相连的词构成子图. Encoding图里的每个词时用5种embedding拼接起来: (1)预训练bert编码BPE得到contextual embedding, (2)POS embedding, (3)depenency relation embedding, (4)entity type embedding 和 (5)是否是entity mention的indicator embedding. 作者还设计了两种edge features(1)两个相连的词组成的三元组(POS1, POS2, 依存关系)在corpus中的出现频率, (2)表明是否与实体相连的全0/全1特征向量与GAT结合计算顶点的表示. 然后图的词列经过BiLSTM, GAT(FFN), weighted sum, multi-head attention, 最后三个图级别的attention加权和...最后就是一个判断关系类别的图分类任务. 本文进行了非常丰富的组合实验, (LSTM) + GAT/GCN + 单图SG/多图MG + 边特征1/边特征2/12, 比较分析了单图/多图, 不同句子长度, 不同图大小的影响. GAT牛逼, 多子图牛逼, 本文提出的边特征牛逼. 本文的方法在SemEval2010Task8取得了SoTA的结果.


