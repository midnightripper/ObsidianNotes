Object Localization:
Identifying the location of specific objects within an image or video frame.
So in simpler terms it is about teaching computers to recognize where an object is with image drawing the box around it.
![[Pasted image 20230814235556.png]]
Detection is used to detect multiple objects.
Classification with localization can be used for knowing where the object is in the image and height and width of it.
![[Pasted image 20230814235958.png]]
In here we train the neural network to also predict the center point of the object along with the height and width of the object.
![[Pasted image 20230815000211.png]]
Here the output is in the given format and checks if 
1st : There is an image
2nd-5th: Where the image is and the parameters of them.
6th-8th: Classes of the object in the image.
The Loss funtion
![[Pasted image 20230815000439.png]]
If the Y1 is 0 we don't care about others.

LANDMARK DETECTION:
Landmark detection is a computer vision technique that involves identifying and locating specific points or landmarks on objects within images or videos. These landmarks are often key features that hold significant meaning or provide critical information about the object. By accurately detecting and tracking these landmarks, computer systems can understand and analyze the structure, position, and movement of objects in visual data. Landmark detection finds applications in various fields, such as facial recognition, medical imaging, robotics, and augmented reality, enabling precise measurements, object manipulation, and context-aware interactions.

![[Pasted image 20230815001440.jpg]]

Object Detection:

Sliding Window detection algorithm
Picking  a small window and slide through the image and check if there is any object in the window and give 0 or 1

Now take a bigger window and then even larger
![[Pasted image 20230815001946.png]]
But doing so many can affect computational cost.
Sliding window detection is a technique used in computer vision for object detection in images. It involves systematically scanning an image with a window of fixed size and sliding it across the entire image at a specified step size. The goal is to detect objects of interest at different scales and positions within the image.

Solution
Turing FC layer into convolutional layers
So using the pipeline to get a final cnn layer can help us to identiy where the image is lying.
![[Pasted image 20230815002734.png]]
In this we get the final cnn layer  where it contains values about where the object lies.

Issue: Position of bounding box is not going to be good