<small>16.06 Principles of Automatic Control</small>

# Lecture 8

### Критерий устойчивости Рауса-Гурвица

Suppose we have a transfer function:

Допустим у нас есть передаточная функция:

$$T(s) = \frac{Y(s)}{R(s)}\frac{b_0 s^m + b_1 s^{m-1} + \dots + b_m}{s^n + a_1 s^{n-1} + \dots
+ a_n}$$

We can always factor as

$$T(s)=\kappa \frac{\prod_{i=1}^m (s - z_1)}{\prod_{i=1}^n (s - p_1)}$$

The closed-loop system is stable if

Замкнутая система устойчива если выполянется условие
$$\mathfrak{R}(p_1) < 0, \forall\; i $$

**NB:** It might turn out that there are pole-zero cancellations, that is, $z_i = p_j$ for some $i.j$. If this happens, system is still unstable if

$$\mathfrak{R}(p_1) > 0$$

The _characteristic equation_ is:

_Характеристическое уравнение_ имеет вид

$$\phi(s) = s^n + a_1 s^{n-1} + \dots + a_{n-1} s + a_n =0$$

The roots are, of course, $p_1, p_2,\dots p_n$.

Его корни соответственно $p_1, p_2,\dots p_n$.

**Important question:** Can we tell if the system is stable, without actually solving for the roots?

**Важный вопрос:** Можем ли мы сказать устойчива ли система, при этом не вычисляя корни?

**Partial answer:** A necessary condition for all the roots to be stable is that all the coeﬃ­ cients of $\varphi(s)$ be positive. So if at least one coeﬃcient is negative, system must be unstable.
A complete answer to the question is obtained using the Routh Array.  The array is con­ stracted as bellow:

**Частичный ответ** Необходимое условие устойчивости для всех корней это чтобы все коэффицента в $\varphi(s)$ были бы положительными. Если хотя бы один коэффицент будет отрицательным - система будет неустойчивой. Полный ответ на этот вопрос определяется используя таблицу Рауса.

$$
\begin{matrix} \text{Ряд}\; n:\;\;\;\;\; & 1 & a_2 & a_4 & \cdots
       \\ \text{Ряд}\; n-1: & a_1 & a_3 & a_5 & \cdots
       \\ \text{Ряд}\; n-2: & b_1 & b_2 & b_3 & \cdots
       \\ \text{Ряд}\; n-3: & c_1 & c_2 & c_3 & \cdots
       \\ \vdots   &  &   \ddots &  &
       \\ \text{Ряд}\; 2:\;\;\;\;   & *   & *      &  &
       \\ \text{Ряд}\; 1:\;\;\;\;   & * & & &
       \\ \text{Ряд}\; 0:\;\;\;\;   & * & & &
 \end{matrix}
$$

The ﬁrst two rows come directly from the polynomial $\varphi(x)$. Each subsequent row is formed by operations on the two rows above:

Первые два ряда берутся напрямую из коэффицентов полинома $\varphi(x)$. Каждый последующий ряд вычисляется на основе двух предшествующих ему рядов:

$$
\begin{eqnarray}
    b_1 & = & - \dfrac{\begin{vmatrix}
	1 & a_2 \\
	a_1 & a_3
    \end{vmatrix}}{a_1} = \dfrac{a_1 a_2 - a_3}{a_1} \nonumber \\
    b_2  & = & - \dfrac{\begin{vmatrix}
	1 & a_4 \\
	a_1 & a_5
    \end{vmatrix}}{a_1} = \dfrac{a_1 a_4 - a_5}{a_1} \nonumber \\
    c_1 & = & - \dfrac{\begin{vmatrix}
	a_1 & a_3 \\
	b_1 & b_2
    \end{vmatrix}}{b_1} = \dfrac{b_1 a_3 - a_1 b_2}{b_1} \nonumber \\
\end{eqnarray}
$$

The number of unstable poles is the number of sign changes in the ﬁrst column of the array.

