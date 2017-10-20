<sup>16.06 Principles of Automatic Control | Lecture 4</sup>


# Block Diagram Manipulations:

![Cхема 1](images/4/block-diagram-1.svg)

![Cхема 2](images/4/block-diagram-2.svg)

![Cхема 3](images/4/block-diagram-3.svg)

>The gain of a single loop feedback system (with sign “-1” in the loop) is the forward gain divided by the sum of 1 plus the loop gain.

![Cхема 4](images/4/block-diagram-4.svg)

So,

![Cхема 5](images/4/block-diagram-5.svg)


Mason’s Rule:

$$
\begin{align*}
 H(s)     & = \frac{1}{\Delta} \sum_{i} H_i \Delta_i                                \\
 H(s)     & = \text{losed-loop transfer function}                                   \\
          & = 1-\sum \text{all loop gains}                                          \\
          & =\; + \sum \text{(products of 2 loops that don't touch)}                \\
          & =\; - \sum \text{(products of 3 loops that don't touch)}                \\
          & = \dots                                                                 \\
 H_i      & = i^{th}\;\text{forward path}                                           \\
 \Delta_i & = \text{determinant of}\;i^{th}\;\text{path}                            \\
          & = \text{value of D for that part of diagram that does not touch path i}
\end{align*}
$$

**Example**

![Пример](images/4/example.svg)

$$H(s) = \frac{G_1 G_2 G_3}{1 + G_1 G_2 + G_2 G_3}$$
