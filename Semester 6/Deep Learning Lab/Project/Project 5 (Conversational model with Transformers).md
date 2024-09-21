# Things to keep in Mind:
- [ ] **Data Modifications:**
	- [ ] Search for Duplicates & Missing Values / inconsistencies
	- [ ] Make sure to understand 
		- [ ] Distribution Data
		- [ ] Where the outliers are - do I want to cut them off
		- [ ] If some classes are "harder" to detected from others
- [ ] Prefer Starting with state-of-art models (pre-trained, if needed)
- [ ] **Model parameter Initialization:** Default Random initialization, with numbers drawn from a range that is computed according to the input and output dimension
	```python
	# Uniform
	torch.nn.init.uniform_(tensor, a=0.0, b=1.0)
	# Normal
	torch.nn.init.normal_(tensor, mean=0.0, std=1.0)
	```
- [ ] **Xavier Normalization:**
	- [ ] Initial weights too small, shrink close to 0, no more useful
	- [ ] Initial weights too large, the signal becomes bigger
	- [ ] Xavier normalization enforces the weights to be of the “right size”
	- [ ] In general: used for layers that utilize sigmoid and tanh activation functions
- [ ] **Learning Rate:**
	- [ ] Change the learning rate while training
	- [ ] `torch.optim.lr_scheduler` provides several methods to adjust the learning rate based on the number of epochs.
	- [ ] Better to use it on the validation set, but it works also in the training
- [ ] **Schedulers:**
	```python
	optimizer = optim.SGD(model.parameters(), lr=0.01)
	scheduler = ExponentialLR(optimizer, gamma=0.9)
	
	for epoch in range(20):
		for input, target in the dataset:
			optimizer.zero_grad()
			output = model(input)
			loss = loss_fn(output, target)
			loss.backward()
			optimizer.step()
			scheduler.step()
	```
# Resources:
- [PyTorch Guide](https://pytorch.org/tutorials/beginner/chatbot_tutorial.html?highlight=chatbot%20tutorial) 
- [GitHub Repo](https://github.com/Currie32/Chatbot-from-Movie-Dialogue/blob/master/Chatbot_Attention.ipynb)