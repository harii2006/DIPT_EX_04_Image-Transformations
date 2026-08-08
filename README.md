# DIPT_EX_04_Image-Transformations
# Name : SHRIHARI M
# Reg.No : 212225230265
### Aim
To perform image transformations such as Translation, Scaling, Shearing, Reflection, Rotation, and Cropping using OpenCV and Python.

### 
```Software Required
Anaconda – Python 3.7
OpenCV (cv2) library
NumPy library
```

### ALGORITHMS :
Step 1:
Import the necessary libraries such as cv2 and numpy.

Step 2:
Read the input image using cv2.imread() and display the original image using cv2.imshow().

Step 3:
Perform various geometric transformations:

Translation: Shift the image position using a transformation matrix.
Scaling: Resize the image using cv2.resize().
Shearing: Apply an affine transformation to skew the image.
Reflection: Flip the image using cv2.flip().
Rotation: Rotate the image using cv2.getRotationMatrix2D() and cv2.warpAffine().
Cropping: Slice the image array to extract a specific region.
Step 4:
Display all the transformed images in separate windows using cv2.imshow().

Step 5:
Wait for a key press using cv2.waitKey(0) and then close all OpenCV windows using cv2.destroyAllWindows().

### PROGRAM :
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
# Step 1: Load the image
image = cv2.imread('temple.jpg')  # Load the image from file
# Display the original image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert BGR to RGB for correct display
plt.title("Original Image")  
plt.axis('off')


# Step 2: Image Translation
tx, ty = 100, 50  # Translation factors (shift by 100 pixels horizontally and 50 vertically)
M_translation = np.float32([[1, 0, tx], [0, 1, ty]])  # Translation matrix: 
# [1, 0, tx] - Horizontal shift by tx
# [0, 1, ty] - Vertical shift by ty
translated_image = cv2.warpAffine(image, M_translation, (image.shape[1], image.shape[0]))  
plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))  # Display the translated image
plt.title("Translated Image")  
plt.axis('off')


# Step 3: Image Scaling
fx, fy = 5.0, 2.0  # Scaling factors (1.5x scaling for both width and height)
scaled_image = cv2.resize(image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR)
# resize: Resize the image by scaling factors fx, fy
# INTER_LINEAR: Uses bilinear interpolation for resizing
plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))  # Display the scaled image
plt.title("Scaled Image")  # Set title
plt.axis('off')


# Step 4: Image Shearing
shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])  # Shearing matrix
# The matrix shears the image by a factor of 0.5 in both x and y directions
# [1, 0.5, 0] - Shear along the x-axis (horizontal)
# [0.5, 1, 0] - Shear along the y-axis (vertical)
sheared_image = cv2.warpAffine(image, shear_matrix, (image.shape[1], image.shape[0]))

plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))  # Display the sheared image
plt.title("Sheared Image")  # Set title
plt.axis('off')



# Step 5: Image Reflection
reflected_image = cv2.flip(image, 2)  # Flip the image horizontally (1 means horizontal flip)
# flip: 1 means horizontal flip, 0 would be vertical flip, -1 would flip both axes

plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))  # Display the reflected image
plt.title("Reflected Image")  # Set title
plt.axis('off')


# Step 6: Image Rotation
(height, width) = image.shape[:2]  # Get the image height and width
angle = 45  # Rotation angle in degrees (rotate by 45 degrees)
center = (width // 2, height // 2)  # Set the center of rotation to the image center
M_rotation = cv2.getRotationMatrix2D(center, angle, 1)  # Get the rotation matrix
# getRotationMatrix2D: Takes the center of rotation, angle, and scale factor (1 means no scaling)
rotated_image = cv2.warpAffine(image, M_rotation, (width, height))  # Apply rotation

plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))  # Display the rotated image
plt.title("Rotated Image")  # Set title
plt.axis('off')


# Step 7: Image Cropping
x, y, w, h = 100, 100, 200, 150  # Define the top-left corner (x, y) and the width (w) and height (h) of the crop
# Cropping the image from coordinates (x, y) to (x+w, y+h)
cropped_image = image[y:y+h, x:x+w]
# The crop is performed by slicing the image array in the y and x directions

plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))  # Display the cropped image
plt.title("Cropped Image")  # Set title
plt.axis('off')
```
### OUTPUT:
<img width="563" height="342" alt="image" src="https://github.com/user-attachments/assets/9cdb15d2-7ebc-4a99-957a-c01a36211751" />

<img width="576" height="336" alt="image" src="https://github.com/user-attachments/assets/d7c144de-d4f9-434a-a6f2-052123c0f0a0" />

<img width="551" height="177" alt="image" src="https://github.com/user-attachments/assets/ef452a18-cb91-43a6-9d1e-a52dacc7c635" />

<img width="552" height="343" alt="image" src="https://github.com/user-attachments/assets/b604a121-6320-4214-ad9d-527c44b05b41" />

<img width="562" height="350" alt="image" src="https://github.com/user-attachments/assets/6a5cd898-4701-40e8-8da4-84672cf09eba" />

<img width="560" height="348" alt="image" src="https://github.com/user-attachments/assets/f36f9dc7-f94b-440e-9bf7-2fd73da63ead" />

### RESULT:
Thus, we successfully performed image transformations such as Translation, Scaling, Shearing, Reflection, Rotation, and Cropping using OpenCV and Python.
