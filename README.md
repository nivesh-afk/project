# project 
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
