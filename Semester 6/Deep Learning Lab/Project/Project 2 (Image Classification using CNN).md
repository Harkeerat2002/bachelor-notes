# Question 1:
## Question 1.1:
- [x] Load the data
- [x] Observe at least one image per class
- [x] Make a histogram of the distribution of the images of the training and test set

## Question 1.2:
- In PyTorch, the dimensions of a tensor often have the following meanings, especially when dealing with images:

	- The first dimension (4) is the batch size. This is the number of samples that are processed simultaneously.
	- The second dimension (3) is the number of channels. For color images, this is typically 3 (red, green, blue).
	- The third dimension (32) is the height of the image in pixels.
	- The fourth dimension (32) is the width of the image in pixels.
	
	So, a tensor of size `torch.Size([4, 3, 32, 32])` represents a batch of 4 color images, each of size 32x32 pixels.
	
	Next steps:	
	1. Confirm if the dimensions of your tensor align with this interpretation.
	2. If not, adjust your data processing accordingly.
	3. Continue with your model training.