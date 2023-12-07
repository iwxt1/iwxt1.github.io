\noindent \textbf{Proof:}
First use the Lemma 1.1 to upper bound the regret:
\begin{align*}
\mathcal{R}_T &= \sum_{t=1}^T(x_t-y_t)^2 - \min_{x\in\left[0,1\right]}\sum_{t=1}^T(x-y_t)^2\\ &= \sum_{t=1}^T(x_{t-1}^*-y_t)^2 - \sum_{t=1}^T(x_T^*-y_t)^2 \\
&\leqslant \sum_{t=1}^T(x_{t-1}^*-y_t)^2 - \sum_{t=1}^T(x_t^*-y_t)^2 \\
\end{align*}
Let’s take a look at each difference in the sum in the last equation.
\begin{align*}
(x_{t-1}^*-y_t)^2 - (x_t^*-y_t)^2 &= (x_{t-1}^*-x_t^*)(x_{t-1}^*+x_t^*-2y_t) \\
&\leqslant \left|x_{t-1}^*-x_t^*\right|\left|x_{t-1}^*+x_t^*-2y_t\right| \\
&\leqslant 2\left|x_{t-1}^*-x_t^*\right| \\
&= 2\left|\frac{1}{t-1}\sum_{i=1}^{t-1}y_i - \frac{1}{t}\sum_{i=1}^{t}y_i\right| \\
&= 2\left| \left( \frac{1}{t-1}-\frac{1}{t}\right)\sum_{i=1}^{t-1}y_i - \frac{y_t}{t} \right| \\
&= 2\left| \frac{1}{t(t-1)}\sum_{i=1}^{t-1}y_i - \frac{y_t}{t} \right| \\
&\leqslant 2\left| \frac{1}{t(t-1)}\sum_{i=1}^{t-1}y_i \right| + 2\left| \frac{y_t}{t} \right|\\
&\leqslant \frac{2}{t} + \frac{2}{t} = \frac{4}{t}\;.
\end{align*}
So we have
\begin{align*}
\mathcal{R}_T &\leqslant 4\sum_{t=1}^T\frac{1}{t}\\
&\leqslant 4\left(1 + \int_{1}^{T} \frac{1}{t}\,dt \right)\\
&= 4 + 4\ln T\;.
\end{align*}