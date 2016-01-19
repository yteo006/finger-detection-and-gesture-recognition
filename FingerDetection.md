#The algorithm to detect fingers on a given hand contour.

# Prepare #

The 1st thing to do is finding the hand contour. This is quite easy in this project, for the hand is present on a dark background. Here is the step:

  1. Convert the image from the camera capture to grey scale.
> 2. Equalize the histogram, then smooth the image.
> 3. Threshold it.
> 4. Find the contour.

# Fingertips detection #

The contour we get from above is a sequences of points, and our task is to determine which point in that sequences is the fingertip. The concept here is that, the point that represents the fingertips is the peaks along the contour perimeters.

At each point i in the hand contour, we calculate the Cos of the angle between 2 vectors [P, P1] and [P, P2], where P is the i point, P1 is the i+r point, and P2 is i-r, I use r = 100 in 640x480 res. The idea here is that contour point P with the Cos close to 1 will represent potential peaks of valleys along the perimeters.

We get rid of the valley by convert the {p,P1] and [P,P2] vector in to 3D vectors lying on the xy-plane, and calculate the cross product. If the z component of the cross product is positive then it the valley.

Among those potential peaks point, we characterize some of them as the fingertips if they meet both of two conditions below:

  1. Cos(PP1,PP2) is is above 0.5 (the angle is lower than 60 degree).
> 2. Cos(PP1,PP2) is the maximum in its neighborhood of the contour.

# Notes #

The code is based on the OpenCV library. Everybody can download it and use it. And, this's the 1st time I code C++, so sorry for the messy code.

# References #

Shahzad Malik. Real-time Hand Tracking and Finger tracking for Interaction.

# Video #
http://youtu.be/h5T_Ga2y5b4