We were tasked with implementing a simulation for a self driving car that would allow for a real life car (the formula trinity autonomous departments race car) to take in information from the outside world using lidar and cameras and display it to our simulation engine. This would give our client a good visual representation of what we were planning to do and implement for them, by having a car drive around the silverstone race track in the United Kingdom without any human interaction. The main premise of the trinity autonomous department is to race a full lap without having anybody sit in the car.

![FT Image](https://github.com/rossmccrann/Traffic-Cone-Detection/blob/master/Ft.png)

![HUD Image](https://github.com/rossmccrann/Traffic-Cone-Detection/blob/master/HUD.png)


# Traffic-Cone-Detection

Orange Traffic Cone Detection in C#

Description of algorithms:

OpenCV/Emgu CV Orange Upright Traffic Cone Detection Algorithm 

Take in original image from Camera

![Original Image](https://github.com/rossmccrann/Traffic-Cone-Detection/blob/master/Original_Image%20-%20Copy.png)

Convert() image to HSV(Hue, Saturation, Value) 

![HSV Image ](https://github.com/rossmccrann/Traffic-Cone-Detection/blob/master/HSV_Image%20-%20Copy.png)

Isolate Oranges inRange() creating a lowThresholdImage and highThresholdImage
Create new image by using Logical OR the threshold images together

![OR Threshold Image ](https://github.com/rossmccrann/Traffic-Cone-Detection/blob/master/OR_Threshold_Image.png)

Create new image by smoothing the threshold image using, Erode(), DIlate() and SmoothGaussian().
Run Canny Edge Detection algorithm on smoothed image to create a Canny Image.
Canny().

![Canny Edge Detection Image](https://github.com/rossmccrann/Traffic-Cone-Detection/blob/master/CannyEdgeDetection_Image%20-%20Copy.png)

Create a Contour image by using findContours() and approxPoly() on the Canny Image.
Create an image of convex hull (Cone Shape)  for each contour in the listOfContours by using getConvexHull.

![Convex Hull Image](https://github.com/rossmccrann/Traffic-Cone-Detection/blob/master/ConvexHull_Image%20-%20Copy.png)

Create an image with convex hulls in the range of 3 to 10 by checking If convexHull.Total >= 3 And convexHull.Total <= 10.
Then check if(convexHullPointingUp(convexHull). (If the traffic cone is upright)

![Pointing Up Image](https://github.com/rossmccrann/Traffic-Cone-Detection/blob/master/Pointing_Up%20-%20Copy.png)
Draw line around remaining convexHulls (Cones) and overlap with Original Image.. 

Draw point at centre of gravity of each convexHull (Cone).
Fuse image with Lidar points to determine physical cones with a greater certainty

![Detected Orange Cone](https://github.com/rossmccrann/Traffic-Cone-Detection/blob/master/Detected%20-%20Copy.png)
