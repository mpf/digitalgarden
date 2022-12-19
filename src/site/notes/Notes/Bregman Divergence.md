---
{"dg-publish":true,"permalink":"/notes/bregman-divergence/"}
---


> See [[Notes/Relative Entropy\|Relative Entropy]]

Let $f:\Re^n\to\Re$ be a function of the _Legendre type_, which implies that $\nabla f \circ \nabla f^* = \text{Id}$.

The Bregman divergence induced by $f$ is the function
$$
D_f(x,y) = f(x) - [f(y) - \ip{\nabla f(y)}{x-y}].
$$

## Examples

1. KL Divergence (simplex domain). Let $f(x) = x\log x$ be the **negative** entropy function, which is convex. Then
$$
\begin{align}
  D_f(x,y) &= \sum_{i}x_{i}\log x_{i} - y_{i}\log y_{i} - \langle \log y + e), x-y \rangle\
           &= \sum_{i}x_{i}\log(x_{i}/y_{i}) - x_{i} + y_{i},
\end{align}
$$
where the log function operates componentwise when applied to vectors.

In the multidimensional case, if we have $\sum_i x_i = \sum_i y_i = 1$, this expression reduces to $D_f(x,y) = \sum_i x_i\log(x_i/y_i)$, which is the **relative entropy** between $x$ and $y$.

By convention, we take $0\log 0=0$. When dealing with probabilities, we also make the convention that $x

2. Exponential. Let $f(x) = \exp(x)$. Then
$$
\begin{align}
  D_f(x,y) &= (\exp x -x) - (\exp y - y).
\end{align}
$$

## Properties

1. Linearity in the generator: $D_{f_1+f_2} = D_{f_1} + D_{f_2}$
2. Dual form: $D_f(x,y) = D_{f^*}(∇f(y),∇f(x))$
3. Gradient: $∇_xD_f(x,y) = ∇f(x)-∇f(y)$
4. Linear invariance in the generator: If $g$ is linear, $D_{f+g}=D_f$

## Convexity

The divergence $D_f(x,y)$ is convex in $x$, but may not necessarily be convex in $y$. Here's a [simple counterexample](https://en.wikipedia.org/wiki/Bregman_divergence#Properties) based on using the scalar absolute value function as the generator: $f=|\cdot|$: take $y=1$, and $(x_1,x_2,x_4) = (0.1, -0.9, 0.9)$, and observe that $D_{f}(y,x_3)\approx 1 > 0.9D_f(y,x_1) + 0.1D_f(y,x2) \approx 0.2$.

## KL-Divergence

Let's compute the dual form of the KL divergence. It's convenient to work with a version of negative entropy that contains a linear term, and so for this section only we define $f(x) = \sum_i^n x_i\log x_i - x_i$. The linear-invariance property above ensures that the generated function continues to be the KL divergence. The conjugate function is $f^*(y) = \exp y$. Let's compute the dual KL function:
$$
\begin{align*}
\KL_*(v,w) &:= D_{f^*}(∇f(w),∇f(v)) \\
          &= f^*(∇f(w)) - f^*(∇f(v)) - \ip{∇f^*(v)}{∇f(w)-∇f(v)}
\end{align*}
$$

