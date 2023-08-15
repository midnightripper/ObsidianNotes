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
