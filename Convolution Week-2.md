We can always get inspired from others ideas like cnn implementations if they are very good at it you can use their models to help in edge detection etc.

Research papers could be read and be able to understand

Outline
Classic networks: The old ones
ResNet(152 layers)
Inception neural network case study

Case Studies
LeNet-5
32x32x1 let it be handwritten digits
![[Pasted image 20230813152430.png]]
and so on as per the image

ALEXNET
Questions i got ?
1)what happens in a same convolution?
In a "same" convolution, the input data is padded in such a way that the output has the same spatial dimensions as the input. This is achieved by adding zeros around the input data before applying the convolution operation

2)why do people prefer max over avg pooling?
People often prefer max pooling over average pooling in tasks like image recognition because max pooling focuses on the most important features in each region, making the model more resilient to small changes and preserving spatial hierarchies. It also introduces useful non-linearities, allows for efficient computations, and retains large values that might be significant. While both have their uses, max pooling is favored for its ability to capture distinctive features and patterns effectively.

Average pooling is helpful when you want to reduce noise, smooth data, and maintain a general sense of information. It's useful for downsampling large datasets, stabilizing representations with outliers, and tasks where gradual changes matter more than sharp features.