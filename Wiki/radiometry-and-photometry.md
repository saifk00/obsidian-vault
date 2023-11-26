# Radiometry and Photometry
**Radiometry** concerns the distribution of radiation in space. **Photometry** is concerned with the interaction of *visible light* with the human eye. Both refer to the same physical process - the transfer of energy by radiation - but seen from two distinct vantage points.

The key point is that [Lumens are how Watts are perceived](https://www.strollswithmydog.com/converting-radiometric-to-photometric-units/) by the eye. Watts is a quantity of energy per second; it describes the rate at which energy is transferred by radiation. However, the human eye perceives only radiation in the *visible spectrum* - which represents some fraction of the total energy delivered by the impinging radiation. This fraction is precisely what **Lumens** measure.

Thus, **Lumens** are the *fundamental* unit of photometry. All other photometric SI units are some expression of lumens over space and time.

# Flux
Radiant flux is a radiometric quantity. It forms a scalar field over space where, at a given point, the radiant flux is the amount of energy transferred per unit time by [[radiation]] (i.e. **radiant energy**. Thus, the SI unit is Watts. It is denoted as follows
$$
	\Phi = \frac{dQ}{dt}
$$
Note that the flux can be about a radiating *source*, or about an area *on* or *through* which the emitted radiation is received. In general, when we *detect* radiation, we measure the *total flux* over some area (for example, the power received in a pixel on a camera's sensor).


The related photometric quantity is **Luminous flux** which is measured in Lumens.

# Irradiance and Illuminance
Irradiance is the *area density* of radiant flux. The distribution of flux over this area may be *non-uniform*, thus the proper definition is:
$$
E = \frac{d\Phi}{ds_0}
$$
Thus, irradiance is a *function of the position* on the specified surface. **NB** this is sometimes called *exitance* when referring to emitted radiation, but in the literature there is actually no distinguishing term for the irradiance leaving a surface vs. coming into it - generally the latter case is assumed.

> [!quote]
> "Irradiance has meaning only with respect to a point on a surface in space. When speaking of irradiance, one should be careful both to describe the surface and to indicate at which point on the surface the irradiance is being evaluated"
> 
> *Introduction to Radiometry and Photometry, Second Edition*
# Radiant and Luminant Intensity
Imagine some radiating source, for example a lightbulb. We measure its radiant flux by collecting all the energy from some 2D surface (call this the 'receiving area') in space onto a sensor. For example:
![[Pasted image 20231126144316.png]]

now, this flux is actually a property of this whole source-sensor setup.

Why? Well for one, if we moved further away, we would receive less flux. So lets control for that - divide the flux by the amount of [[steradians]] subtended by the receiving area. Let's call this new quantity the **radiant intensity**. If we move twice as far away, the flux will drop by half, but we will divide that by $\frac{1}{2}$ because of our control factor (moving twice as far a way halves the steradians subtended) and thus end up with the same quantity. The units of **radiant intensity** are thus Watts per steradian. This also controls for the size of our sensor apparatus - if it doubles then so does the flux and steradians subtended, keeping intensity constant.

This is usually only used for point sources [1]. For extended sources, we must also consider the size of the patch *on the source* from which this energy emanates. This is fine for the radiometry of stars for example. Also, the term *intensity* is often used in subdisciplines of physics to refer to irradiance.

# Radiance and Luminance
Radiance is the most general of the radiometric quantities. Both the source from which and the point through/on which the flux is received must be specified *in addition* to the direction between them.
- [ ] Explain this

# Conversion from Radiance to Luminance
Let the radiometric function be $\Phi_e(\lambda)$. The photometric function $\Phi_v$ in lumens is simply the integration of the former function across the visual spectrum. The one caveat is that this integral is *weighted* because the human eye has a [[spectral-response]] that looks something like a bell curve. During the day, this curve is [centered](https://www.wikiwand.com/en/Spectral_sensitivity) around 555nm, and 507nm at night. This function is denoted $V(\lambda)$ and thus the integral looks like:

$$
\Phi_v(\lambda) = K_m \int\Phi_{e}(\lambda)V(\lambda)d\lambda
$$
Note that due to the bell curve shape we don't need explicit integral limits, but if needed one can use 380nm and 780nm as the lower and upper limits respectively,


# Observations
This is why, held at the same power, a green LED will look brighter than a red one. The lumens we perceive are higher in the former case despite the radiance being the same.

# Further Reading
- [[photons-emitted-by-light-source]]
# References
[1] Introduction to Radiation and Photometry, Second Ed.
[2] https://depts.washington.edu/mictech/optics/me557/Radiometry.pdf
