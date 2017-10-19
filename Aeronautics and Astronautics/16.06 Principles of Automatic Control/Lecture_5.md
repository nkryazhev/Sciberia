16.06 Principles of Automatic Control | Lecture 5

## Dynamic Response:

Usually, we ﬁnd the response of a system using Laplace techniques. Often, do within Matlab.

**Example: DC Motor.**

Suppose:

\[
\begin{align*}
J &= 0,01\;kg\cdot m^2;\;b=0,001\;N-m-sec \\
\\
K_t &= K_e = 1\; n-M/A = 1\; V/(rad/sec)\\
\\
R_a &= 10\Omega,\; L= 1\; H
\end{align*}
\]


Then

\[
\begin{align*}
\frac{\Omega}{V_a}(s) &= \frac{100}{s^3 + 10,1 s^2 + 101 s}\\
\frac{\Omega}{V_a} &= \frac{s\Theta}{V_a}(s) = \frac{100s}{s^3 + 10,1 s^2 + 100s}\\
&= \frac{100}{s^2 + 10,1 s +101}\\
G(s) &= \frac{100}{(s+5,05 + j 8,6889)(s+5,05 + -j8,6889}
 \end{align*}
 \]

What is the step response of the motor?  That is, what is the velocity of the motor as a function of time, if $v_a (t) = \sigma (t)$?

By hand, would do:

$$\begin{align*}
g_s (t) &= L^{-1} \left[ \frac{1}{s} G(s) \right]\\\\
\frac{1}{s} G(s) &= \frac{100}{s(s + a + jb)(s+ a - jb)}\\\\
&= \frac{r_1}{s} + \frac{r_2}{s + a + jb} + \frac{r_3}{s + a - jb}
\end{align*}$$

Would ﬁnd $r_1 ,\; r_2 ,\; r_3$ by partial fraction expansion.
Then ﬁnd $L^{-1}$ of each term, add together, and simplify. A lot of work.

Instead, use MATLAB:

``` matlab
num = [0 0 100];
den = [1 10.1 101];
sysg = tf(num, den);
t = 0:0.01:5;
y = step(sysg,t);
plot(t,y);
```

The above code produces the following ﬁgure:

![sdsd]()

Figure 1: Velocity of the motor.

The above system was an open-loop system. Would do the same for a closed-loop system, after ﬁnding the transfer function.

Example:

The transfer function from aileron input (\(\delta_a\)) to roll angle (\(\varphi\)) is given by

$$\frac{\Phi}{\delta_a}(s) = \frac{k}{s(\tau + 1}$$

\[
\begin{align*}  
\text{where} \; k &= \text{steady roll-rate per unit of aileron deﬂection}\\
\tau &= \text{roll subsidence time constant}\\
&= \frac{I}{-M_{\phi}}
\end{align*}
\]


Suppose $\delta_a$ is measured in % of full deﬂection, so $\delta_a = 1$ is full right aileron, $\delta_a = -1$ if full left one. Then a typical set of parameters might be

$$
\begin{align*}  
k &= 100\; \text{deg/sec}\\
\tau & = 0,5\; sec\\
G(s) &= \frac{100}{s(0,5s + 1)}
\end{align*}
$$

Suppose we implement the following control law:

_diag_

What is the transfer function of a closed-loop system?

\begin{align*}  
H(s) &= \frac{KG(s)}{1+KG(s)} = \frac{\dfrac{Kk}{s(\tau s + 1)}}{1 + \dfrac{Kk}{s(\tau s + 1)}}\\
&= \frac{Kk}{\tau s^2 + s + Kk}
\end{align*}  

Suppose we take $K = 0,1/deg$.
Then:

\begin{align*}
H(s) &= \frac{10}{0,5 s^2 + s + 10}\\
H(s) &= \frac{20}{0,5 s^2 + 2s + 20}
\end{align*}

Find step response via MATLAB:

num=[0  0  20];
den=[1 2 20];
sysg=tf(num,den);
t=0:0.01:5;
y=step(sysg,t);
plot(t,y);
xlabel(’Time, t (sec)’);
ylabel(’Roll angle, \phi (deg)’);

Figure 2: Roll angle vs time.

The result (shown in Figure 2) is NOT very good. Oscillatory! More on this later.

Переведено на Нотабеноиде
http://translate.kursomir.ru/book/30/60

Переводчики: nkryazhev
