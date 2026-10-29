# EXP-1 Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** SIVAPRASATH B
- **Register Number:** 212225230268

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python

import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread('Eagle_in_Flight.jpg', 0)


```

#### 2. Print the image width, height & Channel.
```python
h, w = img.shape
print("Width:", w, "Height:", h, "Channels: 1")
```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img, cmap='gray')
plt.show()

```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
cv2.imwrite('Eagle_in_Flight.jpg', img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
color = cv2.imread('Eagle_in_Flight.jpg')
color = cv2.cvtColor(color, cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
print("Color image shape:", color.shape)
plt.imshow(color)
plt.show()

```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
crop = color[100:400, 100:400]

```

#### 8. Resize the image up by a factor of 2x.
```python
resize = cv2.resize(crop, None, fx=2, fy=2)
```

#### 9. Flip the cropped/resized image horizontally.
```python
flip = cv2.flip(resize, 1)
plt.imshow(flip)
plt.show()

```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
apollo = cv2.imread('Apollo-11-launch.jpg')
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
h, w = apollo.shape[:2]
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN
size = cv2.getTextSize(text, font_face, 1, 1)[0]
x = (w - size[0]) // 2
cv2.putText(apollo, text, (x, h-20), font_face, 1,
            (255, 255, 255), 2)
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
cv2.rectangle(apollo, (100, 50), (400, h-50), (255, 0, 255), 2)
```

#### 13. Display the final annotated image.
```python
plt.imshow(cv2.cvtColor(apollo, cv2.COLOR_BGR2RGB))
plt.show()

```

#### 14. Read the image ('Boy.jpg').
```python
img = cv2.imread('Boy.png')
```

#### 15. Adjust the brightness of the image.
```python
matrix_ones = np.ones(img.shape, dtype=np.float64) * 50
matrix = matrix_ones.astype(np.uint8)
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img, matrix)
img_darker = cv2.subtract(img, matrix)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
for x in [img, img_darker, img_brighter]:
    plt.imshow(cv2.cvtColor(x, cv2.COLOR_BGR2RGB))
    plt.axis('off')
    plt.show()
```

#### 18. Modify the image contrast.
```python
matrix1 = np.ones(img.shape, dtype=np.float64) * 1.1
matrix2 = np.ones(img.shape, dtype=np.float64) * 1.2
img_higher1 = cv2.multiply(img.astype(np.float64), matrix1)
img_higher2 = cv2.multiply(img.astype(np.float64), matrix2)
img_higher1 = np.clip(img_higher1, 0, 255).astype(np.uint8)
img_higher2 = np.clip(img_higher2, 0, 255).astype(np.uint8)
img_lower = cv2.convertScaleAbs(img, alpha=0.8)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
for x in [img, img_lower, img_higher1, img_higher2]:
    plt.imshow(cv2.cvtColor(x, cv2.COLOR_BGR2RGB))
    plt.axis('off')
    plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
B, G, R = cv2.split(img)
for x in [B, G, R]:
    plt.imshow(x, cmap='gray')
    plt.axis('off')
    plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```python
merged_rgb = cv2.merge([R, G, B])
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis('off')
plt.show()

```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
H, S, V = cv2.split(hsv)
for x in [H, S, V]:
    plt.imshow(x, cmap='gray')
    plt.axis('off')
    plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```python
merged_hsv = cv2.merge([H, S, V])
merged_rgb = cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB)
plt.imshow(merged_rgb)
plt.title("Merged HSV Image")
plt.axis('off')
plt.show()
```

## Output:

<img width="427" height="815" alt="image" src="https://github.com/user-attachments/assets/6fcef55c-64a5-4afe-82d7-ed164c4a1236" />

<img width="680" height="692" alt="image" src="https://github.com/user-attachments/assets/5900db6a-0e98-46dd-9af3-196ea7b92263" />

<img width="482" height="727" alt="image" src="https://github.com/user-attachments/assets/029a03b5-b6b7-4767-a5a9-9aca0e1f1287" />

<img width="360" height="700" alt="image" src="https://github.com/user-attachments/assets/18f30aa3-dc44-468f-ada9-998519f175b9" />

<img width="372" height="358" alt="image" src="https://github.com/user-attachments/assets/77beb635-ebf8-4898-8f43-a414ffda26ed" />

<img width="316" height="360" alt="image" src="https://github.com/user-attachments/assets/493b1ec2-c26c-4fe7-ad94-bdf292a77213" />

<img width="367" height="697" alt="image" src="https://github.com/user-attachments/assets/db47d213-0148-4f82-a3e9-e3d34842e948" />

<img width="271" height="387" alt="image" src="https://github.com/user-attachments/assets/3b0ab664-48f2-4dcb-8864-3eb5c2ec9258" />

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
