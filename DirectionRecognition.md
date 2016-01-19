#Recognize which direction the finger point to

# Brief description on how to detect #

We will calculate the angle between 2 vectors (HP) (H is the center of hand, P is the fingertip) and (Ox), from this we will determine which direction the hand point to (left, right, up, down)

The condition for the program to detect direction is the number of fingertips detected is 1. Then the Cos(HP,Ox) is calculated. Depend on its value, we'll have the direct.

Cos(HP,Ox) > 0.7, direct = down.

Cos(HP,Ox) < -0.7, direct = up.

If -0.7 < Cos(HP,Ox) < 0.7, and H.y < P.y, direct = left.

If -0.7 < Cos(HP,Ox) < 0.7, and H.y > P.y, direct = right.

the program running on BeagleBoard

http://www.youtube.com/watch?v=vlyXyA5qgDQ

You can find the code in the the download section.

The code is compiled and work fine on Linux. I've tested it on Ubuntu, and Angstrom on my BeagleBoard.

The parameters is optimized for my camera resolution 640x480, and my camera is /dev/video1. If you want to use it on a different res, change step and r on line 97,98. I change it to r=16 and step=2 on 160x120 res.