The final step in light preprocessing in Siril is stacking. This increases the SNR by sampling the same random process many times.

# Stacking Methods
- Sum stacking
	- Simplest algorithm
	- SNR boost $\propto \sqrt{N}$ for $N$ images
	- No normalization or rejection, so can only be used for planetary processing.
- Average stacking with rejection
	- Compute the mean of pixels in a stack after some normalization and rejection
	- SNR $\propto \sqrt{N}$
	- There are several rejection methods including percentile, sigma, MAD, etc...
- Image weighting
	- We can weight each image by its quality, boosting the SNR further
