<sup>﻿16.06 Principles of Automatic Control | Lecture 9</sup>

# Unity Feedback Control With Noise

Consider a typical unity feedback control system

pic1.
disturbance
sensor noise

$e'$  is the error perceived by the control system; e is the actual
error.  The important transfer functions  are

$$
\begin{align*}
\frac{Y}{R}(s) &= \frac{1}{1 + K(s)G(s)} \equiv S(s)\\
\frac{E}{D}(s) &= \frac{-1}{1 + K(s) G(S)} \equiv -S(s)\\
\frac{E}{V}(s) &= \frac{-K(s)G(s)}{1 + K(s)G(s)} \equiv -T(s)
\end{align*}
$$

S(s) = Sensitivity transfer function
T(s) =Complementary Sensitivity transfer function

For low sensitivity to disturbances, want:

\[
\left| S(s) \right| \ll 1
\]

For good tracking of the reference input, want:

\[
\left| S(s) \right| \ll 1
\]

For low sensitivity to sensor noise or errors, want:

\[
\left| T(s) \right| \ll 1
\]

But these goals are mutually exclusive, since

$$ S(s) + T(s) =  1$$

So there is a fundamental trade-oﬀ between good tracking performance and low sensitivity to sensor noise.

How is this trade-oﬀ addressed?

In most (not all) systems, want good tracking performance at low frequency, low sensitivity to sensor noise at high frequency:
-	Reference inputs are low frequency
-	Sensor noise is usually high frequency
So let’s look at the lowest frequency, $\omega = 0$  $(s = 0)\dots$

Steady-State Errors

Consider a unity feedback system without sensor noise or disturbance:
For stability, deﬁne

$$L(s) = K(s) G(s) = \text{"Loop Gain"}$$

What is the steady-state error to a unit step input?

Use LTs:

$$E(s) = S(s) R(s) = \frac{1}{1 + L(s)} R(s) = \frac{1}{1 + L(s)}\frac{1}{s}$$

To ﬁnd the steady error, use ﬁnal value theorem:

$$\lim_{s \to 0} e(t) = \lim s E(s) = \frac{1}{1+ L(0)}$$

If $L(0)$ is ﬁnite, we deﬁne

$$K_p \equiv L(0) = \text{"positive error constant"}$$

Furthermore, if $L(0)$ is ﬁnite, we say that a system is a “type 0 system”.

So a type 0 system will always have a ﬁnite error in response to a steady input r, but the
error can be made small by making the position error constant large.

To make the steady error zero, we must have that $L(0)$ is inﬁnite. Suppose we can express L(s) as

$$L(s) = \frac{L_0(0)}{s}$$

where $L_0(0) \ne 0$, $L_0(0)$ is ﬁnite. Then L is a “type 1 system” (one pole at $s = 0$). We have that

$$\lim_{s \to 0} e(t) = \lim_{s \to 0} s \frac{1}{1 + \frac{L_0(s)}{s}s} \frac{1}{s} = \lim_{s \to 0} \frac{s}{s + L_0(s)} = 0$$

since $L_0(0) \ne 0$.

What if we want to track a unit ramp instead?

\[
\begin{align*}
r(t) &= tr(t)\\
\Rightarrow\; R(s) &= \frac{1}{s^2}
\end{align*}
\]

The steady-state error for a type 0 system will be

\[
\begin{align*}
e_{ss} &= \lim_{s \to 0} sS(s) R(s)\\
&= \lim_{s \to 0} s \frac{1}{1+L(s)} \frac{1}{s^2}\\
&= \lim_{s \to 0} \frac{1}{1 + L(0)} \frac{1}{s} = \infty
\end{align*}
\]

The steady-state error for a type 1 system will be

\[
\begin{align*}
e_{ss} &= \lim_{s \to 0} sS(s) R(s)\\
&= \lim_{s \to 0} s \frac{1}{1+\frac{L_0(s)}{s}} \frac{1}{s^2}\\
&= \lim_{s \to 0} \frac{1}{s + L_0(s)}\\
&= \frac{1}{L_0(s)}
\end{align*}
\]

which is ﬁnite.  We deﬁne

$$K_v = L_0(s) = \text{"velocity error constant"}$$

More generally, suppose that $L(s)$ has the form

$$L(s) = \frac{L_0(s)}{s^n}$$

$L$ is said to be a type $n$ system, and the error constant is $K_p$,or $K_v$  or $K_a\dots\; = L_0(0)$.

\[
\begin{align*}
K_p &= K_0 = \lim_{s \to 0} L(s), \; n = 0\\
K_v &= K_1 = \lim_{s \to 0} sL(s), \; n=1\\
K_a & = K_2 = \lim_{s \to 0} s^2 L(s), \; n=2\\
&\;\; \vdots
\end{align*}
\]

Obviously, this generalizes, but we usually care most about $K_p$ and $K_v$ - higher order inputs are rare.
