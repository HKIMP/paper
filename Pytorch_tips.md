## 1. Pytorch为什么要手动梯度清零

1. ## 为什么要梯度叠加？

不懂为什么不是处理每个batch清除一次梯度，而是两次或多次再清除一次，相当于提高了batch_size，对硬件要求更高，更适用于需要更高batch_size的情况

用 w.grad.data._zero _ ()就能清零了吗 （总结来说还是不明白为什么梯度清零）

## 2. with torch.no_grad():？？？

不记录梯度？

3. model.train()

4. model.eval() with torch.no_grad() ???

5. torch.tensor 和 torch.Tensor区别？

6. 在 criterion = torch.nn.MSELoss(size_average=False) 那这个loss就是 loss和 

接下来 loss = criterion(y_pred, y_data) loss.backward() 那这个loss反向传播的这个loss是loss和？

问题点就是 批量 batch_size  和 各种优化

7. 试试不同优化器 （SGD。。。

8. 为什么要训练很多个epoch



9. dataloader多线程可能报错

~~~python
train_loader = Dataloader(dataset=dataset, batch_size=32, shuffle=True, num_workers=2) 
#使用多线程可能报错
if __name__ == '_main_':
    for epoch in range(100):
        for i, data in enumerate(train_loader, 0):
            #1 Prepare data
~~~

10. CrossEntropyLoss

(N, C, d1, d2...dk)?

11. dataset  dataloader

12. t transpose permute 轴交换

13. gpu设备

```python
if torch.cuda.is_available():
    device = torch.device('cuda')
    y = torch.ones_like(x, device=device)
    x = x.to(device)
    z = x + y
    z = z.to('cpu', torch.double) #to方法能同时指定类型
```

```python
device = torch.device('cuda:0' if torch.cuda.is_available() else 'cpu')
```

14. 

```python
optimizer = torch.optim.SGD(model.paremeters(), lr=0.01)
```

15. 动态图 静态图

16. 非标量反向传播

17. .data .detach()

    .data 返回一个与之前Tensor共享内存的Tensor 只不过 requires_grad=False

    

    .detach() 比.data 安全 因为如果 in-place 操作修改了计算图中的tensor，将报警

    

    ```python
    a = torch.tensor([1., 2., 3.], requires_grad=True)
    out = a.sigmoid()
    c = out.detach()
    c.zero_()
    out.sum().backward()
    
    RuntimeError: one of the variables needed for gradient computation has been modified by an inplace operation: [torch.FloatTensor [3]], which is output 0 of SigmoidBackward, is at version 1; expected version 0 instead. Hint: enable anomaly detection to find the operation that failed to compute its gradient, with torch.autograd.set_detect_anomaly(True).
    ```

    

18. tensor.numpy()

    require_grad=True 不能直接转换 需要 tensor.detach().numpy()

    

19. tensor.gard 也是tensor 类型是 torch.FloatTensor?

    

20. model.eval()表示设置模型为评估模式，即预测模式。

    model.train(mode=True)表示训练模式

    主要是dropout batchnormalizaion的区别

    

21. 在gpu上运行的结果 转化为numpy类型

    predict = predict.cpu().detach().numpy()

    

22. torch.nn.function 和 torch.nn区别



23. 两种方式 实现交叉熵

    ```python
    criterion = torch.nn.CrossEntropy()
    loss = criterion(input, target)
    
    #or
    
    output = F.log_softmax(x, dim=1)
    loss = F.nll_loss(output, target)
    ```



24. dataloader 的 pin_memory 和 放不放gpu有什么关系？



25. 模型保存和加载

    ```python
    #保存
    torch.save(model.state_dict(), 'model/mnist_net.pt')
    torch.save(optimizer.state_dict(), 'model/mnist_optimizer.pt')
    
    #加载
    model.load_state_dict(torch.load('model/mnist_net.pt'))
    optimizer.load_state_dict(torch.load('model/mnist_optimizer.pt'))
    ```

26. tensor.max(keepdim) ??

27. pytorch tensor类型判断

    ```python
    #type(tensor)
    type(a)
    torch.Tensor
    
    #tensor.type() 推荐 更详细
    a.type()
    torch.LongTensor
    
    #isinstance
    isinstance(a, torch.Tensor)
    True
    isinstance(a, torch.LongTensor)
    True
    isinstance(a, torch.BoolTensor)
    False
    ```

    

28. ```python
    os.path.abspath('.')#获取当前工作目录路径
    ```



29. 列表合并要用 extend 而不是 append



29. 打印gpu名称

    ```python
    torch.cuda.get_device_name(0)
    ```


30. rnn batch_size=True 和 False 序列形状 

    a = a.permute(1, 0, 2) ?????

31. tensor类型转换

    * 简单后缀转换

      ```python
      tensor.int()
      tensor.float()
      tensor.double()
      ```

    * 使用torch.type()函数

      ```python
      tensor.type(torch.FloatTensor)
      ```

    * 使用type_as(tensor)将tensor转换为指定tensor类型

    * tensor创建 -- 指定维度和数据类型

      ```python
      torch.IntTensor(3, 4).zero_()
      torch.Tensor(3, 4).zero()_
      ```

32. rnn 双向 的时候 output拆开什么样子

33. log_softmax 交叉熵的问题

34. 正则表达式学习

35. nn.utils.rnn.pack_padded_sequence 打包

    nn.utils.rnn.pad_packed_sequence 解包

    

36. permute



