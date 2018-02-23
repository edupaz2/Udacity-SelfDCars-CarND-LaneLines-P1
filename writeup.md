# **Finding Lane Lines on the Road** 

## Eduardo Paz Orduña (edupaz2@gmail.com)

### Project submission for Udacity Self-Driving cars nanodegree.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps:

1) Convert the images to grayscale.
2) Apply a Gaussian Blur.
3) Apply Canny Edge Detection.
4) Filter the output to a single region on interest, a frustrum from the middle (narrow side) to the bottom image (wide side).
5) Apply Hough Transform.
6) Draw the result over the initial image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by doing:
1) Sorting left and right side lines by slope and x coord position.
2) Average the lines no each side with the help of np.polyfit
3) Draw a line using the line equation y = mx+b from the bottom image to the middle part of the image.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


Potential shortcomings:
1) The algorithm is not robust enough to discard other objects different than lane lines. Probably a better region of interest and better parameter tuning in the Canny and Hough algorithms will help. 
2) Objects in front of the car can produce unexpected behavior (not tested).


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to spend more time tuning the parameters in both Canny and Hough algorithms and reduce the region of interest to avoid fail detections with the car chasis or side roads.
