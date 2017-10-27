<sup>16.6 Principles of Automatic Control | Lecture 13</sup>

## Root Locus Rules (cont-d)

•	Rule 5 The locus crosses the jω axis at points where the Routh criterion shows a transition in the number of unstable roots.

Example:

The characteristic equation is

The Routh array is

So the transitions occur at k = 8, -1.Look at locus:

For k = 8,the characteristic equation is

which has roots at

jω axis crossing

•	Rule 6 The locus will have multiple roots at points on the locus where

(see FPE for details)

Example:

where does locus depart/arrive real axis?

as in recitation!

Lead Compensator Example

For the plant

ﬁnd a unity feedback controller with compensator K(s) such that

If the closed loop system is second order, the poles would need to have

So set to allow some margin.

This would place poles at

To simplify, want poles at

Look at locus with gain only:

So gain only doesn’t work - must add lead compensation:

where α < β.

Then rough locus will be

Must choose α, β, k to make this work.

We have multiple degrees of freedom, so answer is not unique. Let’s ﬁx
α = 3

to guarantee the real closed-loop pole settles faster than complex poles. Then β must be selected to achieve desired angle condition.
