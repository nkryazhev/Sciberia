<sup>16.6 Principles of Automatic Control | Lecture 11</sup>

## Метод корневого годографа

Часто бывает очень удобно узнать как изменяются полюса замкнутой системы при изменении какого либо одиночного параметра. Для этого используется _метод корневого годографа_.

**Корень** - корень $s$ полиномиального уравнения.

**Годограф** - набор точек.

Рассмотрим систему управления вида

**diag**

If both K(s) and G(s) are rational, then the loop gain may be expressed as

$$
K(s)G(s) = kL(s)
$$

где

$$
\begin{align*}
L(s) &= \frac{n(s)}{d(s)}\\
n(s) &= s^m + b_1 s^{m-1} + \ldots + b_m\\
 &= (s - z_1)(s - z_2)\ldots(s - z_m)\\
 &= \prod_{i=1}^m (s - z_i)\\
 d(s) &= s^n + a_1 s^{n-1} + \ldots + a_n\\
  &= \prod_{i=1}^n (s - z_p)
\end{align*}
$$

Then the roots of the closed-loop system occur at:

$$
1 + K(s)G(s) = 0  \tag{$\star$}
$$

or

$$
1 + kL(s) = 0  \tag{$\star$}
$$

or

$$
L(s) = - \frac{1}{k}  \tag{$\star$}
$$

or

$$
d(s) + kn(s) = 0  \tag{$\star$}
$$

The root locus is the set of values $s$ for which ($\star$) holds, and $k$ is any positive real value. (For reasons that will become clear later, this is the definition of the _positive_ or _180 degree_ locus. Will later define the _negative_, or _0 degree_ locus.)

Пример:


В этом случае,

$$
\begin{align*}
L(s) &= \frac{1}{s(s + 1)},\; n(s) = 1\\
d(s) &= s(s + 1) = s^2 + s\\
Нули:& \; \text{нет}\\
Полюсы:& \; p_i = 0, -1
\end{align*}
$$

Характеристическое уравнение имеет вид:

$$
s^2 + s + k = 0
$$

Because characteristic equation is quadratic, we can find the roots using the quadratic for­mula:

$$
s = - \frac{1}{2} \pm \frac{\sqrt{1 - 4k}}{2}
$$

When $0 \leq k \leq \frac{1}{4}$, the roots are real, and between $-1$ and $0$. For $k>\frac{1}{4}$, the roots are complex, with real part $-\frac{1}{2}$ , and imaginary part that increases (asymptotically) as $\sqrt{k}$.

Suppose our goal is to choose $k$ so that $\zeta = \sin \theta = 0.5 \Rightarrow\theta = 30^\circ$.

Looking at the geometry in the figure, the imaginary part is

$$
\begin{align*}
\operatorname{\mathbb{I}m}(s) &= \frac{-\operatorname{\mathbb{R}e}(s)}{\tan \theta}\\
R(s) &= -\frac{1}{2}\\
\tan \theta &= \frac{\sin 30^{\circ}}{\cos 30^{\circ}} = \frac{1/2}{\sqrt{3}/2} = \frac{1}{\sqrt{3}}\\
\Rightarrow \operatorname{\mathbb{I}m} (s) &= \sqrt{3}/2\\
Но \operatorname{\mathbb{I}m} (s) &= \frac{\sqrt{4k - 1}}{2}\\
k &= 1
\end{align*}
$$

Пример:

Построить корневой годограф для системы


В этом случае

Характеристиеское уравнение имеет вид

Because the polynomial is cubic, we can’t find the roots (easily) in closed form. Nevertheless, can sketch the root loci using root loci sketching rules

Немного практики и вы научитесь строить корневые годографы очень быстро.

Guidelines for Sketching Root Locus

Will give rules for k > 0.
For k > 0 and 1 + kL(s) = 0 must have that
negative real number
That is, the phase of the L(s) must be:
where l is an integer.

This is the root locus phase condition, and the reason we call the locus for k > 0 the
180^0 locus.

Consider the example above:

The phase of L(s) is given by

To see if a given point is on the locus, could measure all the angles, add/subtract, and test result. This used to be done mechanically with a “spirule”. However, it’s only important to be able to sketch general shapes; Matlab can do the rest.

Root Locus Rules

Rule 1
The n branches of the locus start at the n points of L(s). m branches end at the zeros of L(s). n ´ m branches end at s “ 8.

Rule 2
The loci cover the real axis to the left of an odd number of poles and zeros.
To the left of the pole, φ = 180^0
To the left of a zero, Ψ = 180˝.
