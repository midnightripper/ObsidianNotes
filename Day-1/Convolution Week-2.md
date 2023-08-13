We can learn from well-done CNN setups and use their models for tasks like spotting edges. This can be a great way to enhance our work.

Research papers could be read and be able to understand

### Classic Networks: The Early Ones
Discussing older network architectures.

### ResNet (152 layers)
Exploring the ResNet architecture with 152 layers.
### Inception Neural Network Case Study
Taking a closer look at the Inception neural network.
## Case Studies

### LeNet-5
Focusing on the LeNet-5 architecture.
- Input: 32x32x1 for handwritten digits.
- Further details following the image.
![[Pasted image 20230813152430.png]]


**ALEXNET**

**Questions and Answers:**

1. **What happens in a "same" convolution?**
    
    In a "same" convolution, the input data is padded in a way that ensures the output retains the same spatial dimensions as the input. This padding involves adding zeros around the input data before performing the convolution operation. This maintains the size of the input data while allowing convolutional operations to be applied effectively.
    ![[1_1okwhewf5KCtIPaFib4XaA.gif]]
2. **Why is max pooling preferred over average pooling?**
    
    Max pooling is often favored over average pooling in tasks like image recognition for several reasons. Max pooling focuses on extracting the most significant features within each region, which helps the model become more resistant to minor variations and preserves spatial relationships. It introduces non-linearities that capture distinctive patterns effectively. Additionally, max pooling is computationally efficient and retains large values that may hold essential information.
    
    On the other hand, average pooling is valuable when the goal is noise reduction, data smoothing, and maintaining a general sense of information. It's suitable for downsampling large datasets, stabilizing representations in the presence of outliers, and scenarios where gradual changes are more important than sharp features. Both max pooling and average pooling have their specific use cases, but max pooling's ability to capture important features makes it a popular choice for many image-related tasks.
![[Pasted image 20230813231607.png]]

**AlexNet: Purpose and Same Convolutions**

AlexNet is a neural network architecture that gained prominence for its success in the ImageNet Large Scale Visual Recognition Challenge. It utilizes "same" convolutions to maintain spatial relationships and capture detailed features effectively. The use of same convolutions helps preserve context and prevents information loss during the convolution process.

**Types of Padding in Convolutional Neural Networks**

1. **Valid Padding**: This type of padding involves no additional padding to the input data. As a result, the output dimensions are smaller than the input dimensions. Valid padding is suitable when maintaining spatial dimensions is not a priority, making it useful for deep layers in a network where detailed context might not be crucial.
    
2. **Same Padding**: Same padding involves adding zeros around the input data to ensure that the output dimensions remain the same as the input dimensions. It is used to maintain spatial relationships and context of features. Same padding is particularly beneficial in tasks like image recognition where the preservation of object parts and accurate feature extraction are important.
    
3. **Full Padding**: Full padding is less commonly used due to its tendency to generate larger output dimensions. It involves adding padding to the input data to accommodate the complete application of the filter. Full padding is utilized when retaining every possible part of the input data in the convolution operation is essential. This might be the case in certain tasks like edge detection or signal processing where all available information needs to be considered.

The term "edge" here refers to the outer boundary of the image.

![[Pasted image 20230813160909.png]]
  
Sure, here's your provided information formatted and organized in a concise manner for your class notes:

---

**AlexNet Architecture Layers:**

1. **Layer 1 - Convolution and Activation**:
    - 96 filters, size 11x11, stride 4.
    - ReLU activation.
2. **Layer 2 - Max Pooling**:
    - 3x3 kernel, stride 2 for downsampling.
3. **Layer 3 - Convolution and Activation**:
    - 256 filters, size 5x5.
    - ReLU activation.
4. **Layer 4 - Max Pooling**:
    - 3x3 kernel, stride 2 for downsampling.
5. **Layer 5 - Convolution and Activation**:
    - 384 filters, size 3x3.
    - ReLU activation.
6. **Layer 6 - Convolution and Activation**:
    - 384 filters, size 3x3.
    - ReLU activation.
