"# Carnd-Term1" 
#**Finding Lane Lines on the Road** 

[image1]: examples/solidYellowLeft.png "solidYellowLeft.png"  
[image2]: ./examples/solidWhiteCurve.png "solidWhiteCurve.png.png"
[image3]: ./examples/hls.png "hls.png"
[image4]: ./examples/canny.png "canny"
[image5]: ./examples/reg.png "reg"
[image6]: ./examples/houghline.png "houghline"
[image7]: ./examples/polyfit1.png "polyfit1"
[image8]: ./examples/yellow_final.gif "yellow_final"

Overview
---

In this project, I will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.  


The Project
---
**Step 1:** Getting setup with Python

To do this project, you will need Python 3 along with the numpy, matplotlib, and OpenCV libraries, as well as Jupyter Notebook installed. 

**Step 2:** Installing OpenCV

Once you have Anaconda installed, first double check you are in your Python 3 environment.


The Reflection
---
My pipeline consisted of 5 steps. 

**Step 1:**  

I converted the images to grayscale, this is creating gray image for canny use later. 

**Step 2:**  

then use gaussian blur to handle gray image to reduce noise.

**Step 3:** 

then use canny algorithm to detect image's edge, and get lines for hough function usage. 

**Step 4:**  

then define a four sided polygon to mask image, this is the region of interest. set vertices which is our interest region, and plot the interest region with line.

**Step 5:**  

then use hough transform method to to detect lines in an image, and carefully tune the parameters to fit our aim.

**Step 6:**  

and finally draw the lines on the image.

![car_line_draw][image1]
![car_line_draw][image2]

The Modified Information
---
1. RGB -> HLS color space to extract lane line:

![HLS space][image3]

Canny image:

![cany space][image4]

region of interest image:

![region of interest space][image5]

hough line image:

![hough line][image6]

and then use machine learning to polyfit the line, polyfit image:

![polyfit line][image7]

final effect:

![final][image8]

The Detailed Information
---
Please see writeup_template.md file.

Thanks.
all by asimay_y@126.com
