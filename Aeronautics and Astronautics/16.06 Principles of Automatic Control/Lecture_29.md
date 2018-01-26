<sup>16.6 Principles of Automatic Control | Lecture 29</sup>


Digital Control
At one time, most control systems were implemented using analog devices (operational amplifiers,
linear circuit elements, etc). Today, most control systems are implemented using
digital devices (computers, etc.)
The use of digital devices leads to systems which implement difference equations in discrete
time rather than differential equations in continuous time. This will require some new tools,
but much will be familiar.

Basic block diagram:

Image 1

Basic Components:
Sampler - Captures value of continuous time signal periodically so that A/D converter can
read it
Analog-to-digital (A/D) converter - converts samples continuous signal to discrete (binary
encoded) signal. Often, 8, 12, or 14 bits.

Controller - Implemented on a computer, which implements a difference equation, much as
a continuous-time controller is an implementation of a differential equation on analog
components.
Digital-to-analog (D/A) converter - Converts a binary word to an analog signal.
Zero Order Hold - Holds a constant value analog signal for one period.

Discrete Time Control Time line

Image 2

If the control computer is dedicated to a single task, then T is made as short as possible,
and δ “ T.
If the computer has many tasks, then T is longer, and δ ! T. In that case, can take δ “ 0.
Of course, can have anything in between.
For our purposes, we will assume one of the extremes, i.e., either δ “ 0, or δ “ T. Of course,
can generalize to other cases.

Analysis of Discrete Systems.
Our system is a sampled-data system, meaning that it contains both discrete and continuous
signals. However, we can treat it as a discrete system, by treating the dynamics from vpkTq
to ypkTq as discrete.
Discrete systems are a lot like continuous systems - they have step responses, pulse (not
impulse) responses, and transfer functions. The counterpart of the Laplace Transform is the
Z-Transform.

Z-Transform
The Z-transform of a sequence frks is given by

Note: I am using the bilateral transform.
For every interesting property that you learned for the Laplace transforms, there is a corresponding
z-transform property.

For instance,

 (similar to Lrf9ptqs “ sFpsq )

Using this property, can always differentiate equations. E.g.,

yrks “ ´a1yrk ´ 1s ´ a2yrk ´ 2s ` b0urks ` b1urk ´ 1s ` b2urk ´ 2s
Z-transform both sized to obtain
Y psq “ p´a1z´1 ´ a2z´2qY pzq ` pb0 ` b1z´1 ` b2z´2qUpzq
So the transfer function from u to y is

Some Select Transforms

Table
