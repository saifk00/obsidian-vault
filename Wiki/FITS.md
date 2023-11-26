The Flexible Image Transport System, or FITS, is the standard astronomical data format used by professional scientists (incl. NASA). It is *more* than just an image format - it stores multidimensional data.

A FITS file consists of one or more header and data units (HDUs). Each HDU contains a list of keyword records in the format `KEYNAME = value / comment`. The last keyword is the END keyword.