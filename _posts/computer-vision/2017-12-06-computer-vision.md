---
layout: post
title:  "Computer Vision"
date:   2017-12-05 20:00:00 +0900
tag: [Vision, Topics]
---

# What is Computer Vision?

Acquiring, processing, analyzing, and understanding visual data in order to produce numerical or symbolic information.[wikipedia]

# Human Eyes

- [간상세포 (약한 빛, 운동)](https://ko.wikipedia.org/wiki/간상세포)
- [원추세포 (시세포로 색을 감지)](https://ko.wikipedia.org/wiki/원추세포)


# Topics in Computer Vision

- Low-level vision (early vision)
  - Image formation
  - Image filtering 
  - Optical flow 
  - Image segmentation
  - Stereopsis

- Mid-level
  - Object tracking
  - Human motion analysis

- High-level vision
  - Object recognition 
  - Event detection 
  - Scene & video understanding


# Python Image Library

- [Pillow](https://pillow.readthedocs.io/en/4.3.x/)
  - Pillow(PIL fork) provides general image handling and lots of useful basic image operations like resizing, cropping, rotating, color conversion and much more.

# Image
- Images are stored in 2D or 3D arrays.
- Images can be dealt with as a function

# What is Image Histogram?

- A histogram is a distribution of pixel values - each bin has a count of how many pixels have the value.

# What is Histogram Equalization?
- Flattens the histogram so that all intensities are as equally common as possible.

# What is Image Filtering?

- Filtering is a technique for modifying or enhancing an image. For example, you can filter an image to emphasize certain features or remove other features. Image processing operations implemented with filtering include smoothing, sharpening, and edge enhancement.

- Application of Filtering
  - Enhance an image, e.g., denoise, resize.
  - Extract information, e.g., texture, edges.
  - Detect patterns, e.g., template matching.

# Linear Filtering

- Correlation Filtering
  - Involves weighted combinations of pixels in small neighborhoods.
  - The output pixels value is determined as a weighted sum of input pixel values
  - Filter coefficients
- Convolution Filtering
- Symmetric kernel has same results of correlation and convolution filtering.

# Separable Linear Filtering
- The process of performing a convolution requires K2 operations per pixel, where K is the size (width or height) of the convolution kernel.
- In many cases, this operation can be speed up by first performing a 1D horizontal convolution followed by a 1D vertical convolution, requiring 2K operations.
- If this is possible, then the convolution kernel is called separable.
  - **K = vh<sup>T</sup>**


---

# Study Catalog

Image Histogram

Histogram Equalization

Image Filtering

Linear Filtering
- Weight Kernel
- correlation
- convolution

Padding
- zero
- warp
- clamp
- mirror

Image Derivatives
- Prewitt
- Sobel (x-derivative, y-derivative, magnitude)
- Gaussian (sigma 2, 5, 10)

Separable Linear Filters
- box
- bilinear
- Gaussian
- Sobel
- corner
Gaussian Pyramid

Morphology
- Thresholding function
- Dilation
- Erosion
- Majority
- Opening
- Closing
- Counting Object

Distance Transform
Connected components

Edge and lines

Detecting edges
2D edge detection filters
- Gaussian
- Derivative
- Laplacian
Directional Derivatives

Canny Edge Detector
- Hysteresis Thresholding
- Scale Selection
- Scale

Line Detection
- Successive Approximation
- Hough Transform

---

Local Image Descriptors

Invariant Local features
Corner Detection
- Approximation
- Harris Corner Detector
- FAST

Feature Detection
- Rotation invariance
- Scale Invariance


Feature Descriptors
- MOPS
- SIFT
- SURF
- Binary Descriptors
    - BRIEF
    - BRISK
    - ORB
KAZE Feature
- Edge-preserving blur
HOG Feature
Feature Matching
- NNDR
- Greedy approach
- Hungarian method


Image Transformations

- translation
- Euclidean
- similarity
- affine
- projective (homography)

2D Parametric Transformations
- translation
- rigid(Euclidean)
- similarity
- affine
- projective

Degree of Freedom

The number of independent pieces of information that go into the estimate of a parameter is called the degrees of freedom (DOF). In this guide, DOF are given for 3D images.

each of a number of independently variable factors affecting the range of states in which a system may exist, in particular.

Image Warping
- Forward Warping
- Inverse warping
- linear interpolation
- Homogeneous Coordinate


Homography Estimation
- (DLT) Direct linear transform 

Robust Parameter Estimation
- RANSAC
- Estimation Refinement(개선)
- LLS
- NLS
- LM Algorithm
- Robust Least-Squares

Parameter Estimation Summary
To estimate the parameters of a model for the noisy data:
* DLT works only for noise-free data.
* Use RANSAC or similar to filter the outliers.
* Use optimization for the inliers with the RANSAC result as the initial parameter.
* Even after RANSAC filtering, using a robust norm in optimization is desired.  
Panorama Stitching

---

Image Formation
- Pinhole Camera Model
- Projection
- Projection matrix
- Parallel lines meet in the image
- 3d 2d projection
- Camera Intrinsics
- Perspective Projection
- Variable Aperture
- Lense
- Depth of field
- Lens Distortion
- Tilt-shift
- Photometric image formation
- Vignetting: Spatial Non-Uniformity
- Camera Sensor
- Color Separation


---

Structure from motion

Triangulation
P3P Pose Estimation
Epipolar Geometry
Two-frame structure from motion
Bundle Adjustment
- Least squares

2D Homography
Planar Homography
Pure Rotation

Summary
* Image forma0on by pinhole camera model.
    * Camera intrinsics convertng between pixel coordinates and 3D rays.
    * Perspectve projec0on.
* Homogeneous coordinates and 2D and 3D transformations.
    * 2D homography — pure rota0on and planar homography.
* Triangula0on and 3D pose es0ma0on.
* Epipolar geometry.
    * Two-view structure from mo0on.
* RANSAC.
* Bundle adjustment.

---


Dense Stereo and Depth Estimation

Binocular Stereopsis
converging cameras
motion parallel with image plane
forward motion
Stereo Calibration
Stereo Rectification
Stereo Disparity
Sparse Correspondences
Dense Correspondence
Lighting Conditions (Photometric)
Ambiguity
Multiple Interpretations
Window
Problem of Occlusion
Stereo Constraints
Window correlation
global optimization

Stereo matching
Dynamic programming
Segmentation-based techniques
Global Optimization
Multi-view stereo


Depth Estimation

Lense Array (Integral Imaging)
Structured light
laser scanning
time of flight

Summary
* Triangulation and epipolar geometry
* Stereo camera calibration and rectification
* Sparse / dense correspondence
* Local methods / global optimization
* Multi-view stereo  

---

Visual tracking

Mean-shift Algorithm
Main-shift vector
Scale Selection
Camshift Tracking
Probalbilistic Formation of visual tracking
Kalman Filtering
Bayesian Filtering
Particle Filtering
Object Model for tracking
Example: Condensation
Appearance Model
Motion Model
Example: Incremental Visual Tracking
Object state estimation
Tracking as an optimization
Optimization methods
Iterative Closest Point
CMA-ES
Non-rigid Surface Tracking using CMA-ES and NURBS
Physical simulation
Tracking Deformable Objects with Point Clouds

MIL Tracker
L1 Tracker
Hough Track
Tracking-Learning-Detection
Benchmark Evaluation

Summary
* Visual tracking:
    * Probabilistic inference : estimation of posterior probability density.
    * Optimization : state which gives the minimum cost.
* Object models
    * Appearance/shape model
    * Motion model
* Generative / discriminative approaches.
* Thorough evaluation on tracking accuracy or robustness.  

---

Clustering and Segmentation

Data clustering problem
Clustering Algorithms
- Hierarchical methods
    - Agglomerative clustering
    - divisive clustering
- Iterative methods
    - k-means clustering
    - EM algorithm
    - Mean-shift algorithm
- Spectral clustering
    - Normalized cut

Data Affinity

Clustering in computer vision
- image segmentation
- foreground/background segmentation
- feature clustering
- image/video categorization

k-Means Clustering Procedure
1. Randomly select k-means. 2. Find the association of all samples to the k-means. 3. Move the locations of k-means to the mean of the associated samples.
4. Goto the step 2 and iterate until convergence.

Sensitivity to outliers
Segmentation by graph partitioning
measuring affinity
minimum cut
minimum graph cut
Solving normalized cut

---

Detection and Recognition


PCA and FLD

Evaluating classifier
classifier and Error rates

Support Vector Machine
Binary classification
Linear classifiers

Perceptron Algorithm

Large margin classifier
Dual Formulation
Empirical Risk and True Risk
VC Dimension
Capacity of Functions
Capacity of Hyperplanes
Linear Support Vector Machine
Soft-margin Formulation
Soft-margin Optimization
Gradient-descent Algorithm for SVM training
Non-linear Support Vector Machine
The Kernel Tricks

AdaBoost and Face Recognition
Boosting Approach
PAC Learning
Boostring Algorithm
Characteristics of AdaBoost
Face Detection by AdaBoost
Integral Image
Learning Results
Attentional Cascade
Cascaded Classifier

---

Deep Learning

AI - NEURAL NETWORK
• Neural Network • Backpropagation • Activation Function
• Dropout

---

# References

```
http://sebastianraschka.com/Articles/2014_python_lda.html
https://en.wikipedia.org/wiki/Linear_discriminant_analysis
https://en.wikipedia.org/wiki/Principal_component_analysis
https://wikidocs.net/5957
http://sanghyukchun.github.io/72/
https://github.com/rushinshah7942/Classification-and-Regression
https://github.com/jayavardhanravi/FLD/tree/master/mypart1
http://benalexkeen.com/k-means-clustering-in-python/
http://adnoctum.tistory.com/442
http://docs.scipy.org/doc/scipy/reference/tutorial/ndimage.html http://scipy-lectures.github.io/advanced/image_processing/ http://nbviewer.ipython.org/github/jrjohansson/scientific-python-lectures/blob/master/Lecture-4-Matplotlib.ipynb
http://scikit-learn.org/stable/index.html#
```

---
---
---

# [Computational Photography](https://classroom.udacity.com/courses/ud955)

---

# [Introduction to Computer Vision](https://www.udacity.com/course/introduction-to-computer-vision--ud810) (2017-11)

---

# Computer Vision Topics

1. Image formation and optics
2. Image processing, filtering, Fourier analysis
3. Pyramids and wavelets
4. Feature extraction
5. Image matching
6. Bag of words
7. Optical flow
8. Structure from motion
9. Multi view stereo
10.Segmentation
11.Clustering
12.Viola-Jones
13.Bayesian techniques
14.Machine learning
15.RANSAC and robust techniques
16.Numerical methods
17.Optimization
18.Range finding, active illumination
19.Algorithms
20.Graph cuts
21.Dynamic programming
22.Complexity analysis
23.MATLAB and C++. and assembly (optional: GPU programming)
24.Communication and presentation skills

Image and features
• NCC
• Interest point operators
• Scale invariant and affine invariant detectors & descriptors
• Scale space
• Image processing, filtering, Fourier analysis
• Pyramids and wavelets
• Edge detection
• Restoration e.g. deblurring, super-resolution
– Linear, e.g. Wiener filter
– MRF
– Non-local means/BM3D/bilateral filter

Segmentation, grouping and tracking
• Segmentation
– Normalized cuts
• Grouping
– Hough transforms
• Clustering
– K-means
– Mean-shift
– Pedro-clustering
• Tracking
– Kalmanfilter
– Particle filter

Multi-view: stereo, SFM, flow
• RANSAC and other robust techniques
• Geometry:
– epipolar geometry (projective and affine)
– planar homographies
– Affine camera
• Geometry estimators
– 8 point algorithm for F
– 4 point algorithm for H
• Factorization
• Bundle-adjustment
• Flow
– Horn & Schunck L2
– Lucas-Kanade
– L1 regularized

Recognition
• Bag of visual words
• HOG, SIFT, GIST
• Spatial pyramid
• Spatial configurations/Pictorial structures
• Sliding window/jumping window
• Cascades
​
Others
Machine Learning
– Adaboost
– kNN
– SVM
– Random forest
– PCA, ICA, CCA
– EM
– MIL/Latent-SVM
– Regularization
– HMM
– Graphical & Bayesian models
Optimization
– Classical linear and non-linear
– Graph operations
– Dynamic programming/message passing for MAP, max-marginals
– Graph cuts for binary variable MAP
• Texture synthesis
