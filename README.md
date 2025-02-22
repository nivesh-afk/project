# Project Image Based Clothes Changing System

# Image-based clothes changing system
Prior Work:

1)Chen et al.: Developed a clothes-swapping algorithm for similar styles and colors, but it lacked versatility for different textures and styles.
2)Zhou et al.: Proposed a parametric body reshaping system but faced limitations when applied to natural user-provided images.
Proposed System:

Introduces an automatic clothing-changing system.
User Input: Users provide a photo and select clothing from a model library.


Process:

1)Segmentation: Extracts precise masks of the human body from the input and library images.

2)Joint Detection and Boundary Matching: Aligns the user’s body with the target clothing model.

3)Parametric Comparison: Calculates differences between the two bodies.

4)Content-Aware Warping: Adapts the clothing to fit the user's body shape.

5)Head Swapping: Ensures a seamless composition of the final image.

6)Output: A realistic image of the user wearing the selected clothing.


# Articulated Human Pose Estimation
Articulated human pose estimation enhances the semantic understanding of images by predicting the positions of key body joints.
# 	Key Approaches:
1.	Reduced Search Space: Ferrari et al. [3] reduced the computational complexity, improving estimation success.
	
3.	Pictorial Structures: Andriluka et al. [4] applied this generic model, while Johnson and Everingham [5] integrated color segmentation and limb detection.

5.	Part-Based Models: These approaches, including [5–8], are effective in breaking down the body into smaller components.
   
7.	Detector-Based CRFs: Vineet et al. [9] introduced a method combining detection with conditional random fields.
   
# 	Deep Learning Integration:
1.	CNNs combined with graphical models [10] improved pose estimation accuracy.
   
3.	Wei et al. [13] introduced a state-of-the-art system combining CNNs and a pose machine [11].
   
# 	Iterative Feedback: Carreira et al. [12] 
enhanced hierarchical feature extractors with iterative error feedback.

# Articulated Human Pose Estimation
This field focuses on estimating human body poses in images, essential for understanding semantic content in visual data. Highlights include:

1.Reduced Search Space Algorithm: Ferrari et al. improved estimation success rates by minimizing search complexity.

2.Pictorial Structure Models: Introduced by Andriluka et al., providing a generic framework for pose estimation.

3.Hybrid Approaches: Johnson and Everingham combined color segmentation and limb detection for enhanced results.

4.Part-Based Models: Proven effective by various studies [5–8].

5.Graphical Models and CNNs: The integration of these methods [10] achieved high performance.

6.Inference Machines: Ramakrishna et al. proposed a machine leveraging rich spatial interactions.

7.Iterative Error Feedback: Developed by Carreira et al., refining hierarchical feature extractors.

8.Pose Machines: Wei et al. combined CNNs and pose machines for state-of-the-art results.

# Semantic Image Segmentation
This area focuses on partitioning images into meaningful regions. Key advancements include:

1.Interactive Methods: Blake et al. introduced probabilistic approaches for user-guided segmentation.

2.Conditional Random Fields (CRFs): Widely applied for automatic segmentation systems, leading to improved results.

3.Region Grouping: Techniques [17–20] tackle segmentation using grouped regions.

4.Hierarchical Models: Combined with other methods [16, 18, 19] for enhanced segmentation performance.

5.Salient Region Detection & Attention Models: Significantly boosted segmentation capabilities [21–23].

6.Pixel-Wise Labeling: Zheng et al. developed methods labeling each pixel with object class and attributes.

7.Deep Learning: Neural networks [15, 23] currently dominate, achieving state-of-the-art performance.


# Image Warping
Image warping involves deforming images based on control handles for manipulation:

1.Optimization Methods: Used for image deformation.

2.Radial Basis Functions (RBF): Another popular technique for warping.

3.Moving Least Squares (MLS): Effective for smooth image deformation.

4.Skeleton-Based Warping: Zhou et al. introduced resizing methods based on body skeletons and parameters.

5.Finite Element Method (FEM): Kaufmann et al. proposed a unified framework using FEM for warping.


