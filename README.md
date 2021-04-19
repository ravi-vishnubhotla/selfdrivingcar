# **Finding Lane Lines on the Road** 

## Description

### Autonomous Vehicles
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[image2]: (https://github.com/rkv7/selfdrivingcar/blob/main/examples/grayscale.jpg)
---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of following steps. 
1. Converted the images to grayscale
2. Blurr this gray image to smoothen unwanted edges.
3. Detect edges using cv2.canny() function. This detects all edges including many unwanted ones
4. Create a mask with same dimensions as canny_image to crop lanes only in the canny image
5. Define vertices of polygon which is of similar shape to lanes we want to analyse
6. Draw polygon on these vertices using cv2.fillPoly function
7. Use bitwise_and function and apply mask to the image. Now we have image where only lane edges are showing. 
8. We want to extract full line from these partial lane lines
9. Use HoughLinesP functon and extract line cordinates from masked image for both left and right lanes
10. Draw lines on the image using cv2.line and passing cordinates to this function


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

See below gray scale image. This is dispplayed using plt.imshow(). If you want to see an actual gray scale image use cv2.imshow instead

![alt text][image1]


### 2. Potential shortcomings with your current pipeline

1. This code is good for straight lanes. But as soon as the lane curves, we need better algorithms to deal with this
2. Also we are dealing in gray scale. So, code will not know if there are yellow lines
3. Hardcoding cordinate values

### 3. Possible improvements to your pipeline

1. Fit to polynomial curves instead of straight lines
2. Use HSL to deal with yellow lines
3. Ability to customize canny function to get better gradients in different driving conditions
