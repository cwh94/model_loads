**model_loads** is an open-source Python package for pytorch load models easy.

[PyTorch](http://pytorch.org/) is a Python package that provides two high-level features:

- Tensor computation (like NumPy) with strong GPU acceleration
- Deep neural networks built on a tape-based autograd system

It's annoying to load cpu model to gpu devices or load multi-gpus trained model to single gpu devices sometimes, And this package try to simplify it.


## Table of Contents

- [Table of Contents](#table-of-contents) 
- [Installation](#installation)
- [Getting Started](#getting-started)
- [TODO list](#todo-list)

## Installation

To install load_models, you can do as follow:

```
    pip install model-loads
```

Or from source

```
    git clone https://github.com/cwh94/model_loads.git
    cd load_models
    python setup.py bdist_egg
    python setup.py install
```

## Getting Started


1. load pth model to GPU device
```
import model_loads as lo
import torchvision.models as models

model = models.MobileNetV2()
model_path = "../examples/models/pth/mobilenet_v2-b0353104.pth"
model, _ = lo.load_models(model_path, model, use_gpu=True)
print(model)
print(type(model))
```

2. load tar model(which contains state_dict and optimization info or accuracy) to CPU device

```
from models.tar.mobilenet_v2 import MobileNetV2

model = MobileNetV2()
model_path = "models/tar/checkpoint.pth.tar"

model, other_param = lo.load_models(model_path, model)
print(model)
print(other_param)

```

4. load model to CPU device
```
import os

os.environ["CUDA_VISIBLE_DEVICES"] = ""

model = models.MobileNetV2()
model_path = "models/pth/mobilenet_v2-b0353104.pth"
model, _ = lo.load_models(model_path, model, use_gpu=True)
print(model)
print(type(model))
```




Done:

load model which save model by 

```
torch.save(model, "path/to/model")
```

## Todo list

DATA PARALLELISM
