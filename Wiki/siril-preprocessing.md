# Conversion
First, we must convert the raw images into [[FITS]] data. Debayering at this stage should *not* be done for bias, dark, and flat images (or lights that will be preprocessed).

# Calibration
There are three main calibration frames. When multiple exposures are used, you can create a *master* version of that frame. In [[siril]], these can be saved into a library of master frames for use in future sessions. Thanks to [[FITS]], they store the conditions in the metadata thus you will never forget which frame corresponds to which conditions.
## Bias frame
CCD sensors provide an electronic offset signal so that ADCs always get a positive signal. This adds a constant value to all the pixels. To subtract it, you can capture a **bias frame** by keeping the lens cap on and shooting with the shortest exposure time possible. In theory this should be a constant, but you will get a little bit of noise with this method. Instead, you can compute the average and manually specify it in a [[FITS]] `OFFSET` keyword.

## Dark frame
The sensor also has some thermal noise that depends on the ambient temperature and exposure time. Because of the *temperature* requirement, these should be taken around the same time as the light frames (or the same temperature somehow). Normally, you would take these at the *end* or in the *middle* of the session.

- Same exposure time as the light frames, but with the shutter closed

## Flat frame
Because of things like dust particles and sensor properties, we need to divide each light frame by a *flat* frame that is taken of an evenly lit area. See [[how-flats-correct-lights]] for details.

## Cosmetic Correction
In addition to calibration frames, [[siril]] has support for automatically detecting hot and cold pixels by comparing values to nearest neighbours. It can do this using the master dark frame, and there are some tools for reasoning about the results (e.g. if >1% of pixels were determined to be hot, theres probably something wrong). You can also manually specify a file containing bad pixels.

# Registration
Registration is where you physically align the images with respect to a reference image from a light sequence so that they can be processed.
1. Detect features to be matched in each image
2. Compute transformations between each image and the reference
3. Apply the transformations
Depending on the registration method, Siril will pick sensible defaults about whether or not to apply a given transformation. Read [[siril-registration]] for more details.

# Stacking
The final step in preprocessing is stacking the lights. The theory here is that you increase the signal to noise ratio by sampling the same random process many times. See [[siril-stacking]] for more details.