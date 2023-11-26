# Analog Digital Units
[Reference](http://spiff.rit.edu/classes/phys445/lectures/gain/gain.html)

On a CCD, photons knock electrons free which are then read by an ADC and reported as pixel values.
1. Electrons are transferred to a capacitor which holds a certain charge in **coulombs**
2. The voltage induced by this charge ($V = \frac{Q}{C}$) is measured in **volts**
3. An [[analog-digital-converter|ADC]] converts the voltage into a discrete voltage
4. The discrete voltage is converted into a number that is stored as "Data Numbers" or "Analog to Digital Units" - ADUs. This is what is stored in the [[camera-raw-file]]
Steps 3 and 4 scale the result by an arbitrary value - relative pixel values stay the same.

[[spectral-response]]