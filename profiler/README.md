# pytorch-profiler
Computes #parameters and #ops for a given network.

> Will ignore layers that have not been implemeneted yet.

```
usage: profile.py [-h] [--batch-size BATCH_SIZE]
                  model input_size [input_size ...]

pytorch model profiler

positional arguments:
  model                 model to profile
  input_size            input size to network without batch

optional arguments:
  -h, --help            show this help message and exit
  --batch-size BATCH_SIZE
                        batch size to compute ops for
```

If you want to profile model with custom layers, you can implement a ```count_<layer>``` function like in ```profile.py``` and write a tiny script like following:

```
from profile import profile

model = <load / instantiate your model>

custom_ops = { '<your_layer_name' : '<your_custom_count_layer_function>', ... }

num_ops, num_params = profile(model, batch_size, input_size, custom_ops)
```