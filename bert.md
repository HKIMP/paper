用来训练 tranformer 模型中的 encoder网络？


自编码 自回归？

BPE byte pair encoding ?

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




BERT源码

1. [Bert代码详解（一）](https://blog.csdn.net/cpluss/article/details/88418176)
2. [Huggingface-transformers项目源码剖析及Bert命名实体识别实战](https://blog.csdn.net/weixin_36949593/article/details/106515904)
3. 

BERT理解
1. [一文读懂BERT(原理篇)](https://blog.csdn.net/jiaowoshouzi/article/details/89073944)

2. 


两个任务：
1. 预测被遮挡的单词
2. 预测下一个句子





