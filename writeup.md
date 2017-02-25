#**Finding Lane Lines on the Road** 

[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of the following steps, mimicking the lessons:

1. Convert the image to grayscale.
2. Apply Canny algorithm to highlight edges in the gray scale image.
3. Create a quadrilateral region of interest, making out the rest of the Canny edges image.
4. Use Hough transform to detect lines from the masked Canny image, then draw those lines.
5. Layer the lines on top of the original color image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...