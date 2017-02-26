# Vehicle Detection
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

[//]: # (Image References)
[color_classification]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/color_classification.png
[color_distribution_visualization]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/color_distribution_visualization.png
[color_histograms_visualization]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/histograms_color_visualization.png
[data_visualization]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/data_visualization.png
[distortion]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/screenshots/distortion.png
[gradient_visualization]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/gradient_visualization.png
[heatmap]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/heatmap.png
[hog_classification]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/hog_classification.png
[hog_visualization]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/hog_visualization.png
[loading_screen]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/screenshots/loading_screen.png
[one_box_per_car]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/one_box_per_car.png
[random_image_visualization]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/random_image_visualization.png
[sliding_windows]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/sliding_windows.png
[spatial_binning_visualization]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/spatial_binning_visualization.png
[undistorted]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/undistorted.png
[undistorted_and_warped]: https://github.com/ashispapu/CarND-Vehicle-Detection/blob/master/output_images/undistorted_and_warped.png

### Project 5 - Vehicle Detection and Tracking

Below steps are performed to achieve vehicle detection and tracking in a video stream .

+ **Feature Extraction** - apply five techniques, including histograms of color, color distribution, spatial binning, gradient magnitude, and Histogram of Oriented Gradients (HOG), on the labeled training set of images to create a feature vector.
+ **Preprocessing Data** - normalize, randomize, and split the labeled data into a training set, a validation set, and a testing set.
+ **Training** -  train a Linear SVM classifier on the labeled training set
+ **Sliding Windows** - implement a technique to search an image for vehicles using the trained classifier, and optimize the algorithm's efficiency by limiting the search area of the image and/or using heat maps that reject outliers of the positive windows.
+ **Video** - run a function using moviepy that estimates a bounding box for detected vehicles frame by frame.

Detailed description is given below .

### Feature Extraction

Several different techniques for feature extraction were used in Section 2 of  this project, including histograms of color, color distribution, spatial binning, gradient magnitude, and Histogram of Oriented Gradients (HOG). Each has its own effect on the feature vector that is produced, and when combined the techniques tend to improve the chosen classifier's performance.

**Histograms of Color**

Histograms of color are used to analyze the raw pixel intensities of each color channel as features in the image. Given an image in RGB color space, color histograms of features return a concatenated feature vector based on the number of intensity bins and pixel intensity ranges.

![color_histograms_visualization]


**Color Distribution**

Color distribution maps are useful in studying color values and locating clusters of color that correspond to objects of interest in an image. When plotting these maps in 3D, often the color distribution of objects of interest is conveniently clustered along a plane.

![color_distribution_visualization]

**Spatial Binning**

Raw pixel values are useful to include in the feature vector when the desired objects in an image remain identifiable at low image resolutions, such as a car object.

![spatial_binning_visualization]

**Gradient Magnitude**

Gradient magnitude is a technique used in previous computer vision projects (Projects 1 & 4) that applies a filter that represents the magnitude of the sobel-x and sobel-y gradients of odd-numbered pixel squares, such as 3x3 or 5x5.

![gradient_visualization]

**Histogram of Oriented Gradients (HOG)**

HOG feature extraction is the most important technique utilized in this project. The scikit-image package has a built in function to handle HOG extraction, which is tuned by parameters including orientations, pixels_per_cell, and cells_per_block.

![hog_visualization]

The final feature extraction method that was implemented includes color histograms, spatial binning, and HOG
