# lazyLLM 和 Finch的启发

Finch中有分块的思想，每个块与prompt做注意力计算来得到注意力分数

lazyLLM将预填充的部分计算分散到后续的解码阶段来做来减少TTFT

* 是否可以实现一个逐步递减的cache,用一个观察窗口作为query来计算注意力分数，但是一次生成过程中只计算一次窗口，并在这个窗口内进行融合。
* 能否在channel的方向上融合
* q,k,v都考虑的注意力值预测

# 遗忘因子

预测注意力分数到底要考虑多少步状态信息是一个问题，现有的固定折扣因子缺乏灵活性。

* 将遗忘因子和注意力头的分类相结合，检索头让他参考更长的历史信息，非检索头让他参考更短的历史信息



# 位置编码相关思考

在做merge的时候对部分token的位置做了一些移动，而在生成过程中，因果掩码会对一个token所能attend到的位置做了限制（只能attend到自己位置之前的token），而merge操作移动了部分token，改变了这些token所能attend到的范围，是否能够在因果掩码上做些修改来缓解注意力范围变化的问题。


# 语义相似度

https://www.cnblogs.com/shona/p/11971310.html

* 余弦相似度
* Jaccard相似度
* 编辑距离
* 欧氏距离
* 汉明距离
* Jaro-Winkler距离
* Levenshtein距离
* Jaro距离
* Cosine similarity
* Jaccard similarity
* Edit distance
* Euclidean distance
* Hamming distance
