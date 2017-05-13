# **Finding Lane Lines on the Road** 
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:

* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline process an image as follows.

1. Makes a gray scale image to normalize the image,
2. Applies Gaussian smoothing to suppress noise of the image,
3. Applies Canny transform to extract edges of the image,
4. Applies Hough transform to a region where the lane lines are running to find lane lines in the image, and
5. Draws the lane lines in the image in red.

At Step 5 above, `draw_lines()` does following things.

1. Filters and categorizes lines into the left lane or the right lane using `looksLikeLane()`, which is a simple function that checks the magnitude of the slope of the line. If the magnitude of the slope is in a potive range, e.g. more than 0.5 and less than 1, the line is recognized as part of the right lane. If the magnitude of the slope is in a negative range, e.g. more than -1 and less than -0.5, the line is recognized as part of the left lane. 
2. Finds the top ends and the bottom ends of the lane lines by sorting the lines. 
3. Updates the coordinates of the top ends of the lane lines if necessary. This is for keeping the position of the top ends of the lane lines in a certain area throughout of a video. 
4. Calculates the coordinates of the bottom ends using `extension()`, which simply utilizes the coordinates of the top end and the bottom end of the lane line.
5. Draws the lane lines using the coordinates of the top ends and the bottom ends calculated at Step 3 and 4 above. 


### 2. Identify potential shortcomings with your current pipeline


Potential shortcoming would be

1. The logic implemented in `looksLikeLane()` to detect lane lines is not adaptive. The parameters to accept lines as part of a lane have to be manually set at this point. 
2. The initial image processing affects the positions of the top ends of the lane lines. Since the positions of the top ends of the lane lines will be kept in a certain area throughout of a video, the positions the top ends could be locked in a wrong area throughout of a video e.g. if noises of image were not removed properly in the image processing and the noise was recognized as part of a lane. 

### 3. Suggest possible improvements to your pipeline

A possible improvement would be 

1. To utilize more information to detect lane lines if possible. e.g. the position of the camera could be utilized to detect features of a lane line. If the position of the camera was relatively high, the slope of a lane would become steep and vice versa. 
2. To conduct a fine tuning of the parameters of the image processing. This would be necessary to avoid fixing the position of the top ends at the first place. 

### 4. Note

I tried the optional challenge, but I was not able to make it for the due date. My pipeline works just for the first and the second videos at this point. 