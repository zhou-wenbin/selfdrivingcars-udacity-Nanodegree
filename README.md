# **Finding Lane Lines on the Road** 

## Getting started

### In this project, I will demonstrate how to detect lane lines in images using OpenCV. This is one of the main technologies for developping self-driving cars.

---

**Finding Lane Lines on the Road**

The goals of this project are the following:
* Make a pipeline that finds lane lines on the road
* Get familiar with OpenCV
* Get familiar with how to do image processing 


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[step1]: ./examples/step1.png "step1"
[step2]: ./examples/step2.png "step2"
[step3]: ./examples/step3.png "step3"
[step4]: ./examples/step4.png "step4"
[step5]: ./examples/step5.png "step5"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 4 steps. First, I converted the images to grayscale, then I use GaussianBlur funcitn to reduce noise and obtain a blurred gray image.
Second, I apply Canny function to detect all the edges in the image, from edges I use hough transform method to select lines. Then I define a four sided polygon to mask the desired area, which is normally in front of the  sensor camera implemented on the self-driving car, and choose the lines in the mask area. Thirdly, I draw the left and right line from the detected lines. In order to draw a single line on the left lanes, I pick up those lines with slope between 0.5 and 1, then pick up the point that the selected lines intersect with the border of the mask area as the upper point to the line that I want to draw, so as the bottom point for the left line. And do the same for right line by chosing those lines with slope between -0.5 and -1. Lastly, I combine the image with lines and orginal image to output the image with left and right lines drawn on the image.

#### I would like to include images to show how the pipeline works, here is how to include an image: 
* Step1: Obtain a blurred gray image

![alt text][step1]

* Step2.1: Obtain image with only lines selected

![alt text][step2]

* Step2.2: Mask desired area

![alt text][step3]

* Step3: Draw left and right lines on the lane

![alt text][step4]

* Step4: Combine original image with left and right line drawn image and output

![alt text][step5]

### 2. Identify potential shortcomings with your current pipeline


* One potential shortcoming would be what would happen when the self-driving car move from one kind of road into another kind of road where the chosen mask area wound not be applicable to both.



### 3. Suggest possible improvements to your pipeline

* A possible solution to the above issue is that to try methods that won't use mask area but can still can find the correct left and right lines.

