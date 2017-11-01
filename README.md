# **Finding Lane Lines on the Road** 


--

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./WorkingThrough_Shots/Org_testset.png 
[image2]: ./WorkingThrough_Shots/After_HSL.png 
[image3]: ./WorkingThrough_Shots/After_ColorSel.png 
[image4]: ./WorkingThrough_Shots/After_ROI.png
[image5]: ./WorkingThrough_Shots/Grayscale.png  
[image6]: ./WorkingThrough_Shots/CannyEdges.png 
[image7]: ./WorkingThrough_Shots/After_GaussianNorm.png 
[image8]: ./WorkingThrough_Shots/LinesDet.png 
---

### Reflection

### 1. Describe your pipeline.

My pipeline consisted of 6 steps as follows:

Firstly, I worked on this test set during the implementation [image1]

1- I'm converting the frame to the HSL color space , after many trials on the test set and another shots of the challenge.mp4 test video I ended up that HSL gives more accurate detections among the whole test set [image2].

2- Then I started to determine white and yellow color masks in order to apply them to the frame after merging both of them into single final mask [image3].

3- After applying the color mask I started to applying the region of interest ROI mask, firstly I tried manualy a varaiety of polygon vertices to accurately extract only the lanes region till I ended with some constant factors for each vertex coordinates which behaves properly on different frames [image4].

4- Then the frame gets converted to gray scale in order to apply the canny edge detection and then gaussian normalizing to remove the redundant noise [image5], [image6], [image7].

5- Now the frame is ready to apply hough line detection , I tried different values in order to tune all of the hough line detector parameters [image8].

6- Final step I drew the detected lines on the original frame using weighted_img() with predefined parameters. 
If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

1-  This pipeline doesn't extrapolate the sliced white lane to the full extent perfectly and I believe that this is most probably due to some fine tuning needed in the min_line_length and max_line_gap.

2- This pipeline doesn't behave perfectly on the challenge.mp4 video specifically in the white lane detection when the lane gets shaded by trees. 

3- I'm not sure if the lower and upper boundaries of the white and yellow colors are best set, I really searched in this point much much more trying to understand how the rgb boundaries are converted to HSL or HSV boundaries and I ended up with these values. 

### 3. Suggest possible improvements to your pipeline
1- More tuning for min_line_length and max_line_gap.
2- Trying more accurate white and yellow color ranges or maybe another color space maybe should be used.


