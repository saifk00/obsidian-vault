#siril
[[siril]]

[Siril Docs](https://siril.readthedocs.io/en/stable/file-formats/Bit-depth.html)

The bit-depth of an image is the number of bits used for each color channel. 8-bits is usually enough for daily life, but for astronomical imaging, we need at least 16 bits of depth, and 32 bits is also common. 64 bits is possible in the [[FITS-image-format]] but is not common. Not all file formats support 16/32 bits!

Some common image formats include jpeg, png, and the (outdated) `bmp`. PNG does support up to 16 bit depths, and is a good choice for saving a final image that has been processed. [[TIFF]] is a good choice as it supports up to 32 bits, and there is even a pseudo-standard called Astro-TIFF that is specifically for astronomical imaging. [[FITS]] is the de-factor standard for astronomical data. 

SER is used in Siril for *sequences* of images.