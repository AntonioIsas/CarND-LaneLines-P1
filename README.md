# **Finding Lane Lines on the Road**

Overview
---
When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project you will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.


[//]: # (Image References)
[image1]: ./test_images_output/regionOfInterest_solidYellowCurve.jpg "Region of interest"
[image2]: ./test_images_output/yellowMask_solidYellowCurve.jpg "Yellow mask"
[image3]: ./test_images_output/whiteMask_solidYellowCurve.jpg "White mask"
[image4]: ./test_images_output/colorFiltered_solidYellowCurve.jpg "Color filtered"
[image5]: ./test_images_output/gray_solidYellowCurve.jpg "Gray-scale"
[image6]: ./test_images_output/cannyEdges_solidYellowCurve.jpg "Canny edges"
[image7]: ./test_images_output/lines_solidYellowCurve.jpg "Houge lines"
[image8]: ./test_images_output/result_solidYellowCurve.jpg "Result"


Video of the results
---

[Video 1](https://youtu.be/sPFDIdei5m0)

[Video 2](https://youtu.be/uGqcpDyqN4Q)

[Challenge video](http://www.youtube.com/watch?v=ECmhbCULJpU)


# Reflection

##### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps.
* *1- Region of Interest:*

First I get the region of interest so we are only working whit the important section of the image
![alt text][image1]

* *2- Color Filtering:*

I had to add this step to complete the challenge as the canny edges on the gray-scale was not enough.
For this step I first transform the images to HSV space because it makes it easier to identify colors than RGB
Secondly I get a mask for the yellow color selecting all the colors in the appropriate range
![alt text][image2]
Then I do the same but this time for the color white
![alt text][image3]
After having both masks I combine them into a single mask I can use on the main image to extract only the colors I need
![alt text][image4]

* *3- Canny Edges:*

With the image filtered for colors we proceed to prepare the image for the edge detection converting it to gray-scale and applying a Gaussian blur
![alt text][image5]  ![alt text][image6]

* *4- Hough Lines:*

We apply a Hough transform to detect the lines in the edges giving us the following image
![alt text][image7]

* *5- Draw Lines:*

To draw the final lines I start by splitting them in two groups, based on the slope we determine if they belong to the left or right of the lane
Sometimes the code will find lines that are not part of the main line, so I added a new function to filter them out, what it does is calculate the average slope and then remove the lines that are too far from the average.

Then we send the filtered list to another custom function that will extract all points forming the lines, then fits a line through the points and draws them to the image
![alt text][image8]

##### 2. Identify potential shortcomings with your current pipeline

* One shortcoming is that the line is not very smooth, when some part of the line is not detected in the frame the line will move too much
* Another shortcoming could be different environment conditions like night as it is not thoroughly tested
* One more problem could be when there is a car closer in the region of interest
* Test with different image sizes as it is currently adjusted to the provided videos
* What happens when there are more objects in the image like rain or bugs
* Harder curves will have the lines split too much at the end


##### 3. Suggest possible improvements to your pipeline

A possible improvement would be to add some persistence to the line between frames so the line is more smooth
