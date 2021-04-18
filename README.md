# **Finding Lane Lines on the Road** 

## Writeup Template test

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

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

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
