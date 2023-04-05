---
title: PyTorch学习笔记
date: 2022-10-21 16:14:56
tags: 深度学习
---

# PyTorch学习

学着学着就发现自己的这方面的基础还是太差了，所以决定学一下PyTorch基础，相信绝对不会亏！！！

*下面都是一个简单的介绍或者说总结，详细内容请看官方文档[PyTorch documentation](https://pytorch.org/docs/stable/index.html)，这个非常重要*

## 1.数据加载

主要用到两个函数

datasets

DataLoader()

datasets是用来获取或者说读取数据的，不过现在一般都是使用torchvision.datasets来进行数据集的下载

DataLoader()则用来对数据做一些设置，例如按照batch_size来分堆，我们使用数据主要就是使用DataLoader()函数获得的对象，它能把数据和标签分别存起来，后面直接调用，例如img, target = test_data[0]



## 2.网络模型骨架（nn.Module）

需要重写nn.Module类，主要重写两个函数，一个初始化函数，一个forward函数,下面讲的都是常用的。

### 2.1卷积层

我们常用的是[`nn.Conv2d`](https://pytorch.org/docs/stable/generated/torch.nn.Conv2d.html#torch.nn.Conv2d)（2d表示对2维数据，即图像进行操作），主要确定以下参数

- in_channels：输入通道数量
- out_channels：指定输出通道数量
- kernel_size：卷积核大小
- stride：步长
- padding：周围填充

### 2.2池化层

这里以最大池化层为例

常用[`nn.MaxPool2d`](https://pytorch.org/docs/stable/generated/torch.nn.MaxPool2d.html#torch.nn.MaxPool2d)，主要确定以下参数

- *kernel_size*：卷积核大小
- *stride*：步长

### 2.3非线性激活层（Non-linear Activations）

用来给网络里加入一些非线性特征，常用有ReLU,SIGMOID函数

### 2.4 线性层（linear）

又叫全连接层，常用[`nn.Linear`](https://pytorch.org/docs/stable/generated/torch.nn.Linear.html#torch.nn.Linear)函数实现，可以把数据集的特征压缩指定值，使用之前通常需要用Flatten()变到一维，最后输出的维度就是所有可能的结果的数量，分别代表着每种结果的概率，通常需要确定以下值

- in_features：输入样本大小
- out_features：输出样本大小
- bias：如果设置为False，则图层不会学习附加偏差。默认值是True，表示增加学习偏置。

### 2.5 SEQUENTIAL（torch.nn.Sequential）

把网络放在一起，让代码更加整洁

## 3 lossfunction

主要有两个作用

1.计算实际输出与目标之间的差距

2.为我们更新输出提供一定的依据（反向传播），给每个卷积核设置了一个梯度（grad）

第一次时模型还没有梯度参数，在进行一次loss.backward()后，模型就可以得到梯度这个重要的参数。

常用的有交叉熵函数[`nn.CrossEntropyLoss`](https://pytorch.org/docs/stable/generated/torch.nn.CrossEntropyLoss.html#torch.nn.CrossEntropyLoss)

## 4优化器（optimizer）

常用函数有optimizer.zero_grad()，放在梯度计算之前，防止上次残留的梯度对这次的计算造成影响。

以及optimizer.step()，通过梯度来对模型参数进行更新（例如卷积核的大小等）

## 5模型的保存与加载

可以torch.save()来保存模型，然后通过torch.load()加载模型

也可以通过torch.save()来保存model.state_dict()，然后通过model.load_state_dice()来加载模型

资料来源[xiaotudui/pytorch-tutorial: PyTorch深度学习快速入门教程（绝对通俗易懂！） (github.com)](https://github.com/xiaotudui/PyTorch-Tutorial)，
