16.6 Principles of Automatic Control | Lecture 10

# PID Control

A common way to design a control system is to use PID control.

PID = proportional-integral-derivative Will consider each in turn, using an example transfer function

Proportional (P) control In proportional control, the control aw is simply a gain, to that u is proportional to e: For our example, the characteristic equation is The resulting natural frequency is So in the example, increasing kp increases the natural frequency, but reduces the damping ratio. Plot of pole location vs kp:

pic1\. increasing kp open loop pole location closed-loop pole location

Derivative (D) control To add damping to a system, it is often useful to add a derivative term to the control, or What is the characteristic equation? So increasing kD increases the damping ratio without changing the natural frequency, for this example. For kpﬁxed, kD varying, plot of closed-loop pole location is:

pic2\. pole position for kD = 0 pole position for kD > 0 increasing kD

NB: For other G(s), results may vary. Sometimes, it's better to place derivative feedback in the feedback path: Why? We get the same pole locations, but no additional zeros to cause additional overshoot. Another way to think about this is that we want the derivative eﬀect on y, because that adds damping, but we don't want to diﬀerentiate the reference.

Integral (I) control Especially if the plant is a type 0 system, we may want to add integrator to controller to drive steady-state error to zero:

Example: Suppose we want a system that

1. Has rise time above $t_r = 1\:s$
2. Has peak overshoot of $M_p = 0,05$
3. Has zero steady-state error to step command Let's do one piece at a time: Characteristic equation is

So can only change ωn (and indirectly, ζ) with kp. for tr = 1, need

So let's take kp = 2 for simplicity. Then To get Mp = 5%, need ζ = 0.7\. So add derivative control. Characteristic Equation is The desired polynomial is

So take kD = 1.8.

If PD control is in forward loop, and the peak overshoot will be 16%, not 5%. So instead, use control structure (˚) = "mirror loop feedback" With this structure, we have:

So let's add integral control: Take kI = 0.25 (trust me!) Then Response sort of meets specs: The response has a long tail, due to slow pole – poles are at: ^ slow pole causes long tail.
