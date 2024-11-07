# CORM: Cache Optimization with Recent Message for Large Language Model Inference

## 思路
首先认为相似的query会关注相似的token

然后发现当前token与最近token会比较相似

于是用最近token来选择重要token，具体来说，在最近token中都认为是不重要的token会被永久淘汰。同时，总是保存最近token