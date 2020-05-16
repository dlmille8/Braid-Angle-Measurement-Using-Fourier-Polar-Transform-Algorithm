# Braid-Angle-Measurement-Using-Fourier-Polar-Transform-Algorithm
Darren Miller | Class of 2020 at NC State University | iSSRL - Dr. Matthew Bryant
Artificial Muscle Research Project - Grad Students: David K., Nick M., Emily D. 

This image processing program uses a 2-D Fourier Transform and Polar Transform to measure the angle between fibers
in a mesh or braided structure. The main use case is artificial muscles (McKibben Actuators), which consist of an 
inflatable bladder encased in a tubular mesh structure. The "braid angle" of these muscles is a key figure in 
characterizing the behavior of these muscles, so I created an app to aid in the measurement of this value. The definition
of the Braid Angle is the angle between the horizontal (axially oriented along the muscle) and the fiber direction. 
This is effectively equivalent to half the angle between the fiber directions.

Potential other uses could be textiles, composite materials, etc. Anything where the angle between fiber directions is useful.

Load either a single image or a directory containing multiple images (only the images) and a seperate "plot data" text file to go 
along with the images, then run the program. The process in measuring the braid angle is as follows: the image (spatial domain)
is converted into frequency domain using a 2D Fourier Transform. The patterns in the frequency spectrum resulting from this
tell valuable information about the braided structure. 

If the image used is in the proper orientation (as described in the Guide pdf file), the prominent feature of the result 
of the 2D Fourier Transform (shown in the GUI) should be a 4-pointed star. The star is axially symmetric, so the top half 
or 0-180 degree section is used. The star point in the first quadrant (with a "positive" slope) corresponds to the frequency 
spectrum of fibers in the image that have a "negative" slope. The star point in the second quadrant (with a "negative" slope)
corresponds to fibers with a "positive" slope. That is to say, the patterns in the spatial domain and frequency domain 
responses are inverted. 

The program then uses a Polar Transform to find the angle each pixel lies at relative to the +x axis, where the center of the image
is the center of the coordinate system with the +x axis running to the right. The value of the pixels at the peaks are the highest, 
as the frequency of patterns in that direction are highest in the spatial domain (inverted though). A search vector with a "flare 
angle" (to be fan shaped, acting as a cushion to account for discretization of image) is swept around 0-180 degrees with a 
desired incremental step size. The mean pixel intensity is found at each step. The peaks of the star will be the peak values of 
mean pixel intensity. These refer to the most frequent or most prominent fiber directions contained in the image. 

In Single Image mode, the mean pixel intensity distribution and braid angle will be displayed. In Image Series mode, a plot of the 
Braid Angle vs the values in the plot data file will be shown. 

That file should be in the form of the following example:

Pressure (psi)

0  

5

10

15


20

There must be the same number of numerical entries as images, each entry on its own line. So in this case, 6 lines: 1 header with the data label, then five lines of numbers. The first line, containing the data label, will be the x axis label on the plot. 

Github is showing the numerical entries as being double-spaced, but that is incorrect. Each entry should be on seperate lines but not a blank line between.

There is also an option to show an animation of what is happening during the search vector sweep / scan and what the fan shaped vector 
looks like. This slows down the program, but is cool and fun.

Email me at dlmille8@ncsu.edu if you have any questions.
