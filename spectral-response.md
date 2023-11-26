# Spectral Response
See [[radiometry-and-photometry]] for some background before reading this.

[The Spectral Response of Digital Cameras](https://www.strollswithmydog.com/camera-spectral-sensitivity/)
- The optical system (camera) has an *aggregate spectral response* which describes how different wavelengths of light will result in different [[radiometry-and-photometry|irradiance]]. 
- A sensor measures light over some wavelength range $\lambda \pm \frac{1}{2}\Delta$ where $\Delta$ is ~5-10nm
	- By measuring the power, we get the radiance caused by that wavelength (which, collecting results over all wavelengths, gives us the radiance distribution).
- All components:
	- Lens
	- UV/IR filter [[hot-mirror]]
	- (older cams) antialiasing-filter, AR coated clear glass
	- [[color-filter-array|CFA]] dyes
	- > at this point, we have units of W/sr/m^2/nm (radiance/wavelength)
	- > we then convert radiance to photons/m^2 using [[photons-emitted-by-light-source]]
		- Energy of photon is $\frac{hc}{\lambda}$  [J/ph] , so dividing radiance by that gives us ph/sr/m^2/nm
		- For a proportional value: just multiply radiance by nm

