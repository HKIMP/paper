## 清华 

pip install XXX -i https://pypi.tuna.tsinghua.edu.cn/simple

## Spacy

pip install -U spacy -i https://pypi.tuna.tsinghua.edu.cn/simple

pip install -i https://pypi.tuna.tsinghua.edu.cn/simple spacy --uesr

下载spacy：https://pypi.org/project/spacy/1.9.0/#description



出现：Defaulting to user installation because normal site-packages is not writeable

解决方法：pip install -U spacy -i https://pypi.tuna.tsinghua.edu.cn/simple

使用pip install en_core_web_sm-2.3.0.tar.gz 

import spacy

spacy.load('en_core_web_sm')





官方提供了两种

## Torch

```bash
# 配置国内源，方便安装Numpy,Matplotlib等
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
# 配置国内源，安装PyTorch用
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
# 显示源地址
conda config --set show_channel_urls yes
```

- 安装PyTorch

```
# 安装PyTorch，要使用国内源请去掉-c pytorch这个参数！！
conda install pytorch torchvision cudatoolkit=10.0
```

[pytorch 安装](https://blog.csdn.net/watermelon1123/article/details/88122020#11%E6%9C%8826%E6%97%A5%E6%9B%B4%E6%96%B0ubuntu%E4%B8%8Bpytorch1.3%E5%AE%89%E8%A3%85%28%E9%80%9A%E8%BF%87conda%29)


- 安装常用库

```
pip install numpy matplotlib pillow pandas
```

df -h 查看磁盘剩余空间

du -sh * 查看大文件 (对当前目录下每一个目录和文件的大小分别进行汇总)

du - sh . 对当前目录下所有的目录和文件大小进行汇总，-s 表示汇总 -h 表示人性化显示

du -sh .[!.]* 查看隐藏文件

某个目录空间快满了，删除了若干文件之后，使用df -h显示还是快满的，但是现实的总文件大小却没那么大。原因是某个进程正在使用删除的文件，导致删除之后，空间仍不能释放。

查看rm掉但是扔被占用的文件的列表，使用如下命令：

lsof |grep -i deleted（lsof -n | grep deleted）

再使用 ps -aux | grep pid查到对应的进程号，在关闭进程 kill

* 更新Pytorch

  ~~~shell
  conda updata pytorch torchvision -c pytorch
  ~~~

  

查看进程

ps -f -p 46047

ps -ef | grep xxx

ps:process show 展示进程

e:显示所有程序

f:显示UID，PID，PPID

~~~shell
apt --fix-broken install
~~~

su: Authentication failure 解决办法

~~~shell
sudo passwd root
~~~

软连接硬链接http://c.biancheng.net/view/740.html



## HuggingFace使用

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

??? pip install pytorch_pretrained_bert



不更新预训练模型，固定参数:

```python
def __init__(self, freeze_bert=False, ...):
    super(MyModel, self).__init__()
    self.bert = AutoModel.from_pretrained(model_name, output_hidden_states=True..)
	if freeze_bert:
        for p in self.bert.parameters():
            p.requires_grad = False  
```







