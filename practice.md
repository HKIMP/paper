1. from transformers import BertForMaskedLM和 AutoModel
   结果不一样， Auto不是自动判断吗，还是调用MaskedLM会修改在最后
   修改结构？