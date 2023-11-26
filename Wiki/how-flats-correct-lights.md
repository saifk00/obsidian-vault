#siril #astrophotography

In astrophotography, we must preprocess *light* frames which contain our actual image data using three types of calibration frames: bias, dark, and flat. The model used by [[siril]] is as follows (note that *noise* is not a consideration - that goes away by *stacking lights*):

$$
	L = a - b\left(x - \frac{W}{2}\right)^2 + d_{\text{rate}}t_{\text{lights}} + o
$$

That is, a light frame contains a **spatial illumination** component that is quadratic - the maximum value is $a$ - in the middle of the frame ($x = \frac{W}{2}$). The *dark current* $d_{\text{rate}}t_{\text{lights}}$ varies with the exposure time $t$ but does not depend on the position of the pixel. Finally, there is the CCD offset $o$. We have the following data from calibration frames:
$$\begin{align}
	D &= d_{\text{rate}}t_{\text{lights}} + o\\
	F &= K\left\{a - b\left(x - \frac{W}{2}\right)^2\right\} + o\\
	O &= o
\end{align}$$
where D is the dark frame, F is the flat, and O is the bias/offset. By not illuminating the dark frames, we set the spatial illumination component of D to 0.

Since we illuminate the flats heavily and evenly, we get a factor $K>1$ in the spatial illumination which increases the intensity. This is true provided pixels respond linearly to the number of photons gathered - which is a sensible assumption. It is further assumed that this intensity is enough to make the dark current 0, which is true provided the exposure time for the flats is not too high. #conjecture usually we pick an exposure time that gives us a nice, centred histogram.

The unit of measurement here is [[analog-digital-units|ADUs]]

# Solution
The **goal** here is to set $L$ to 1. This is because what we get in our light frames is $L$ *times* the actual data that we want (remember sensor values are linear wrt photons). So to solve these equations, we do this:
$$
	L_c = \frac{L-D}{F - O} = \frac{1}{K}
$$
[[siril]] can automatically determine $K$ to further normalize this to 1 through `Auto evaluate normalization value`.

# Observations
If you haven't shot darks, then you are better off calibrating you lights with just the offset ($\frac{L-O}{F-O}$); otherwise you will get inverse vignetting.

If you can at least shoot *one* dark, you can measure its median and subtract that synthetic value from the lights.