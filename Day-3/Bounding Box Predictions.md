Issue with previous ideas is you don't get most accurate bounding box predictions with sliding windows.

YOLO Algorithm
![[Pasted image 20230815144031.png]]
For each vector 3x3 position there is 8 layer 

**YOLO Implementation:** YOLO, which stands for "You Only Look Once," is a popular object detection algorithm used in computer vision. It's designed to rapidly and accurately identify objects within images or videos. The YOLO algorithm divides the input image into a grid and predicts bounding boxes and class probabilities for objects present in each grid cell.
You also don't implement this convolution 9 times rather we use convolution for that.

**IOU (Intersection over Union):**

IOU, which stands for Intersection over Union, is a common evaluation metric used in object detection and image segmentation tasks. It quantifies the overlap between a predicted bounding box or segmented region and a ground truth bounding box or region of interest. IOU is particularly useful for measuring the accuracy of object detection algorithms.

The formula for calculating IOU is:
![[Pasted image 20230815155105.png]]
Non-Max Suppression
There can be multiple detection done in the detection so how do you only detect one object one time only?
Here comes you guessed it!
So it first detects the largest probability rectangles and those others are suppressed. 
![[Pasted image 20230815230437.png]]


Anchor Boxes:
So what if ther are 2 objects and the mid point is same
Then we use 2 anchor boxes one is horizonatal rectangle and the other is vertical rectangle
![[Pasted image 20230815232730.png]]


Region Proposal:

**Semantic Segmentation:**
Semantic segmentation is a computer vision task that involves categorizing each pixel in an image into a specific class or category. Unlike object detection, which identifies and localizes objects within an image, semantic segmentation focuses on pixel-level labeling without distinguishing individual instances of objects.

In semantic segmentation, the goal is to assign a semantic label to each pixel, indicating the class or category to which it belongs. This results in a detailed and dense understanding of the content in the image, highlighting regions of interest and their semantic significance.
![[Pasted image 20230816002639.png]]

Transpose Convolution:
Motivation: How do you make a 2x2 convolution into 4x4 convolution this lets you do that.
![[Pasted image 20230816003024.png]]
![[Pasted image 20230816003645.png]]

U-Net Architecture Implementations:
Intuition of how U-Net works:
![[Pasted image 20230816004130.png]]
![[Pasted image 20230816004423.png]]

So here in the first line the thin line represents height as size
and width as channels
