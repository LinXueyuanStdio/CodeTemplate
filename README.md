# CodeFileStructTemplate代码文件组织结构模板

For laziness, run the comment below:
```shell
echo "alias newtemp='git clone git@github.com:LinXueyuanStdio/CodeFilesTemplate.git'" > ~/.bashrc
```

Then you can just run `newtemp` to create a great file structure.

Remember to `rename directory name` or `copy to another directory`.

# tree
.
├── checkpoints
├── config.py
├── data
│   ├── dataset.py
│   ├── get_data.sh
│   └── __init__.py
├── main.py
├── models
│   ├── AlexNet.py
│   ├── BasicModule.py
│   └── __init__.py
├── README.md
├── requirements.txt
└── utils
    ├── __init__.py
    └── visualize.py

# doc

checkpoints/： 用于保存训练好的模型，可使程序在异常退出后仍能重新载入模型，恢复训练
data/：数据相关操作，包括数据预处理、dataset实现等
models/：模型定义，可以有多个模型，例如上面的AlexNet和ResNet34，一个模型对应一个文件
utils/：可能用到的工具函数，在本次实验中主要是封装了可视化工具
config.py：配置文件，所有可配置的变量都集中在此，并提供默认值
main.py：主文件，训练和测试程序的入口，可通过不同的命令来指定不同的操作和参数
requirements.txt：程序依赖的第三方库
README.md：提供程序的必要说明

# __init__.py

可以看到，几乎每个文件夹下都有__init__.py，一个目录如果包含了__init__.py 文件，那么它就变成了一个包（package）。
__init__.py可以为空，也可以定义包的属性和方法，但其必须存在，其它程序才能从这个目录中导入相应的模块或函数。

例如在data/文件夹下有__init__.py，则在main.py 中就可以
```python
from data.dataset import DogCat
```
而如果在data/__init__.py中写入
```python
from .dataset import DogCat
```
则在main.py中就可以直接写为：
```python
from data import DogCat
```
或者
```python
import data;
dataset = data.DogCat
```
相比于from data.dataset import DogCat更加便捷。