7. **Layer 7 - Convolution and Activation**:
    - 256 filters, size 3x3.
    - ReLU activation.
8. **Layer 8 - Max Pooling**:
    - 3x3 kernel, stride 2 for downsampling.
9. **Layer 9 - Fully Connected and Dropout**:
    - Two fully connected layers, each with 4096 neurons.
    - Dropout applied.
10. **Layer 10 - Fully Connected and Dropout**:
    - One fully connected layer with 1000 neurons (class count).
    - Dropout applied.
11. **Layer 11 - Output Layer**:
    - Output layer with softmax activation for class probabilities.

**Q/A: Understanding Convolutional Network Layers and Filters**

**Q1: What do the initial and later layers in a convolutional network capture, using a human face detector as an example?**

**Initial Layers:** These layers capture basic features like edges, corners, and textures in a human face. For a human face detector, the initial layers might detect simple contours and color variations that form the foundation of more complex features.

**Intermediate Layers:** These layers build upon the initial features to recognize facial parts such as eyes, nose, and mouth. By combining the basic features, these layers understand the spatial relationships and structure of these parts in relation to each other.

**Later Layers:** In the context of a human face detector, the later layers identify complete faces, facial expressions, and even unique identities. They consider the overall context, positioning of facial parts, and lighting conditions to make accurate predictions.

**Q2: What can each filter capture in a convolutional layer?**

Each filter in a convolutional layer of a neural network can capture specific features and patterns present in the input data. These features include edges, textures, colors, corners, and object parts. As the network's layers deepen, filters become capable of recognizing higher-level features, such as entire objects or complex arrangements of elements. In essence, each filter learns to detect different visual elements within the data, enabling the network to understand progressively intricate aspects of the input.

VGG-16 Network
![[Pasted image 20230813164800.png]]
**VGG16 (Visual Geometry Group 16)** is a convolutional neural network architecture known for its depth and simplicity. It was developed by the Visual Geometry Group at the University of Oxford. VGG16 consists of 16 weight layers, including 13 convolutional layers and 3 fully connected layers.

**Skip Connections in Residual Networks (ResNets)**

In traditional neural networks, information flows layer by layer sequentially. However, in Residual Networks (ResNets), skip connections are introduced. These connections allow information from layer "l" to directly reach layer "l+2," bypassing intermediate layers. This shortcut enables more direct access to deeper parts of the network.

**Purpose of Skip Connections:** The main purpose is to address challenges that arise when increasing network depth. Ideally, as you add more layers, training error should decrease. However, practical issues like overfitting can hinder this improvement.

**Advantages of Skip Connections:** ResNets leverage skip connections to mitigate the challenges of deep networks. By allowing shortcuts, information can flow directly, aiding in the training process. This is particularly effective for avoiding vanishing gradients, which can occur when gradients become too small during backpropagation through many layers. By introducing these connections, ResNets can be trained deeper without sacrificing performance.

**1x1 Convolution:**

1x1 convolution serves multiple purposes in neural networks:
- **Network Idea:** It's a fundamental component that allows for flexible design choices.
- **Feature Reduction:** It can reduce the number of feature channels in a network layer.
- **Dimensionality Reduction:** Useful for shrinking spatial dimensions without losing information.
- **Increasing Model Expressiveness:** It introduces non-linearity, enhancing model capabilities.

**Inception Network:**

Inception networks use 1x1 convolutions for various reasons:
- **Bottleneck/1x1 Convolution:** This is employed to decrease model complexity.
- **Block with Different Kernels:** Different filters are applied and their outputs concatenated along the channel dimension.
- **Reducing Input Channels:** 1x1 convolutions help trim input channel dimensions, saving computation.

**Inception Module:**

In the inception module:
- **Previous Activation:** Refers to the preceding layer's output.
- **Multiple Filter Sizes:** The module employs filters of various sizes simultaneously.
- **1x1 Convolution Bottleneck:** While 1x1 convolutions speed up computations, the bottleneck effect isn't an issue because it's offset by the parallel processing nature of the inception module.

