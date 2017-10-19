# A regarder : 
* Computer Vision A-Z  Section 1 Face Detection : https://www.udemy.com/computer-vision-a-z/learn/v4/t/lecture/8254464?start=0

#  A retenir : 
```
Video 1- Viola-Jones algorithm 
2001 : Creation of cv2 
2 parts : Training , Detection 
Detection on GREYSCALE 
Detection / Looking for some feature of the face : 2 eyes, 1 noise, 1 mouse. 
Scan the image, create several green boxes of detection. 
```

```
Video 2- Haar-like Features
 
-Edge features 
-Line features 
-Four rectangle features 
Look at in the GREYSCALE the different features. 
Mouse = Line features 
Eyebrow = Edge features 
Noise (both size) = Edge features 
Eyes = Line features 

Edge features Map : 
~ 0 withe (0.1, 0.2, 0.3.....)
~1 black (0.4, 0.6, 0.7.......)
average intensity of all the pixels 
W=0.166
B=0.568 
B-W =0.402 
if B-W ~0.402 can be a potential noise 
```

```
Video 3- Integral Image 
Same size of the initial image 
Rectangle: everything left 
Sum all the value on the left 
4 operations against 12.  

Video 4-Training Classifiers 
Which features are relevant? 
Reduce the size of the images : 24x24 px dimension. 
Labeled as Face image / None-Face Images (high rate of false postive).

Video 5- Why Adaboost ? 
Too much features to detect. 
180.000 + features in a 24X24 px. 
huge number. 
180.000 for all the images in the training images.....nightmare, too long. 
Increase the importance of the images that was not well classified. 
Minimize the error rate.

Video 6- The Cascade 
Step 1 : If the top five features to detect an object are not presents we reject Sub-Window.
Next 12 features at step 2. 
```
