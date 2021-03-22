**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report




[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Pipeline

- Read an image and convert it to grayscale
- Apply a Gaussian blur, kernel_size = (3, 3).
- Use Canny edge detection, low_threshold = 50 and high_threshold = 150.
- Define the region of interest(quadrilateral) and apply a mask to the image outputted by Canny image detection.
- Apply the Hough transformation to find the lines in the masked image.
- Draw the lines over the original image. Several lines are generated from the previous step for left/right lane. I calculed the slope using the x and y coordinates and filtered the lines into "left" and "right" categories based on their position. I get the passing point using average coordinates of x and y. Then the endpoints of the lane lines were extrapolated using the passing point and the slope for left and right. 

![alt text][image1]


### 2. Identify potential shortcomings

- If the actual lane isn't clear, it's that it doesn't work well.
- It is not always accurate, as there is a possibility of losing precision in sudden rotation.
- In video tests, sometimes lanes may disappear at certain frames.

### 3. Suggest possible improvements

A possible improvement would be to fit the nonlinear curve to the lane instead of fitting the line. It can predict the upcoming turn and determine the curve.
Also, there is sometimes sudden movement of lanes in a video clip, so you can use the lanes of previous frames to consolidate the information of the frames to get a better result.
