# Orthogonality and Orthonormality

## Orthogonal Sets

* Definition: A set of vectors $$\left\{\textbf{u}_1, \textbf{u}_2, \cdots, \textbf{u}_p \right\}$$ in $$\mathbb{R}^n$$ is an **orthogonal set** if each pair of distinct vectors from the set is orthogonal. That is, if $$\textbf{u}_i\cdot\textbf{u}_j=0$$ whenever $$i\ne j$$.

## Orthonormal Sets

* Definition: A set of vectors $$\left\{\textbf{u}_1, \cdots, \textbf{u}_p\right\}$$ in $$\mathbb{R}^n$$ is an orthonormal set if it is an orthogonal set of **unit vectors**.

> **Note**
>
> An orthogonal (or orthonormal) set is also a linearly independent set.

## Orthogonal and Orthonormal Basis

Consider basis $$\left\{\textbf{v}_1, \cdots, \textbf{v}_p\right\}$$ of a $$p$$-dimentional subspace $$W$$ in $$\mathbb{R}^n$$.
In this case, we can make it as an orthogonal (or orthonormal) basis by **Gram-Schmidt process**. 

QR factorization : In this method, we break into a matrix by **Gram-Schmidt Orthogonalization**.

## Orthogonal Projection $$\hat{\textbf{y}}$$ of $$\textbf{y}$$ onto one-diemensional subspace $$L$$.

$$ 
\hat{\textbf{y}} = \text{proj}_L \textbf{y} = \frac{\textbf{y} \cdot \textbf{u}}{\textbf{u} \cdot \textbf{u}} \textbf{u}
$$

if $$\textbf{u}$$ is a unit vector,

$$
\hat{\textbf{y}} = \text{proj}_L \textbf{y} = \left(\textbf{y} \cdot \textbf{u}\right) \textbf{u}
$$

## Orthogonal Projection $$\hat{\textbf{y}}$$ of $$\textbf{y}$$ onto Plane

Consider the orthogonal projection $$\hat{\textbf{y}}$$ of $$\textbf{y}$$ onto two-dimensional subspace $$W$$.

$$
\begin{align*}
\hat{\textbf{y}} &= \text{proj}_L \textbf{y} \\
&= \frac{\textbf{y} \cdot \textbf{u}_1}{\textbf{u}_1 \cdot \textbf{u}_1} \textbf{u}_1
+ \frac{\textbf{y} \cdot \textbf{u}_2}{\textbf{u}_2 \cdot \textbf{u}_2} \textbf{u}_2
\end{align*}
$$

If $$\textbf{u}_1$$ and $$\textbf{u}_2$$ are unit vectors,

$$
\begin{align*}
\hat{\textbf{y}} &= \text{proj}_L \textbf{y} \\
&= \left(\textbf{y} \cdot \textbf{u}_1\right)\textbf{u}_1
+ \left{\textbf{y} \cdot \textbf{u}_2}\right)\textbf{u}_2
\end{align*}
$$

Projecton is done independently on each orthogonal basis vector.


## Orthogonal Projection $$\hat{\textbf{y}}$$ of $$\textbf{y}$$ onto Plane $$W$$ when $$\textbf{y} \in W$$

Consider the orthogonal projection $$\hat{\textbf{y}}$$ of $$\textbf{y}$$ onto two-dimensional subspace $$W$$, **where $$\textbf{y} \in W$$.

$$
\begin{align*}
\hat{\textbf{y}} &= \text{proj}_L \textbf{y} \\
&= \frac{\textbf{y} \cdot \textbf{u}_1}{\textbf{u}_1 \cdot \textbf{u}_1} \textbf{u}_1
+ \frac{\textbf{y} \cdot \textbf{u}_2}{\textbf{u}_2 \cdot \textbf{u}_2} \textbf{u}_2 \\
&= \textbf{y}
\end{align*}
$$

If $$\textbf{u}_1$$ and $$\textbf{u}_2$$ are unit vectors,

$$
\begin{align*}
\hat{\textbf{y}} &= \text{proj}_L \textbf{y} \\
&= \left(\textbf{y} \cdot \textbf{u}_1\right)\textbf{u}_1
+ \left{\textbf{y} \cdot \textbf{u}_2}\right)\textbf{u}_2 \\
&= textbf{y}
\end{align*}
$$

## Transformation: Orthogonal Projection

Consider a transformation of orthogonal projection $$\hat{\textbf{b}}$$ of $$\textbf{b}$$, 
given **orthonormal basis** $$\left\{\textbf{u}_1$$,\cdots, $$\textbf{u}_2\right)$$ of a subspace $$W$$:

$$
\begin{align*}
\hat{\textbf{b}} &= f(\textbf{b}) = (\textbf{b} \cdot \textbf{u}_1)\textbf{u}_1 +(\textbf{b} \cdot \textbf{u}_2)\textbf{u}_2 \\
&= \left(\textbf{u}_1^T\textbf{b}\right) \textbf{u}_1 + \left(\textbf{u}_2^T\textbf{b}\right) \textbf{u}_2 \\
&= \textbf{u}_1\left(\textbf{u}_1^T\textbf{b}\right)  + \textbf{u}_2\left(\textbf{u}_2^T\textbf{b}\right) \\
&= \left(\textbf{u}_1\textbf{u}_1^T\right)\textbf{b}  + \left(\textbf{u}_2\textbf{u}_2^T\right)\textbf{b} \\
&= \left(\textbf{u}_1\textbf{u}_1^T+\textbf{u}_2\textbf{u}_2^T\right)\textbf{b}  \\
&= \begin{bmatrix}\textbf{u}_1 & \textbf{u}_2 \end{bmatrix} \begin{bmatrix} \textbf{b}_1^T \\ \textbf{b}_2^T\end{bmatrix} \\
&= UU^T\textbf{b} \rightarrow \text{linear transformation}
\end{align*}
$$

