#**Finding Lane Lines on the Road** 
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline process an image as follows.

1. Makes a gray scale image to normalize the image,
2. Applies Gaussian smoothing to suppress noise of the image,
3. Applies Canny transform to extract edges of image,
4. Applies Hough transform to a region where the lane lines are running to find lane lines in the image, and
5. Draws the lane lines in the image in red

At Step 5 above, `draw_lines()` does following things.

1. Filters and categorizes each line into the left lane or the right lane using `looksLikeLane()`. This function checks the magnitude of the slope of the line. If the magnitude of the slope is in a potive range, e.g. more than 0.5 and less than 1, the line is recognized as part of the right lane. If the magnitude of the slope is in a negative range, e.g. more than -1 and less than -0.5, the line is recognized as part of the left lane. 
2. 

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...