The Inception network, also known as GoogLeNet, is a deep neural network architecture designed by Google. It's known for using "inception modules," which combine different-sized convolutions and pooling operations in parallel to capture diverse features. This approach helps efficiently recognize complex patterns in images while managing computation. Inception networks were successful in image recognition challenges due to their ability to balance accuracy and efficiency.

MOBILE NET
Normal ones
![[Pasted image 20230813220501.png]]
difference
![[Pasted image 20230813220845.png]]
MobileNetV2
![[Pasted image 20230813222103.png]]
Residual Networks are used in V2 to use the residual network advantages

MobileNetV1 and MobileNetV2 are both efficient neural network architectures for mobile devices. MobileNetV2 improves upon MobileNetV1 by introducing inverted residual blocks, shortcut connections, and bottleneck designs. These enhancements lead to better accuracy and efficiency in MobileNetV2, making it a preferred choice for resource-constrained applications.

**![[Pasted image 20230813222529.png]]


**EfficientNet:**

EfficientNet addresses model efficiency across various aspects like depth, width, and input resolution. It achieves individuality for specific devices by balancing these factors to find the optimal network configuration for performance and resource constraints.

**Transfer Learning:**

Transfer learning involves utilizing pre-existing models and adjusting their output layers to suit your task. This approach is beneficial because you can leverage well-trained models and their learned features. It's advisable to freeze initial layers, ensuring they retain their learned patterns. If you have a substantial dataset, you can unfreeze and fine-tune the transferred layers for improved performance.

**Data Augmentation:**

Data augmentation is a technique to enhance your dataset's diversity and robustness by applying transformations. Common methods include:

- **Mirroring:** Flipping images horizontally, widely used for tasks like object recognition.
- **Random Cropping:** Extracting different random sections of an image to enrich variations.
- **Rotation:** Rotating images at various angles for better generalization.
- **Shearing:** Distorting images by shifting points along one axis, transforming rectangles into trapezoids.
- **Local Warping:** Applying localized distortions to augment specific regions.

![[Screenshot from 2023-08-13 22-48-03.png]]

**Color Shifting:**

Color shifting involves altering the color balance of images by adjusting their color channels. This technique can enhance the dataset's diversity and robustness, allowing models to learn from a wider range of color variations.

**PCA Color Augmentation:**

PCA color augmentation is a method that realistically alters image colors using mathematical techniques. This augmentation enriches the training data by changing colors while maintaining a natural appearance. This technique helps computers better comprehend objects even when presented with different colors. It's akin to providing the computer with varied perspectives to learn from.

**State of Computer Vision:**

The "data engineering vs. hand engineering" dilemma presents a choice for machine learning practitioners during model development. It involves deciding between two approaches:

- **Data Engineering:** Relying on raw data and enabling the model to learn from it directly.
- **Hand Engineering:** Creating and designing features manually based on domain knowledge.

This decision impacts how the model extracts information. Data engineering embraces the power of the data itself, while hand engineering involves crafting features that might be more aligned with specific insights. Balancing these approaches is key to achieving optimal model performance.

![[Pasted image 20230813230327.png]]


**Achieving Good Benchmark Performance for Your Model:**

**Ensembling:** To excel in benchmark performance, consider employing ensembling techniques:

- **Train Independently:** Train multiple networks separately, each capturing different aspects of the data.
- **Average Outputs:** Combine predictions from these networks by averaging their outputs.
- Ensembling helps reduce overfitting and improves generalization, often leading to better benchmark scores.

**Multicrop at Test Time:** Enhance your model's performance during testing by adopting the following technique:

- **Multiple Test Versions:** Run the classifier on various versions of the test images.
- **Average Results:** Average the predictions obtained from these multiple test image versions.
- This approach accounts for variations in image presentation and contributes to more robust predictions.

Utilizing ensembling and multicrop techniques can significantly enhance your model's performance in benchmark settings.
![[Pasted image 20230813230934.png]]

