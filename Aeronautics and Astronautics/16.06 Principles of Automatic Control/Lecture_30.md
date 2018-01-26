<sup>16.6 Principles of Automatic Control | Lecture 30</sup>


Z-transform Inversion
There are 3 ways to invert a Z-transform:
1. Partial Fraction Expansion
Example

Using coverup method

But we don’t know the inverse transform of z´
1
a .
Instead, do PFE as

2. Inverse transform integral

where the integral is counter-clockwise around the origin in the region of convergence. If the
integral is done using residues, this method reduces to method 1.
3. Long division
There is no analog to this in continuous time!1
By expanding Fpzq in powers of 1{z, can obtain samples frks directly.

Example:

Do long division:

In practice, not very practical2, but can be easily implemented to directly obtain, say, step
response.

Relationship between s and z.
Consider a continuous-time signal

Its Laplace transform is

with pole at s “ ´a. The z-transform of the sampled signal fpkTq is

with pole at z “ e´at. Therefore, there is a natural mapping

between s-plane and the z-plane. For example, if we want a system to have natural frequency
ωn and damping ratio ζ, in the z-plane the poles should be at

Image 1

Observations:
1. The stability boundary is |z| “ 1.
2.	 The region near s “ 0 maps to the region z “ 1. For reasonable sampling rates, this is
where all the action is.
3.	 The z-plane pole locations give response information normalized to the sample rate, not
to dimensional time as in s-plane. So the meaning of, say, z “ 0.9 depends on the
sampling rate.
4.	 z “ ´1 corresponds to ω “ ωs{2, where ωs “ 2π{T “sample rate in radians/sec. ωs{2 is
the Nyquist frequency.
4

5. Vertical lines in s-plane (constant ζωn) correspond to circles centered at z “ 0 in z-plane.
6. Horizontal lines in s-plane (constant ωd) correspond to radial lines from z “ 0 in z-plane.
7.	 Frequency greater than ωs{2 overlap lower frequencies in the z-plane. This is called
aliasing. So should sample at least twice as fast as highest frequency component in
Gpsq and rptq.

Design by Emulation
Can either design directly using, say, root locus in z-plane, or can design in continuous time,
and discretize the continuous controller. Must then verify that the design works, of course.
The book suggests three methods:
1. Tustin’s approximation
2. Matched Pole-Zero Method (MPZ)
3. Modified MPZ
Will start with...
Tustin’s approximation
We have found that

We can approximate z by

or we can approximate z´1 by

The more symmetric approximation


has some useful properties. Inverting, we have

 Replacing every occurrence of s by the RHS of (2) in a given Kpsq is Tustin’s method, or the
bilinear transform. It results in a discrete controller, Kdpzq, that is a good approximation to
Kpsq.

Example: For the plant

find a controller for the unity feedback, discrete-time system, with sample time T “ 0.025
sec (40 Hz sampling), with ωc “ 10 r/s, and PM “ 50˝.
First, let’s design for the continuous system

Image 2

Need to add a lead compensator at crossover to get desired PM. Compensator is

then

3 ways to actually compute Kdpzq:

1. Actually do the substitution indicated above (ugh!)
2. Use the Matlab command
kd “ c2dpk, 0.025, 1
tustin1
q
3. Map the poles and zeros of Kpsq
