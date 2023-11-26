[Doc](https://siril.readthedocs.io/en/stable/preprocessing/registration.html)
Registration involves identifying features in a series of light frames and then applying transformations to get them to match. Siril offers several registration methods, each of which uses different feature detection algorithms and transformation calculations. There are two broad categories of transformations: *pixel*-level transformations are just a pixel offset that can be saved for each image. *sub-pixel*-level transformations are more accurate, but require intermediate data.

# Image Transformations
- **Shift** - just a 2-degree of freedom x/y shift. Only need 1 pair of stars to match
- **Euclidean** - 3-dof (x/y shift + rotation). Need 2 pairs of stars to match
- **Similarity** - 4-dof (x/y shift + rotation + scale). 2 pairs required
- **Affine** - 6-dof (x/y shift, rotation, shear, two scales). 3 pairs
- **Homography** - 8-dof, default transformation. strongly recommended for wide-field images. needs at least 4 pairs of stars to match.
# Registration Methods
- Global - a good default, robust
	- Matching is based on triangle similarity - see "FOCAS automatic catalog matching algorithms (1995)" for details.
	- RANSAC is used to reject outliers and determine a projection matrix
	- Then, the best matches are fed into the image transformation algorithm
- 2pass - global but lets you pick a good reference image after matching occurs