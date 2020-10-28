1. rocket qa

2. bert改进

3. teacher forcing

4. 模型蒸馏

5. transformer-XL, XLNET, ALBERT, RoBERTa DistilBERT

   



## Practice

HuggingFace 使用清华源

注意：`transformers > 3.1.0` 的版本支持下面的 `mirror` 选项。

只需在 `from_pretrained` 函数调用中添加 `mirror` 选项，如：

```
AutoModel.from_pretrained('bert-base-uncased', mirror='tuna')
```

目前内置的两个来源为 `tuna` 与 `bfsu`。此外，也可以显式提供镜像地址，如：

```
AutoModel.from_pretrained('bert-base-uncased', mirror='https://mirrors.tuna.tsinghua.edu.cn/hugging-face-models')
```







Good:

1. [transformer-XL与XLNet笔记](https://carlos9310.github.io/2019/11/11/transformer-xl-and-xlnet/#transformer-xl)
2. 