# 1. Initial Segmentation with GrabCut
Algorithm:

Graph-cut-based segmentation that iteratively optimizes masks.

Traditionally requires user input, but here automated with prior knowledge.

# 2. Heatmap Generation
Saliency Heatmap (H):
High-saliency regions are detected using [30].
Heatmap values (0–255) are converted into a four-valued indicator function:

0: Background.

1: Probable background.

2: Probable foreground.

3: Foreground.




![Screenshot (23)](https://github.com/user-attachments/assets/4d0c8b0e-3749-4d72-94c2-bbfd75213274)



# 4. Contour Detection for Refinement
Hierarchical Contour Detection:

Locates the human body contour as a polygon.

Regions inside the polygon are designated as human body parts.



# 5. Mask Refinement
1.Challenges:

Rough mask edges.
Noise pixels affecting matching accuracy.

2.Refinement Techniques:

Median Filtering: Reduces noise but can lose details.
Weighted Image Matting [33]: Effective but slow (>1 min for  480 x 640 images)


3.Guided Image Filter [31]:

Chosen for its speed and efficiency.
Processes a 480×640 image in 0.1 seconds on standard hardware.

# Results and Demonstration
Output: The refined mask effectively separates the human from the background.
Limitations Addressed:

Combines saliency and skin detection to improve segmentation.
Utilizes contour detection for better region delineation.
Applies guided filtering to ensure clean edges and noise removal.



#  Partial Shape Matching 
This section outlines the process of matching body contours for accurate image warping, emphasizing the need for precise alignment to avoid distortions. Here's an organized breakdown:



# Body Contour Matching
1. Boundary Point Extraction
   
From the segmentation mask, boundary points (C) are extracted using an edge detection algorithm.
These points define the body contour for matching.


2. Challenges with Shape Contexts
   
Shape Contexts [34]:
A common method for shape matching.
Ineffective for human body contours due to:

Cross Matching: Incorrect associations between body parts (Fig. 4(a)).
Part Shifting: Misalignment of body part contours (Fig. 4(b)).

Lack of semantic body information leads to challenges in subsequent tasks like warping and head swapping.




3. Manual Key Point Labeling (Inefficient Solution)
Labeling key points along contours could help, but:

Requires manual input for each image.
Time-consuming and impractical for automated systems.



Research Overview
The paper presents a system that allows users to change their clothes virtually using their own photo and an image library.
The system involves several steps: body segmentation, contour matching, image warping, and head swapping.
Methodology
Body Segmentation:
Uses saliency detection and skin detection to generate a mask for the human body.
The mask is refined using median filtering and guided image filtering.
Contour Matching:
Extracts boundary points from the body contour using edge detection.
Utilizes Convolutional Pose Machines (CPM) to detect key joint points, which are then used to select control points on the body contour.
Generates denser control points for triangle mesh generation to maintain body semantics.
Image Warping:
Compares two standard image warping methods: Radial Basis Functions (RBF) and Moving Least Squares (MLS).
RBF is chosen due to its better performance in avoiding distortion and aliasing.
Warping is performed using constrained Delaunay triangulation and barycentric coordinates.
Head Swapping:
Extracts the head contour from the mask.
Determines the stitch line and fusion area based on the control points on the neck.
Replaces the head and performs Poisson fusion to hide the stitching line.
Results and Discussion
The system can handle various input poses and body shapes, maintaining the user's body shape accurately.
It performs well even in extreme cases with significant differences in height and weight.
Comparison with other methods shows that the proposed system requires less user interaction and provides more accurate body warping results.
Limitations and Future Work
The system relies heavily on brightness and illumination for color-space-based image segmentation.
It assumes no overlap between limbs and the body.
The system only uses the contour of the clothes for shape recognition, which may not accurately reflect the user's body shape.
Future work includes collecting more data to create a neural network for segmenting body parts and improving the warping method to avoid distortion in hands and shoes.
Conclusions
The system has broad applications, such as online virtual try-on and in-store customer experience.
It aims to change the traditional way of selecting clothes by providing a quick and efficient way to visualize different outf






















