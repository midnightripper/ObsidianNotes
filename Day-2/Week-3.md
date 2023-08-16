**Object Localization:**

Object localization involves the task of determining the precise location of specific objects within an image or video frame. In simpler terms, it's about teaching computers to recognize where an object is by drawing a bounding box around it. This process enables machines to accurately pinpoint and outline the position of objects in visual data, enhancing their ability to understand and interact with their environment.

![[Pasted image 20230814235556.png]]
**Object Detection:**

Object detection is employed to identify and locate multiple objects within an image or video frame. This task goes beyond simple recognition, as it involves precisely localizing the positions of various objects in the visual data.

**Classification with Localization:**

Classification with localization combines object classification and precise object localization. In addition to determining what objects are present in an image, this approach also provides information about where each object is located within the image, as well as its height and width. This richer level of understanding enhances the ability to recognize objects accurately and ascertain their spatial attributes.

![[Pasted image 20230814235958.png]]
In here we train the neural network to also predict the center point of the object along with the height and width of the object.
![[Pasted image 20230815000211.png]]
Here the output is in the given format and checks if 
1st : There is an image
2nd-5th: Where the image is and the parameters of them.
6th-8th: Classes of the object in the image.
The Loss function
![[Pasted image 20230815000439.png]]
If the Y1 is 0 we don't care about others.

**Landmark Detection:**

Landmark detection is a computer vision technique focused on identifying and pinpointing specific points or landmarks on objects within images or videos. These landmarks serve as crucial reference points or distinctive features that hold significant meaning for the object's interpretation.

Accurate detection and tracking of these landmarks enable computer systems to comprehend the object's structure, location, and movement within the visual data. This technique finds applications across diverse domains, including facial recognition, medical imaging, robotics, and augmented reality. Through landmark detection, precise measurements, object manipulation, and context-aware interactions become achievable, enhancing the depth of understanding and interaction between machines and their visual environment.

![[Pasted image 20230815001440.jpg]]

Object Detection:

Sliding Window detection algorithm
Picking  a small window and slide through the image and check if there is any object in the window and give 0 or 1

Now take a bigger window and then even larger
![[Pasted image 20230815001946.png]]
But doing so many can affect computational cost.

**Sliding Window Detection:**

Sliding window detection is a computer vision technique utilized for object detection in images. This method systematically examines an image using a window of a predetermined size, which is then slid across the entire image at a specified interval.
The primary objective of sliding window detection is to identify objects of interest at various scales and positions within the image. By iteratively scanning the image with different window placements, the technique enhances the likelihood of detecting objects with varying sizes and orientations. This approach serves as a fundamental method for object localization and recognition, allowing for effective detection across a range of scenarios.

**Solution: Transforming FC Layer into Convolutional Layers**

By converting fully connected (FC) layers into convolutional layers, we can leverage a pipeline that facilitates the creation of a final convolutional neural network (CNN) layer. This transformation aids in identifying the spatial positioning of objects within an image.

The pipeline involves integrating convolutional layers that maintain spatial information, enabling the network to capture context and relationships among image features. This approach proves particularly useful for tasks like object localization, as it allows the network to discern where objects are situated in the image while considering their surrounding context.
![[Pasted image 20230815002734.png]]

**Outcome: Obtaining the Final CNN Layer**

Through this process, we derive the ultimate convolutional neural network (CNN) layer, which encapsulates information regarding the object's location within the image.

**Challenge: Suboptimal Bounding Box Positioning**

However, a concern arises regarding the accuracy of the bounding box's placement around the detected object. The current approach might not yield precise positioning of the bounding box, potentially impacting the overall performance of object detection and localization.

Face Verification vs Recognition:
![[Pasted image 20230816210848.png]]

**Face Verification:**

- **Definition:** Face verification is the process of confirming whether two given facial images belong to the same person or not.
- **Task:** It focuses on answering a binary question: "Is the person in Image A the same as the person in Image B?"
- **Use Case:** Commonly used in scenarios where identity needs to be verified, such as unlocking devices, accessing secure areas, or online identity confirmation.
- **Example:** When unlocking a smartphone using facial recognition, the device verifies if the captured face matches the enrolled face.
- **Output:** Either a "match" or "not match" decision is provided.

**Face Recognition:**

- **Definition:** Face recognition involves identifying a person by matching their facial features against a database of known faces.
- **Task:** It aims to determine the identity of a person in an image by comparing it with a set of known faces.
- **Use Case:** Applied in various contexts like surveillance, biometric authentication, and tagging individuals in photos.
- **Example:** Social media platforms use face recognition to suggest names for people in photos based on their facial features.
- **Output:** Provides the identity of the recognized person, often from a predefined list of individuals.

## One shot Learning
If you have very limited data to train on then you can't practically train a model every time you get new person added or with such little data what  should you do?
![[Pasted image 20230817014117.png]]
One-shot learning is a machine learning paradigm that focuses on training models to recognize new objects or classes with very limited training examples, often just a single example per class. In traditional machine learning, models require a substantial amount of data to generalize effectively. However, in real-world scenarios, obtaining a large dataset for every new class might be impractical or time-consuming.

SIAMESE NETWORK

![[Pasted image 20230817014836.png]]
![[Pasted image 20230817014923.png]]

TRIPLET LOSS:
![[Pasted image 20230817015749.png]]
![[Pasted image 20230817015949.png]]
![[Pasted image 20230817021256.png]]
