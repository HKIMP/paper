## Question

为什么word2vec是静态的啊，word2vec不可训练吗?

用来训练 tranformer 模型中的 encoder网络？

BERT输入的原始向量是什么啊？是随机初始化的还是预训练好的啊？

自编码 自回归？

BPE byte pair encoding ?

pooler?
普通的bert后边也有 pooled_output吗
attention mask tensor 作用 ？

pooler_output?
```
pooler_output (torch.FloatTensor of shape (batch_size, hidden_size)) – Last layer hidden-state of the first token
of the sequence (classification token) further processed 
by a Linear layer and a Tanh activation function. 
The Linear layer weights are trained from the next sentence prediction
 (classification) objective during pretraining.
```
是不是最后一层 最开始标志位加一个线性层 激活函数的输出。 对


outputs.hidden_states 为什么返回的是(batch_size, sequence_length, hidden_size)
不应该是每一层的输出吗？

BERT 双向？ GPT单向？ BERT用的是Transformers的encoder，GPT用的是Transformers的decoder
要了解 ELmo GPT

weight dacay


position embedding???怎么去生成
是自己输入的是 token_tensors, segments_tensor, masks_tensors 然后 分词自动生成 [token_embeddings, segment_embeddings, position_embeddings]








BERT源码

1. [Bert代码详解（一）](https://blog.csdn.net/cpluss/article/details/88418176)
2. [Huggingface-transformers项目源码剖析及Bert命名实体识别实战](https://blog.csdn.net/weixin_36949593/article/details/106515904)
3. 

BERT理解
1. [一文读懂BERT(原理篇)](https://blog.csdn.net/jiaowoshouzi/article/details/89073944)

2. [图解BERT模型：从零开始构建BERT](https://cloud.tencent.com/developer/article/1389555)

3. [请问GPT为什么不能双向？](https://www.zhihu.com/question/322034410)

双向的问题
4. [从语言模型看Bert的善变与GPT的坚守](http://www.tensorinfinity.com/paper_160.html)




两个任务：
1. 预测被遮挡的单词
2. 预测下一个句子

token_id默认是什么 都是一句话吗

attention_mask作用





