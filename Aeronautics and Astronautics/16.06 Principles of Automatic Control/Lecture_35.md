<sup>16.6 Principles of Automatic Control | Lecture 35</sup>


Higher Harmonic Control
Helicopters and other rotating machinery often have serious vibration at multiples of the
rotation speed, or harmonics.
To eliminate vibration, need to have


be zero at S “ jNΩ,
where
Ω “ roatation rate in r/s
N “ harmonic to be controlled.
Therefore, need to have

To achieve this, K must have an oscillator at ωn “ NΩ, ζ “ 0. So

But usually need a zero as well, because we want the pole on the jω axis to move directly
left, at a departure angle of 180˝.
Often, “low gain” control in OK, so the time constant T of the system can be long. That is,
the closed-loop poles associated with the oscillator will be at

where T is large, compared to 1{Ω.

Image 1


For a given Gpsq, how do we get poles at desired location?

We could use Root locus methods; however, we don’t really know Gpsq,we only know Gpjωq.

Where are roots of 1 ` KpSqGpsq ?

If we take

 then near s “ jNΩ,

 Using this approximation and setting KG “ ´1at s “ ´T
1 ` jNΩ, we find

Example:


 Root locus

 Image 2

 
