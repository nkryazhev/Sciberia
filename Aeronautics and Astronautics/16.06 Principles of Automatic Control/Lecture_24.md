<sup>16.6 Principles of Automatic Control | Lecture 24</sup>

## Compensation
Compensation is the use of a dynamic controller Kpsq (as opposed to proportional control)
to improve the system’s stability and error characteristics.
We have already seen compensation when we did root locus control, but we can do compensation
more systematically using frequency response techniques.

We look primarily at four types of compensation:
+ PD Control used primarily to add lead at the crossover frequency, allowing the
Lead Compensation c
used primarily to add lead at the crossover frequency, allowing the
Lead Compensation compensated system to have a faster speed of response and/or
have more damping.

PI Control used primarily to increase the frequency response magnitude
Lag Compensation at low frequencies, reducing steady-state tracking errors.

Example:
Control the plant

so that the rise time of the step response is

and the overshoot is

Solution:
We must first translate this requirements into frequency response characteristics. For a
second order system,

So effective ζ required is

Using the relationship

we see that the required phase margin is about 59˝. So (rounding), require that PM “ 60˝.
Next, figure out what the crossover frequency is. By dimensional analysis, know that

Generally, will have

For other, more reasonable values of PM,

So let’s try

What must loop look like?

Image 1

To get PD correct, need 60˝ phase lead from PD zero,

Since phase of Gpsq is ´180˝ everywhere, the phase is

To get 60˝at ωc, need

If we use unit gain, what is |KG| at crossover? Using straight line

Image 2

Using exact expressions,

So controller is

Check results: Using Matlab, found that:

Part of the problem is that phase lag increases below crossover, increasing Mr, and therefore
the peak overshoot. This will hopefully become a bit clearer when we do the Nichols plot.
Could fix by increasing PM to « 80˝.
One problem with PD controller is that the gain is infinite at high frequencies. So instead
use lead compensator 
