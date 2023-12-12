There is a device file for the framebuffer - `/dev/fb`. 

What happens when you operate on a device file?
- E.g. open()
	- it loads the inode, which for device files contains an `i_rdef` field containing the major/minor number of the device. There is a kernel object which stores pointers to the `write, read, ioctl, etc.` operations for the file. The kernel then sets this to point to the *device driver's* implementation of these operations; thus from now on any read/write/etc. of the device file will call into the device driver instead of the kernel routine.