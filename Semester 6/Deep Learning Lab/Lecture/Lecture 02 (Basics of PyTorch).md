# Data
- **Define** the task and collect **suitable data**.
- Collect some basic info on your data *before* starting the learning process (number of classes, density of each class, ...)
- **How much Data is Enough?**
	- "*10 times rule of thumb*": The amount of input data (i.e., the number of examples) should be ten times more than the number of parameters in your data set.
	- If we distinguish cat images from images of dogs based on 1000 parameters, you need 10000 pictures to train the model.
## Data Augmentation
- Expand the number of items in the training set
- Allows the model to less rely on certain *positional* attributes
- Not recommended during tests

# Code Blocks
## Tensors on GPU:
```python
a = torch.randint(0, 10, (2, 3), device='cpu')
> print("Starting device: ", a.device)
Starting device: CPU
> # Move it to GPU after checking availability
> print("Is GPU available?", torch.cuda.is_available())
Is GPU available? True
> # General framework when you want to use GPUs with torch
> device = torch.device('cuda:0' if torch.cuda.is_available() else "cpu")
> b = a.to(device)
> print("Finally, we have it on", b.device)
Finally, we have it on cuda:0
```
## Automatic Differentiation:
```python
> x = torch.tensor(2, requires_grad=True,
dtype=torch.float32)
> y = torch.tensor(3, requires_grad=True,
dtype=torch.float32)
> z = x * x + y
> z.backward()
> print(x.grad)
> print(y.grad)
tensor(4.)
tensor(1.)
```