## What is PyTorch?

PyTorch is an open-source machine learning framework developed by Facebook's AI Research lab. It provides a flexible and dynamic computational graph, making it easier to build and train deep learning models. PyTorch is widely used for tasks such as computer vision, natural language processing, and reinforcement learning. Its intuitive design and strong community support make it a popular choice among researchers and developers.


## Main Modules of PyTorch

PyTorch is composed of several key modules that provide the building blocks for creating and training machine learning models:

1. **torch**: The core module that provides multi-dimensional arrays (tensors) and mathematical operations on them. It is the foundation of PyTorch.

2. **torch.nn**: A module that provides tools for building neural networks, including layers, loss functions, and activation functions.

3. **torch.optim**: A module that contains optimization algorithms like SGD, Adam, and RMSprop, which are used to update model parameters during training.

4. **torch.utils.data**: A module for handling datasets and data loading. It provides utilities like `DataLoader` and `Dataset` to simplify data preprocessing and batching.

5. **torch.autograd**: A module for automatic differentiation, enabling gradient computation for backpropagation. It is essential for training neural networks.

6. **torchvision**: An extension library for computer vision tasks. It includes pre-trained models, image datasets, and utilities for image transformations.

These modules work together to provide a comprehensive and flexible framework for developing machine learning applications.



## Example: Training a Linear Model with Gradient Descent

Below is a simple example of training a linear model to approximate the function \( f(x) = x \cdot w + b \) using PyTorch. The model is trained for 10 iterations using gradient descent.

```python
import torch

# Define the data
x = torch.tensor([[1.0], [2.0], [3.0], [4.0]])
y = torch.tensor([[3.0], [5.0], [7.0], [9.0]])

# Initialize weights and bias
w = torch.tensor([[0.0]], requires_grad=True)
b = torch.tensor([[0.0]], requires_grad=True)

# Define the learning rate
learning_rate = 0.01

# Training loop
for epoch in range(10):
    # Forward pass: compute predictions
    y_pred = x @ w + b

    # Compute the loss (Mean Squared Error)
    loss = ((y_pred - y) ** 2).mean()

    # Backward pass: compute gradients
    loss.backward()

    # Update weights and bias
    with torch.no_grad():
        w -= learning_rate * w.grad
        b -= learning_rate * b.grad

        # Zero the gradients
        w.grad.zero_()
        b.grad.zero_()

    # Print progress
    print(f"Epoch {epoch+1}: Loss = {loss.item():.4f}")

print(f"Trained weight: {w.item():.4f}, Trained bias: {b.item():.4f}")
```

