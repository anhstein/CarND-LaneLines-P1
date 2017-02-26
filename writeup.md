#**Finding Lane Lines on the Road** 

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of the following steps, mimicking the lessons:

1. Convert the image to grayscale.
2. Apply Canny algorithm to highlight edges in the gray scale image.
3. Create a quadrilateral region of interest, masking out the rest of the Canny edges image.
4. Use Hough transform to detect lines from the masked Canny image, then draw those lines.
5. Layer the lines on top of the original color image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function to try to find a line that fits best through all small segments on each side. I separated left lane segments from right lane segments based on their slopes and their relative position compared to the midway point of the image. Using numpy.polyfit(), I got the formula for the line best fitted through all available points, and draw a line from the top of the region of interest to the bottom of the image. I tried to make longer segments count for more by including more points from them as the numpy.polyfit() input.

###2. Identify potential shortcomings with your current pipeline

Some potential shortcomings are:

- On roads with short or spaced out or faded line marks, this won't work very well.
- It only works with straight roads. It's obvious with the optional challange results that my code does not work on curvy roads.
- The region of interest is hardcoded and is the same for every frame. This may not work well on roads with a lot of up and down hills where the composition of the vision may change.
- The code can easily be fooled by other seemingly straight lines that fall into the region of interest, like ramps or other vehicles. 

###3. Suggest possible improvements to your pipeline

Some possible improvements to handle the shortcomings might be:

- I used the same parameters for Canny and Hough algorithms as from the sample in the quiz. There are perhaps more optimal values that would work better and create more stable lines.
- There's probably a better way to get the average line than what I did which felt rather manual.
- A smarter way to identify the region of interest, maybe by learning from past images compared against other positional data from the gyroscope or the steering wheel.
- What to do with curvy roads? Instead of drawing straight lines, do we need to draw curves? 