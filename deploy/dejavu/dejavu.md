# DejaVu: KV-cache Streaming for Fast, Fault-tolerant Generative LLM Serving

偏系统，主要在解决KV缓存在CPU和GPU之间传输的效率问题，留以后细读
## 现有问题
* 流水线泡沫
* 像FasterTransformer这样的最新LLM服务系统，在流水线并行设置中过度配置KV缓存
* 现有的LLM服务系统未能有效处理故障或抢占
  