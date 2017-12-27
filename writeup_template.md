# **Finding Lane Lines on the Road** 
### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale when I tried to do this with RGB, but I decided to use HSL, so (1) I converted the image to HSL and apply a yellow and white filter to the image. (2) After that, i reduced the noises using gaussian blur. (3) After that apply Canny algorithm to detect line on the image, as a result, we have two lines, but they have empty spaces in some places especially on the image that not started with the marking. (4) Next, i defined vertices for an area of interest and apply the mask to the image output of the Canny algorithm. (5) Then I apply hough transform, it finds the lines from canny edges. To solve the problem with lines that not started from the beginning of the region of interest.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by adding a new function draw_lane_lines which calculate target slope for every frame, there we have 2 important indicators: how far current slope from average and the indicator of average Hough lines.

If you'd like to include images to show how the pipeline works, here is how to include an image
![alt hsl](https://github.com/Lykhoyda/SDC-Finding-Lane-Lines-on-the-Road/blob/master/result_images/hsl.png)
![alt roi](https://github.com/Lykhoyda/SDC-Finding-Lane-Lines-on-the-Road/blob/master/result_images/roi.png)
![alt result1](https://github.com/Lykhoyda/SDC-Finding-Lane-Lines-on-the-Road/blob/master/result_images/result_1.png)



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the road will have sharp turns and line is not
flexible enough to apply there.

Another shortcoming could be when we will have a lot of light or the road will be very dark, our line also can have gaps


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to modify hyperparameters, change the region of interest because I'm not sure that we need all the piece of road so far.

Another potential improvement could be to change logic of extrapolation because it works well only on straight road

P.S. The video 3 looks like scene from Star Wars :)