Количество неустойчивых полюсов это количество смен знаков в первом столбце таблицы.

#### Example:
Пример

$$\phi(s) = s^3 + 2 s^2 + 3 s + 8$$

The Routh Array is

Таблица Рауса имеет вид

$H_0$ is
$$
\begin{matrix} 3: & 1 & 3 & 0
            \\ 2: & 2 & 8 & 0
            \\ 1: & -1 & 0 &
            \\ 0: & 8 & &
            \\ & \downarrow
\end{matrix}
$$

First column has two sign changes!
There are two unstable poles. In fact, the roots are:

Первый столбец имеет две смены знаков, т.е. существует два неустойчивых полюса. Собственно вот корни уровнения.

$$
\begin{align*}
    -2,2483\\
0,1241 + 1,8822 i\\
0,1241 - 1,8822 i
\end{align*}
$$

**Note:** We can scale any row of the array by a positive constant, and not change the sign of any of the terms. This can simplify the algebra by eliminating fractions.

**Замечание** Мы можем масштабировать любой столбец таблицы с умножая или деля на положительную константу и это не повлияет на знаки элементов таблицы. Такой метод поможет упростить вычисления и избавиться от дробей.

### Stability vs. Parameter Range

Устойчивость против разброса параметров

It’s much easier to use a calculator or Matlab to ﬁnd roots. So why use Routh?

Кажется что гораздо легче использовать калькулятор, ну или Матлаб для того что бы найти корни. Так зачем там тогда Раус?

Routh allows us to determine symbolically what values of a parameter will lead to stability/instability.

Критерий Рауса позволяет нам определить символьно(не вычисляя) какие величины параметров влияют на устойчивость/неустойчивость

#### Пример:

For what values of $k$ is the following system stable?

Для значений $K$ следующая система будет устойчива?

**Решение:**

The Closed Loop transfer function is:
Передаточная функция замкнутой системы имеет вид:
$$
\begin{eqnarray*}
T(s) & = & \frac{KG(s)}{1 + KG(s)} = \dfrac{\dfrac{K}{(s + 1)^3}}{1 + \dfrac{K}{(s + 1)^3}} \\
& = & \dfrac{K}{(s + 1)^3 + K} \\
& & \\
\Rightarrow \phi(s) & = & s^3 + 3 s^2 +3 s + 1 + K
\end{eqnarray*}
$$

The Routh array is

Таблица Рауса

$$
\begin{matrix} 3: & 1 & 3 & 0
            \\ 2: & 3 & 1 + K & 0
            \\ 1: & \frac{8 - K}{3} & 0 &
            \\ 0: & 1 + K & 0
\end{matrix}
$$
For stability, need ﬁrst column to be positive, so that $K < 8$ and $K > -1$.
If $K < -1$, ﬁrst column is $+ + + -$, so there is $1$ unstable pole.
If $K > 8$, ﬁrst column is $+ + - +$, so there are $2$ unstable poles.

Для устойчивости системы нужно чтобы первый столбец был весь положителен, это произойдет при $K < 8$ и $K > -1$.

Если $K < -1$, первый столбец имеет $+ + + -$, т.е. одна смена знака значит один неустойчивый полюс. Если $K > 8$, первый столбец имеет $+ + - +$, т.е. здесь два неустойчивых полюса.

**Возможные проблемы:**
If the ﬁrst element of a row is zero, process fails.
Если первый элемент ряда равен нулю, весь процес неимеет смысла.

**Решение:** Replace $0$ by $\epsilon$, a small positive number.
If a whole row is zero, must replace row as explained in the book. This happens whenever there is a complex conjugate pair of roots on the imaginary axis.

Можно заменить $0$ на $\epsilon$ - очень маленькое полодительное число. Если весь ряд равен нулю, нужно заменить ряд как описано в книге (FPE?) Это происходит всякий раз когда присутствует коплексно-сопряженая пара корней на мнимой оси.
