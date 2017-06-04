# **Finding Lane Lines on the Road**

## Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)
[image1]: ./test_images_output/regionOfInterest_solidYellowCurve.jpg "Region of interest"
[image2]: ./test_images_output/yellowMask_solidYellowCurve.jpg "Yellow mask"
[image3]: ./test_images_output/whiteMask_solidYellowCurve.jpg "White mask"
[image4]: ./test_images_output/colorFiltered_solidYellowCurve.jpg "Color filtered"
[image5]: ./test_images_output/gray_solidYellowCurve.jpg "Grayscale"
[image6]: ./test_images_output/cannyEdges_solidYellowCurve.jpg "Canny edges"
[image7]: ./test_images_output/lines_solidYellowCurve.jpg "Houge lines"
[image8]: ./test_images_output/result_solidYellowCurve.jpg "Result"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps.
* 1- Region of Interes:
First I get the region of interest so we are only working whit the important section of the image
![alt text][image1]

* 2- Color Filtering:
I had to add this step to complete the challenge as the canny edges on the grayscale was not enought.
For this step I first transform the images to HSV space because it makes it easier to identify colors than RGB
Secondly I get a mask for the yellow color selecting all the colors int
*
*
*


![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]
![alt text][image6]
![alt text][image7]
![alt text][image8]

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ...

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
