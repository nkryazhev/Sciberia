<sup>16.6 Principles of Automatic Control | Lecture 31</sup>

Example (continued)
We will use the third method. The zero and pole are at

Therefore,

The determine k1
, match K and Kd at convenient point. Usually use

In our case

Therefore,


which agrees with the Matlab c2d command (using ’tustin’ option).

How well does controller work?

Must first determine Gdpzq. Assuming no processing delay, can find Gd using Matlab:

gd=c2d ( g , 0 . 0 2 5 , ‘ zoh ’ )

which yields

Can use Matlab to compare step responses for continuous and discrete systems (next page).
Note that

Why is discrete worse?

Image 1

Look at Bode plots of GK, GdKd below. The magnitude plots agree well out to 50 r/s, well
beyond ωc “ 10 r/s. However, the phase plots are significantly different, even at ωc. At ωc,
the difference in the phases is 7.2˝. This additional phase lag completely accounts for the
increased overshoot.
To see where the phase comes from, look at Bode plot of G, Gd and K, Kd separately. Note
that at ωc “ 10 r/s, almost all the additional phase comes from the discretization of G1, not K

Image 2

Image 3

Image 4

The phase lag in Gd is due to the effect of the zero order hold. To see why, consider sampling
then holding a sinusoidal signal:

Image 5

Note that the reconstructed signal is delayed by about 1{2 the sample period, so there is an
additional phase lag of ωT{2. At crossover, this lag is

This is precisely the additional phase lag seen in the Bode plots!

Compensator Redesign
Since we (now) understand that the ZOH adds phase lag at crossover, we should incorporate
that lag from the beginning when we do discrete design. Let’s do that now:

To get PM “ 50˝, need


where 7.2˝ “ 2 π for this case.
Using a centered lead compensator, we get

So take

Must also choose gain, so that crossover is at ωc “ 10. Net result is

Convert to discrete time by hand or by Matlab c2d to obtain

See step response below.

Image 6
