# **Finding Lane Lines on the Road** 

## Writeup 


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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I use a mask for white and yellow. I bit wise or them to create a general mask and then I bitwise and that new mask across the grey image.
I then used a gaussian blur on the images using a kernel size of 7. I then use a canny edge detector to sign the edges I care out. I then filter out all that data by only looking at a certain area of interest (what would be in front of the car). I then used a hough transform to return an image with the lines drawn

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by calculating the line, determining if it's negative or positive to see if if belongs to the right or the left side of the image. I append those values to a stack for positive and negative slopes, respectively. I then get the average of the slopes and intercepts. Then I find the x_min and x_max for the positive line or the negative and then output the line using cv2.line


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the lane line start to curve or when the time of day changes. The changing of the lane would cause the predicted line to constantly come in and out. The time of day changes could affect the detection of the lines because now the colors are not necessarily "yellow" or "white"


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use HLS or HSV instead of RGB images

Another potential improvement could be to use the previous location of a lane and use that as a box of interest to look for the continuitation of that line 
