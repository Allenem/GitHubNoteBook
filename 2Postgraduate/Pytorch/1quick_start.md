# Pytorch 快速入门

## 目录

- `torch`, `ipython`, `ipdb`, `jupyter`, `CUDA`, `CUDANN` 的安装
- `Tensor` 简介
- `autograd` 简介
- 神经网络nn
- 牛刀小试：CIFAR-10分类

---

## 1.安装 `torch`

访问官网 [https://pytorch.org/](https://pytorch.org/) 寻找适合自己的 `torch`, `torchvision`, `torchaudio` 版本安装

Windows 命令：

```bash
pip install torch===1.7.1 torchvision===0.8.2 torchaudio===0.7.2 -f https://download.pytorch.org/whl/torch_stable.html
```

我的速度太慢啦，就直接下载whl文件安装

`https://download.pytorch.org/whl/cu102/torch-1.7.1-cp36-cp36m-win_amd64.whl`

`https://download.pytorch.org/whl/cu102/torchvision-0.8.2-cp36-cp36m-win_amd64.whl`

`https://download.pytorch.org/whl/torchaudio-0.7.2-cp36-none-win_amd64.whl`

```bash
pip install torch-1.7.1-cp36-cp36m-win_amd64.whl torchvision-0.8.2-cp36-cp36m-win_amd64.whl torchaudio-0.7.2-cp36-none-win_amd64.whl
```

安装成功，显示如下：

```bash
Successfully installed dataclasses-0.8 torch-1.7.1 typing-extensions-3.7.4.3 torchaudio-0.7.2 torchvision-0.8.2
```

---

## 2.安装 `ipython` & `ipdb` & `jupyter`

```bash
pip install ipython ipdb jupyter
```

安装好后命令行直接输入 `ipython` 启动 `IPython`

代码中 `import ipdb` 引入 debug 功能

命令行输入 `jupyter notebook` 浏览器启动 `Jupyter`，或者手动输入 `http://127.0.0.1:8888`

---

## 3.安装 `CUDA` & `CUDANN` 则可用 `GPU` 计算

电脑桌面右击 `NVIDIA控制面板` → `帮助` → `系统信息` → `组件`，查看自己的 `驱动` & `CUDA` 支持版本，官网 https://developer.nvidia.com/cuda-toolkit-archive 或者其他渠道寻找下载安装。

`CUDANN` 从官网 https://developer.nvidia.com/rdp/cudnn-archive 下载安装特定版本。

实际上，我的显卡 GeForce GTX 960M 驱动版本太旧 382.05 ，我直接下载升级驱动到了 461.09 。理论上的安装步骤应该是：安装显卡驱动 -> 查看CUDA支持版本 -> 安装 `torch`, `torchvision`, `torchaudio` 指定版本。

---

## 4.Tensor

eg1.加法

```py
import torch as t 

# Build a matix with size 5*3, its space allocated but it's NOT initialized
a = t.Tensor(3,4)
# Initialize a matrix with uniform distribution in [0,1] & size 5*3
x = t.rand(5, 3)
print(x)
y = t.rand(5, 3)
print(y)
# Print x's size, row, column
print(x.size(), x.size()[0], x.size(0), x.size()[1], x.size(1))

# Add Method 1
print(x + y)
# Add Method 2
print(t.add(x, y))
# Add Method 3, need preallocate space
result = t.Tensor(5, 3) 
t.add(x, y, out=result) 
print(result)
# Add Method 4, y isn't changed
s = y.add(x) 
print(s, y)
# Add Method 5, y IS changed
y.add_(x) 
print(y)
```
<details>
<summary>OUTPUT</summary>

```bash
tensor([[0.6794, 0.1218, 0.5304],
        [0.5599, 0.6890, 0.4911],
        [0.2290, 0.0117, 0.1078],
        [0.5902, 0.4370, 0.0467],
        [0.6739, 0.1170, 0.2570]])
tensor([[0.8950, 0.0903, 0.2694],
        [0.6663, 0.2188, 0.8282],
        [0.8049, 0.1454, 0.9109],
        [0.8443, 0.5518, 0.3769],
        [0.4926, 0.9064, 0.1200]])
torch.Size([5, 3]) 5 5 3 3
tensor([[1.5744, 0.2120, 0.7998],
        [1.2262, 0.9078, 1.3193],
        [1.0339, 0.1571, 1.0187],
        [1.4345, 0.9887, 0.4236],
        [1.1664, 1.0233, 0.3770]])
tensor([[1.5744, 0.2120, 0.7998],
        [1.2262, 0.9078, 1.3193],
        [1.0339, 0.1571, 1.0187],
        [1.4345, 0.9887, 0.4236],
        [1.1664, 1.0233, 0.3770]])
tensor([[1.5744, 0.2120, 0.7998],
        [1.2262, 0.9078, 1.3193],
        [1.0339, 0.1571, 1.0187],
        [1.4345, 0.9887, 0.4236],
        [1.1664, 1.0233, 0.3770]])
tensor([[1.5744, 0.2120, 0.7998],
        [1.2262, 0.9078, 1.3193],
        [1.0339, 0.1571, 1.0187],
        [1.4345, 0.9887, 0.4236],
        [1.1664, 1.0233, 0.3770]]) tensor([[0.8950, 0.0903, 0.2694],
        [0.6663, 0.2188, 0.8282],
        [0.8049, 0.1454, 0.9109],
        [0.8443, 0.5518, 0.3769],
        [0.4926, 0.9064, 0.1200]])
tensor([[1.5744, 0.2120, 0.7998],
        [1.2262, 0.9078, 1.3193],
        [1.0339, 0.1571, 1.0187],
        [1.4345, 0.9887, 0.4236],
        [1.1664, 1.0233, 0.3770]])
```

</details>

eg2.Numpy 与 Tensor 互相转换

```py
import torch as t
import numpy as np

a = t.ones(5)
b = a.numpy()
c = np.ones(5)
d = t.from_numpy(c)

print(a, b, c, d)

a.add_(1)
d.add_(1)

# Numpy & Tensor share memory
print(a, b, c, d)
```

OUTPUT

```bash
tensor([1., 1., 1., 1., 1.]) [1. 1. 1. 1. 1.] [1. 1. 1. 1. 1.] tensor([1., 1., 1., 1., 1.], dtype=torch.float64)
tensor([2., 2., 2., 2., 2.]) [2. 2. 2. 2. 2.] [2. 2. 2. 2. 2.] tensor([2., 2., 2., 2., 2.], dtype=torch.float64)
```

---

## 5.autograd

`t.autograd` 的 `Variable` 简单封装了 Tensor，主要包含如下三个属性：

- `data`：保存 Variable 所包含的 Tensor
- `grad`：保存 data 对应的梯度，grad 也是个 Variable，而不是 Tensor，它和 data 的形状一样
- `grad_fn`：指向一个 Function 对象，这个 Function 用来反向传播计算输入的梯度，具体下节再讲

eg1.grad 在反向传播时不断累加，所以反向传播之前需要把梯度清零

```py
import torch as t
from torch.autograd import Variable

x = Variable(t.ones(2, 2), requires_grad=True)
y = x.sum()

print(x)
print(y)
print(x.grad_fn)
print(y.grad_fn)

y.backward()
print(x.grad)

y.backward()
print(x.grad)

y.backward()
print(x.grad)

# Gradient Reset to 0
print(x.grad.data.zero_())
y.backward()
print(x.grad)
```

OUTPUT

```bash
tensor([[1., 1.],
        [1., 1.]], requires_grad=True)
tensor(4., grad_fn=<SumBackward0>)
None
<SumBackward0 object at 0x0000018A8EC44F28>
tensor([[1., 1.],
        [1., 1.]])
tensor([[2., 2.],
        [2., 2.]])
tensor([[3., 3.],
        [3., 3.]])
tensor([[0., 0.],
        [0., 0.]])
tensor([[1., 1.],
        [1., 1.]])
```

eg2.Variable 与 Tensor 无缝切换

```py
import torch as t
from torch.autograd import Variable

x = Variable(t.ones(4, 5))
y = t.cos(x)
x_tensor_cos = t.cos(x.data)

print(y)
print(x_tensor_cos)
print(type(y))
print(type(x_tensor_cos))
```

OUTPUT

```bash
tensor([[0.5403, 0.5403, 0.5403, 0.5403, 0.5403],
        [0.5403, 0.5403, 0.5403, 0.5403, 0.5403],
        [0.5403, 0.5403, 0.5403, 0.5403, 0.5403],
        [0.5403, 0.5403, 0.5403, 0.5403, 0.5403]])
tensor([[0.5403, 0.5403, 0.5403, 0.5403, 0.5403],
        [0.5403, 0.5403, 0.5403, 0.5403, 0.5403],
        [0.5403, 0.5403, 0.5403, 0.5403, 0.5403],
        [0.5403, 0.5403, 0.5403, 0.5403, 0.5403]])
<class 'torch.Tensor'>
<class 'torch.Tensor'>
```

---

## 6.神经网络nn

以最早的卷积神经网络 **`LeNet`** 为例

![LeNet](./LeNet.png)

```py
import torch as t
from torch.autograd import Variable
import torch.nn as nn
import torch.nn.functional as F


# 1.Define LetNet
class LeNet(nn.Module):
    def __init__(self):
        # nn.Module's subclass LeNet must run superclass's constructor
        # equalts `nn.Module.__init__(self)`
        super(LeNet, self).__init__()
        # Convolution layer: input-channels, output, kernel 5*5
        self.conv1 = nn.Conv2d(1, 6, 5)
        self.conv2 = nn.Conv2d(6, 16, 5)
        # Full connection layer：y = Wx + b
        self.fc1 = nn.Linear(16 * 5 * 5, 120)
        self.fc2 = nn.Linear(120, 84)
        self.fc3 = nn.Linear(84, 10)

    def forward(self, x):
        # (convolution -> activation -> pooling/subsampling) * 2
        x = F.max_pool2d(F.relu(self.conv1(x)), (2, 2))
        x = F.max_pool2d(F.relu(self.conv2(x)), 2)
        # reshape, '-1' means self-adpated
        x = x.view(x.size(0), -1)
        # (full connection -> activation) * 2 -> full connection
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        x = self.fc3(x)
        return x


# 2.Some useless operation except `net = LeNet()`
net = LeNet()
print(net)

params = list(net.parameters())
print(len(params))

for name, parameters in net.named_parameters():
    print(name, ':', parameters.size())


# 3.Define Inputs, Run LeNet, Define Targets, Calculate Loss
# Inputs:
#   Variable can autograd, Tensor can't
#   Only mini-batches are supported by torch.nn, 
#   so shape is mSamples x nChannels x Height x Width.
# Loss:
#   nn.MSELoss, nn.CrossEntropyLoss & etc.
inputs = Variable(t.randn(1, 1, 32, 32))
outputs = net(inputs).squeeze()
targets = Variable(t.arange(0, 10)).float()
criterion = nn.MSELoss()
loss = criterion(outputs, targets)
print(loss)


# 4.Clean grad, BP(auto grad), Update params using SGD
net.zero_grad()
print('Grad of conv1.bias before BP:\n', net.conv1.bias.grad)
loss.backward()
print('Grad of conv1.bias after BP:\n', net.conv1.bias.grad)
print(loss.grad_fn)
learn_rate = 0.01
for param in net.parameters():
    param.data.sub_(param.grad.data * learn_rate)
```

OUTPUT

```bash
LeNet(
  (conv1): Conv2d(1, 6, kernel_size=(5, 5), stride=(1, 1))
  (conv2): Conv2d(6, 16, kernel_size=(5, 5), stride=(1, 1))
  (fc1): Linear(in_features=400, out_features=120, bias=True)
  (fc2): Linear(in_features=120, out_features=84, bias=True)
  (fc3): Linear(in_features=84, out_features=10, bias=True)
)
10
conv1.weight : torch.Size([6, 1, 5, 5])
conv1.bias : torch.Size([6])
conv2.weight : torch.Size([16, 6, 5, 5])
conv2.bias : torch.Size([16])
fc1.weight : torch.Size([120, 400])
fc1.bias : torch.Size([120])
fc2.weight : torch.Size([84, 120])
fc2.bias : torch.Size([84])
fc3.weight : torch.Size([10, 84])
fc3.bias : torch.Size([10])
tensor(28.2911, grad_fn=<MseLossBackward>)
Grad of conv1.bias before BP:
 None
Grad of conv1.bias after BP:
 tensor([ 0.0057, -0.0090, -0.0085, -0.0139,  0.0416, -0.0045])
<MseLossBackward object at 0x0000025CFAB71A90>
```

使用优化器：

```py
import torch as t
from torch.autograd import Variable
import torch.nn as nn
import torch.nn.functional as F
import torch.optim as optim


# 1.Define LetNet
class LeNet(nn.Module):
    def __init__(self):
        super(LeNet, self).__init__()
        self.conv1 = nn.Conv2d(1, 6, 5)
        self.conv2 = nn.Conv2d(6, 16, 5)
        self.fc1 = nn.Linear(16 * 5 * 5, 120)
        self.fc2 = nn.Linear(120, 84)
        self.fc3 = nn.Linear(84, 10)

    def forward(self, x):
        x = F.max_pool2d(F.relu(self.conv1(x)), (2, 2))
        x = F.max_pool2d(F.relu(self.conv2(x)), 2)
        x = x.view(x.size(0), -1)
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        x = self.fc3(x)
        return x


# 3.Initialize net as LetNet, Define Optimizer, Clean grad, 
# Define Inputs, Run LeNet(squeeze [1,10] to [10]),
# Define Targets(to float), Calculate Loss,  
# loss BP(auto grad), Update params using optimizer
net = LeNet()
optimizer = optim.SGD(net.parameters(), lr=0.01)
optimizer.zero_grad()
inputs = Variable(t.randn(1, 1, 32, 32))
outputs = net(inputs).squeeze()
targets = Variable(t.arange(0, 10)).float()
criterion = nn.MSELoss()
loss = criterion(outputs, targets)
loss.backward()
optimizer.step()
```

---

## 7.牛刀小试：CIFAR-10分类

加载数据 -> 定义网络 -> 输入数据 -> 前向传播+反向传播 -> 更新参数