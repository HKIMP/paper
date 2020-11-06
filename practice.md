1. [Transformers 从pytorch-pretrained-bert迁移](http://panchuang.net/2020/04/29/transformers-%E4%BB%8Epytorch-pretrained-bert%E8%BF%81%E7%A7%BB-%E5%8D%81/)

2. [浅谈 PyTorch 中的 tensor 及使用](https://blog.csdn.net/byron123456sfsfsfa/article/details/90609758)


3. from transformers import BertForMaskedLM和 AutoModel
   结果不一样， Auto不是自动判断吗，还是调用MaskedLM会修改在最后
   修改结构？ 修改结构

4. 保存每次最佳的参数

5. named_children named_parameters names_module

6. 参考2
冻结部分网络参数
```python
model = torchvision.model.resnet18(pretrained=True)
for param in model.parameters():
   param.requires_grad = False

#用一个全新的fc层 来替代之前的全连接层
#因为新构建的fc层的参数默认 requires_grad=True
model.fc = nn.Linear(512, 100)

#只更新fc参数
optimizer = optim.SGD(model.fc.parameters(), lr=1e-2, momentum=0.9)
```
