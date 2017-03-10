#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

(all the image can be get at ./examples, video output is white.mp4 & yellow.mp4.)

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
**Step 1:**  I converted the images to grayscale, this is creating gray image for canny use later. 
**Step 2:**  then use gaussian blur to handle gray image to reduce noise, set kernel_size to 5.
**Step 3:**  then use canny algorithm to detect image's edge, and get lines for hough function usage. 
             set `low_threshold = 50` and `high_threshold = 150`.
**Step 4:**  then define a four sided polygon to mask image, this is the region of interest.
             set `vertices = np.array([[(30,imshape[0]),(418, 325), (550, 325), (930,imshape[0])]], dtype=np.int32)`, which is our interest region.
             and plot the interest region with line.
**Step 5:**  then use hough transform method to to detect lines in an image, and carefully tune the parameters to fit our aim.
			 for images test, set: 
			 `rho = 2`, `theta = np.pi/180`, `threshold = 13`, `min_line_len = 40`, `max_line_gap = 6`, this get images very good effect.
			 for video test, set:
			 `rho = 2`, `theta = np.pi/180`, `threshold = 17`, `min_line_len = 41`, `max_line_gap = 15`, this could get good video handling result.
**Step 6:**  and finally draw the lines on the image.



In order to draw a single line on the left and right lanes, I modified the draw_lines() function by :
**1:**  add "vertices" parameter into the function prototype, in order to automated call the values of region which i defined before, no need 
        to modify the value by hand.
**2:**  define left_lines array and right_lines array to store the left lines and right lines. The two sides lines are separated by their slope, slope = (y2-y1)/(x2-x1),
        so if slope>0, it is right line, otherwise, if slope<0, it is left line, and according to "b = y1 - slope * x1", calculate b in the meantime, then put all left lines or right lines into array, and then calculate their average by np.mean() method, by this way, we can get average "slope" and "b" parameter, then we can get a line by fomular "y=slope*x + b", this is what we want. also, y is certainty according to our mask region of interest, max y is the bottom of image[0], mix y is the top of image[0], so as x. 
**3:**  then use cv2.line() to draw the line according to above x,y end point data.
**4:**  show image or video to see the output is correct or not.
   


###2. Identify potential shortcomings with your current pipeline
**1:** in the yellow left video, the left line is a little hop in the video. this is produced by other noise.
solutions: 
	a.still need to tune the hough parameter to get good output.
	b.use more complicated math theory to solve getting line problem.
	c.use algothrim to get best hough parameters.

**2:** output is determined greatly by hough and canny parameters. if we driving on the complicated road in reality, we cannot guarantee the program works well, maybe it
wil crush when driving.

**3:** image process is impacted by illumination and whether and so on, the result will not be good.




###3. Suggest possible improvements to your pipeline
**1:** need to tune the hough parameter to get good output.
**2:** use more complicated math theory to solve getting line problem.
**3:** or use algothrim to get best hough parameters.
**4:** add more abnormal cases handling when no line find by hough transform function.