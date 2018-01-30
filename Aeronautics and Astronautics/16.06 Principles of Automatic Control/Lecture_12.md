<sup>16.6 Principles of Automatic Control | Lecture 12</sup>

## Root Locus Rules
#2
•	Rule 1	The n branches of the locus start at the n poles of L(s). m branches end at the zeros of L(s). n - m branches end at s = 8.
•	Rule 2	The locus covers the real axis to the left of an odd number of poles and zeros.

To the left of the pole, φ = 180˝
To the left of a zero, Ψ = 180˝.

![fig_id](images/12/root-locus-rules.svg "Title Text")

To the right of a pole, φ = 0^0 To the right of a zero, Ψ = 0^0. So,

if m1 + n1 is oﬀ, where

m1 = number of zeros to the right of s
n1 = number of poles to the right of s

•	Rule 3 For large k, n - m of the loci are asymptotic to the lines emanating from the point s = 8, with angles

where

Why? If s -> 8, k -> 8,then to highest order the equation

becomes

So the solution satisﬁes

To get the point s = α, do asymptotic analysis with next terms: Result is that center of pattern is at:

A related rule, not in FPE, is:

•	Rule 3a If n - m >= 2, the centroid of the closed-loop poles is constant, and is at

To show this, consider a polynomial with roots z1, z2, ... The polynomial is then

Therefore, a1 = -sum(pi).

Now, the closed loop polynomial is given by

That is, the ﬁrst term to change in the polynomial is the an´mterm. If n - m >= 2, the a1term is unchanged, and the centroid is a constant.

Note that if m poles go to the m zeros zi, the centroid of the remaining n - m poles must go to

in agreement with rule 3.

•	Rule 4 The angle(s) of departure of a branch of the locus from a pole of multiplicity q is

and the angle(s) of arrival of a branch at a zero of multiplicity q is given by

where the sum sum()˚ excludes to poles (or zeros) at the point of interest.

Example:

![fig_id](images/12/example.svg "Title Text")
