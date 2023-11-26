#siril 

Siril manipulates *sequences* of images. A sequence is a set of manipulated files, for example the set of [[astrophoto-dark|dark]] images that will be turned into a master dark. These can be either [[FITS]] files, or a single [[siril-file-formats|SER]] file. In fact, because of the flexibility of FITS we can store the entire sequence in a single FITS file by placing each image in its own HDU while maintaining their headers. This method is called FITSEQ in Siril.
