#**Finding Lane Lines on the Road**


**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

As discussed through the first term of the course we go through 5 step process:

1. Converting image to one channel image (aka grayscale). It reduces color noice for the further processing + Canny edge detection algorithm expects exactly a grayscale image.
2. Transforming the image to show possible edges via processing it trough Canny edge detection algorithm.
3. Since Canny gives us a noisy image we need to make it smoother through applying  Gaussian Blur algorithm.
4. Choosing the region of our interest by creating a mask, that leave us only the road in front of the car. We get the final image by using bitwise `and` for the image and the mask.
5. Using Hough Lines to find all lines on the image. Min length and the max gap should be defined for the vast majority if use cases.

Changed the `draw_lines()` to eliminate lines out of the specific range.
`15 < angle < 45`


###2. Identify potential shortcomings with your current pipeline

There are a few, first it's not suitable for a city. I basically removed all horizontal lines. So, stop line will be just ignored.
Second, road visibility is quite small, particularly on a curved road.
Of course there is no detection of other cars.


###3. Suggest possible improvements to your pipeline

There are lots of hardcoded values. They should by dynamic and adjusted to an environment.
