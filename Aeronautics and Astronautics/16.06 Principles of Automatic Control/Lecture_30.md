<sup>16.6 Principles of Automatic Control | Lecture 30</sup>


## Z-transform Inversion

There are 3 ways to invert a Z-transform:
### 1. Partial Fraction Expansion (PFE)

### Example

$$
F(z) = \frac{z}{(z - 1/2)(z - 1/3)}
$$

Using coverup method

$$
F(z) = \frac{3}{z - 1/2} - \frac{z}{z - 1/3}
$$

But we don’t know the inverse transform of $\frac{1}{z - a}$

Instead, do PFE as

$$
\begin{align*}
\frac{F(z)}{z} &= \frac{1}{(z - 1/2)(z - 1/3)}\\
&= \frac{6}{z - 1/2} - \frac{6}{z - 1/3}\\
\Rightarrow F(z) &= \frac{6z}{z - 1/2} - \frac{6z}{z - 1/3} \\
\Rightarrow f[k] &= ((1/2)^k - (1/3)^k)\sigma [k]
\end{align*}
$$

### 2. Inverse transform integral

$$
f[k] = \frac{1}{2 \pi j} \oint F(z) z^{k-1} dz
$$

where the integral is counter-clockwise around the origin in the region of convergence. If the
integral is done using residues, this method reduces to method 1.

### 3. Long division

There is no analog to this in continuous time![1]

[1] Actually, expanding Fpsq in powers of 1{s yields the infinite series (Taylor series) for fptq, which isn’t really that useful.

By expanding $F(z)$ in powers of $1/z$, can obtain samples $f[k]$ directly.

### Example:

$$
F(z) = \frac{z}{z - a} = \frac{1}{1-az}
$$

Do long division:

$$
  \begin{array}{rl}
  & \underline{1 + az^{-1} + a^2 z^{-2} + \dots}\\[-8pt]
    1 - az^{-1} &| 1\\
    & \underline{1 - az^{-1}}\\
    & \phantom{0} + az^{-1}\\
    & \phantom{0} \,\underline{+\:az^{-1} - a^2 z^{-2}}\\
    & \phantom{0000000}\; + a^2 z^{-2}\\
    & \phantom{00000000} \underline{+\: a^2 z^{-2} - a^3 z^{-3}}\\
  &  \phantom{00000000000000000000} \vdots
  \end{array}
$$

So $f[k] = a^k$, $k\geq0$


In practice, not very practical[2], but can be easily implemented to directly obtain, say, step
response.

### Relationship between $s$ and $z$.

Consider a continuous-time signal

$$
f(t) = \sigma (t) e^{-at}
$$

Its Laplace transform is

$$
F(s) = \frac{1}{s + a}
$$

with pole at $s = -a$. The z-transform of the sampled signal $f(kT)$ is

$$
F(z) = \frac{z}{z - e^{-et}}
$$

with pole at $z = e^{-at}$. Therefore, there is a natural mapping

$$
\boxed{z = e^{st}}
$$

between s-plane and the z-plane. For example, if we want a system to have natural frequency $\omega_n$ and damping ratio $ζ$, in the z-plane the poles should be at

$$
z = e^{(-\zeta\omega_n + j \sqrt{1 - \zeta^2 \omega_n})T}
$$

Image 1

Observations:
1. The stability boundary is $|z| = 1$.
2.	 The region near $s = 0$ maps to the region $z = 1$. For reasonable sampling rates, this is
where all the action is.
3.	 The z-plane pole locations give response information normalized to the sample rate, not to dimensional time as in s-plane. So the meaning of, say, $z = 0.9$ depends on the
sampling rate.
4.	 $z = -1$ corresponds to $\omega =\omega_s /2$, where $\omega_s = 2 \pi/T$ = sample rate in radians/sec. $\omega_s/2$ is the Nyquist frequency.
5. Vertical lines in s-plane (constant $\zeta \omega_n$) correspond to circles centered at $z = 0$ in z-plane.
6. Horizontal lines in s-plane (constant ωd) correspond to radial lines from $z = 0$ in z-plane.
7.	 Frequency greater than $\omega_s /2$ overlap lower frequencies in the z-plane. This is called aliasing. So should sample at least twice as fast as highest  frequency component in $G(s)$ and $r(t)$.

### Design by Emulation

Can either design directly using, say, root locus in z-plane, or can design in continuous time,
and discretize the continuous controller. Must then verify that the design works, of course.
The book suggests three methods:
1. Tustin’s approximation
2. Matched Pole-Zero Method (MPZ)
3. Modified MPZ

Will start with...

#### Tustin’s approximation

We have found that

$$
z = e^{sT}
$$

We can approximate $z$ by

$$
z \approx 1 + sT
$$

or we can approximate $z^{-1}$ by

$$
z^{-1} = e^{-sT} \approx 1 - sT \Rightarrow z \approx \frac{1}{1 - sT}
$$

The more symmetric approximation

$$
z \approx \frac{1 + sT/2}{1 - sT/2}
$$


has some useful properties. Inverting, we have

$$
s \approx \frac{2}{T} (\frac{z - 1}{z + 1})
$$

 Replacing every occurrence of s by the RHS of (2) in a given $K(s)$ is Tustin’s method, or the bilinear transform. It results in a discrete controller, $K_d(z)$, that is a good approximation to
$K(s)$.

Example: For the plant

$$
G(s) = \frac{1}{s(s+1)}
$$

find a controller for the unity feedback, discrete-time system, with sample time $T = 0.025$
sec (40 Hz sampling), with $\omega_c = 10$ r/s, and $PM = 50^\circ$.
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
