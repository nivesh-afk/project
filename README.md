# project ClOTHS WRAPPING
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
2.	
3.	Pictorial Structures: Andriluka et al. [4] applied this generic model, while Johnson and Everingham [5] integrated color segmentation and limb detection.
4.	
5.	Part-Based Models: These approaches, including [5–8], are effective in breaking down the body into smaller components.
6.	
7.	Detector-Based CRFs: Vineet et al. [9] introduced a method combining detection with conditional random fields.
8.	
# 	Deep Learning Integration:
1.	CNNs combined with graphical models [10] improved pose estimation accuracy.
2.	
3.	Wei et al. [13] introduced a state-of-the-art system combining CNNs and a pose machine [11].
4.	
# 	Iterative Feedback: Carreira et al. [12] enhanced hierarchical feature extractors with iterative error feedback.

