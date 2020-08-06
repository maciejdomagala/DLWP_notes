# Deep Learning with PyTorch

Source: [https://pytorch.org/assets/deep-learning/Deep-Learning-with-PyTorch.pdf](https://pytorch.org/assets/deep-learning/Deep-Learning-with-PyTorch.pdf)

Notes made while reading the book. Starting from chapter 5. Code for examples and tests made in Jupyter.

## To do:

- [ ]  Go through the book from chapter 5 (page 100) to the chapter 15 (page 480). 
Going through 380 pages, doing ~30 pages daily → ~2 weeks.

## Chapter 5

Code in the Jupyter Notebook for exercises/examples: link here.

- 110 - L1 vs L2 metric for error (MSE)
- 111 - torch.ones(()), using size, shape, type functions, broadcasting (more on broadcasting semantics: [https://pytorch.org/docs/stable/notes/broadcasting.html](https://pytorch.org/docs/stable/notes/broadcasting.html), examples in Jupyter).
- 113 - idea of a gradient descent, rate of change of the function (ROC) formula
- 114 - why the analytically calcuated gradient is better then calculating ROC for discrete values
- 118 - overtraining with too big learning rate problem
- 119 - input normalization, problem of having parameters of different scale

having different learning rates for different parameters is not a good option, becomes redundant as the model scales up. always normalize the inputs.

- 123 - using autograd functionality

calling backward on a function accumulates the gradient. after updating parameters use **params.grad.zero_()** to set the gradient to 0 before next iteration of gradient calculating.

usage of **torch.no_grad()**: it stops tracing the grad changes. used when updating the parameters, since grad would track that in-place change being made.
another way of doing that: creating a copy of a tensor using the **tensor.detach()** functionality (also removes the grad tracking).
also **torch.set_grad_enabled()** which takes boolean value could be used

- 127 - adding the optimizers, torch.optim

optimizers have two primary methods: **zero_grad** and **step.** when constructing optimizer, we are passing the parameters inside. the **zero_grad** will zero the grad for these parameters. **step** method is updating the value of the parameters (we don't have to change the values of parameters after backward pass in place anymore)

- 130 - ADAM optimizer

ADAM is a lot less sensitive to the scale of the parameters than SGD. it has the adaptive learning rate property.

- 131 - train/test/valid dataset separation, overfitting

if the training loss and validation loss are diverge with the training going forward, it means we are overfitting. the model is fitting too well to the training data and therefore it's not generalizing well

ways to prevent overfitting:
1. using more data (more samples for model to learn → statistically better generalizing)
2. using regularization methods - penalizing big differences between the prediction and ground truths. this makes sure that the model will be as regular in-between the training data.
3. using data augmentation - providing more training samples by manipulation of already existing data (adding noise, translations etc.)
4. making the model simpler - having less parameters → a bit worse fit to the data → less error during prediction on new data
usual way of performing the neural network fitting in two steps:
1. make it bigger until it fits the data
2. scale it down so it prevents overfitting.

- 134 - splitting a dataset

**torch.randperm()** is shuffling the tensor indices

### Log:

Starting on August, 6. 

Deadline - August, 20.

- August 6: pages 100 - 140
-