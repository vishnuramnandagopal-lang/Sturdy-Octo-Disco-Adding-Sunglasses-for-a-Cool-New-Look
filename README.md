# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

## NAME: Vishnuram G N
## REG NO: 212225240187

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

## Features:
- Detects the face in an image.
- Places a stylish sunglass overlay perfectly on the face.
- Works seamlessly with individual passport-size photos.
- Customizable for different sunglasses styles or photo types.

## Technologies Used:
- Python
- OpenCV for image processing
- Numpy for array manipulations

## How to Use:
1. Clone this repository.
2. Add your passport-sized photo to the `images` folder.
3. Run the script to see your "cool" transformation!

## Applications:
- Learning basic image processing techniques.
- Adding flair to your photos for fun.
- Practicing computer vision workflows.

Feel free to fork, contribute, or customize this project for your creative needs!

## Code
```

import cv2
import numpy as np
import matplotlib.pyplot as plt

faceImage = cv2.imread('/content/How To Robert Downey Jr Hairstyle at Ryandreher.jpeg')
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")

```
<img width="375" height="575" alt="421692059-2dd634f5-bb44-469d-b982-136c4636f9cb" src="https://github.com/user-attachments/assets/55762833-cdf9-4ea5-a160-f155ca2529d0" />

```
faceImage.shape
```
<img width="179" height="35" alt="421692403-224cd26b-6ed0-44cc-ae55-f1d3c5d167d9" src="https://github.com/user-attachments/assets/89e7780c-bc36-4959-8eca-55bdf9723cbe" />
```
glassPNG = cv2.imread('/content/584999937b7d4d76317f5ffd (1).png',-1)
plt.imshow(glassPNG[:,:,::-1]);plt.title("glassPNG")
```
<img width="697" height="509" alt="421692859-f790f7f1-258d-45c5-900c-a810328b933d" src="https://github.com/user-attachments/assets/ad2c7a02-f1e1-47a3-8f28-097c635d059f" />

```
glassPNG.shape

```
<img width="149" height="38" alt="421693066-c214ae0f-8ead-4278-bfc9-5fe421f158b1" src="https://github.com/user-attachments/assets/0cc51503-a907-46b2-bfa1-7efb1f8a1dfa" />

```
glassPNG = cv2.resize(glassPNG,(240,150))
print("image Dimension ={}".format(glassPNG.shape))
```
<img width="330" height="45" alt="421693220-e777a615-58e5-4db3-96d8-9d3172c6ee44" src="https://github.com/user-attachments/assets/53a89e42-fe44-4623-89f6-06c129531dff" />

```
glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]

plt.figure(figsize=[16,16])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');

```
<img width="1627" height="526" alt="421693616-bd61b586-69cb-473e-ba1c-e976de7bcd0b" src="https://github.com/user-attachments/assets/618da2bd-dade-4dcd-be48-977f49ca902a" />

```
faceWithGlassesNaive = faceImage.copy()

# Replace the eye region with the sunglass image
faceWithGlassesNaive[205:355,105:345]=glassBGR

plt.imshow(faceWithGlassesNaive[...,::-1])

```
<img width="448" height="556" alt="421693867-b39f012a-a800-4315-9b0a-3dc635b81e0c" src="https://github.com/user-attachments/assets/a67ccac4-e036-473b-ba4b-8119d55ad8b3" />

```
glassMask = cv2.merge((glassMask1,glassMask1,glassMask1))

# Make the values [0,1] since we are using arithmetic operations
glassMask = np.uint8(glassMask/255)

# Make a copy
faceWithGlassesArithmetic = faceImage.copy()

# Get the eye region from the face image
eyeROI= faceWithGlassesArithmetic[205:355,105:345]

# Use the mask to create the masked eye region
maskedEye = cv2.multiply(eyeROI,(1-  glassMask ))

# Use the mask to create the masked sunglass region
maskedGlass = cv2.multiply(glassBGR,glassMask)

# Combine the Sunglass in the Eye Region to get the augmented image
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)

# Display the intermediate results
plt.figure(figsize=[20,20])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")
```
<img width="1771" height="407" alt="421694382-42a289c7-c773-482e-b0c6-6fc53e78b14d" src="https://github.com/user-attachments/assets/47d38360-d73a-4355-b692-19bccb486787" />

```
# Replace the eye ROI with the output from the previous section
faceWithGlassesArithmetic[205:355,100:340]=eyeRoiFinal

# Display the final result
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(faceImage[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");

```
<img width="1341" height="823" alt="421695545-b44da584-0a47-4d69-a97f-d45c0929ba84" src="https://github.com/user-attachments/assets/eace2895-92d7-49b0-b904-03d47fb14719" />

## Result
Program for adding Sunglasses to a Passport Photo Using OpenCV, Successfully executed




