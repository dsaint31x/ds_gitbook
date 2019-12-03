# Symmetric and Hermitian Matrix
@(LinearAlgebra)

## Symmetric Matrix

$$
a_{ij} = a_{ji} \leftrightarrow A^T=A
$$

## Hermitian Matrix

$$
a_{ij} = \bar{a}_{ji}(=a^*_{ji}) \leftrightarrow \bar{A}^T = A^H  = A
$$

* Diagonal entries들을 기준으로 entry들이 complex conjugate관계임.
* Hermitian Matrix $$\supset$$ Symmetric Matrix

## Properties of Hermitian Matrix

1. All Hermitian matrices have eigenvalues of real number.
2. In the Hermitian matrices, all eigenvectors are orthonormal respectively.

### Proof

#### 1.

$$
A\textbf{x} = \lambda \textbf{x} \rightarrow \textbf{x}^H A \textbf{x} = \textbf{x}^H \lambda \textbf{x} = \lambda \textbf{x}^H  \textbf{x} 
$$
* $$\lambda$$ is an eigenvalue so that it's just a scalar.
* So, it can be moved the first position

$$
\left( \textbf{x}^H A \textbf{x}\right)^H = \textbf{x}^H A^H \textbf{x}^{HH}  = \textbf{x}^H A \textbf{x}
$$
* $$A$$ is an Hermitian matrix.
* $$\textbf{x}^H A \textbf{x}$$ also is a scalar, so that it never be an complex number. ($$\because s^H = s \rightarrow s\text{ is a real number.}$$)


* $$\textbf{x}^H \textbf{x} $$ 역시 항상 real number임 ($$\because (a+bj)(a-bj)=a^2+b^2$$)

$$
\textbf{x}^H A \textbf{x} = \lambda \textbf{x}^H \textbf{x} \\
\lambda = \frac {\textbf{x}^H A \textbf{x}} {\textbf{x}^H \textbf{x}}
$$
* $$\textbf{x}^H A \textbf{x}$$와 $$\textbf{x}^H \textbf{x} $$가 real number이므로, $$\lambda$$도 real number임.

#### 2.

* eigenvalue $$\lambda_1, \cdots \lambda_n$$이 서로 다르다고 가정하고, 이에 대응하는 eigenvector $$\textbf{x}_1 \cdots \textbf{x}_n$$ 이 있다고 하자. 이 경우,

$$
\begin{align*}
\lambda_1\textbf{x}_1^H\textbf{x}_2 &= \left( \lambda_1 \textbf{x}_1\right)^H \textbf{x}_2 \\
&= (A \textbf{x}_1)^H\textbf{x}_2 \\
&= \textbf{x}_1^H A^H \textbf{x}_2 \\
&= \textbf{x}_1^H A \textbf{x}_2 \\
&= \textbf{x}_1^H \lambda_2 \textbf{x}_2 \\
&= \lambda_2 \textbf{x}_1^H \textbf{x}_2 \\
\end{align*}
$$

* 즉, $$\lambda_1\textbf{x}_1^H\textbf{x}_2 = \lambda_2 \textbf{x}_1^H \textbf{x}_2 $$가 성립.
* eigenvalue들이 각각 다르다고 했으므로, 이 등식이 성립하려면 다음이 성립해야함.

$$
\textbf{x}_1^H\textbf{x}_2 = 0
$$

* 이는 inner product가 0인 경우로, $$\textbf{x}_1$$와 $$\textbf{x}_2$$가 orthogonal임을 의미함.
* 모든 orthogonal 한 관계의 vector들은 length를 1로 만들 수 있으므로 orthonormal한 관계가 성립하게 됨.

## Eigendecomposition

$$
A=PDP^{-1}
$$
where
* $$P$$ : eigenvvector들을 column vector로 가지는 eigenvector matrix 
* $$D$$ :$$P$$의 column vector들에 대응하는 eigenvalue들을 diagonal entries로 가지는 diagonal matrix. eigenvalue matrix로 불리기도 하며 $$\Lambda$$로 표기되기도 함.

### $$A$$가 symmetric matrix인 경우,

$$
\begin{align*}
A &= QDQ^{-1} \\
&=Q\Lambda Q^{-1} \\
&=Q\Lambda Q^{T} \\
\end{align*}
$$
where
* $$Q$$ is an eigenvector matrix like $$P$$. All eigenvectors of symmetric matrix can be orthonormal!

### Diagonalization of Symmetric Matrices

* In general, $$A \in \mathbb{R}^{n \times n}$$ is diagonalizable if and only if $$n$$ linearly independent eigenvectors exist.
* How about a symmetric matrix $$S \in \mathbb{R}^{n \times n}$$, where $$S^T = S$$?
* $$S$$ is **always diagonalizable**.
* Furthermore, $$S$$ is **orthogonally diagonalizable**, meaning that their eigenvectors are not only linearly independent, but also orthogonal to each other. 

### Spectral Theorem of Symmetric Matrices

Consider a symmetric matrix $$S \in \mathbb{R}^{n \times n}$$, where $$S^T = S$$.
* $$A$$ has $$n$$ real eigenvalues, counting multiplicities.
* The dimension of the eigenspace for each eigenvalue equals the multiplicity of $$\lambda$$ as a root of the characteristic equation.
* The eigenspaces are mutually orthogonal. That is, eigenvectors corresponding to different eigenvalues are orthogonal.
• To sum up, $$A$$ is orthogonally diagonalizable.
• Proofs in Lay Ch7.1

### Spectral Decomposition

Eigendecomposition of a symmetric matrix, also known as spectral decomposition, is represented as

$$
\begin{align*}
S = UDU^{-1} = UDU^T &= \begin{bmatrix} \textbf{u}_1 & \textbf{u}_2 & \cdots & \textbf{u}_n\end{bmatrix} \begin{bmatrix} \lambda_1 & 0 & \cdots & 0 \\
0 & \lambda_2 & \ddots & \vdots \\
\vdots & \ddots & \ddots & 0 \\
0 & \dots & 0 & \lambda_n \end{bmatrix}
\begin{bmatrix} \textbf{u}_1^T \\ \textbf{u}_2^T \\ \vdots \\ \textbf{u}_n^T\end{bmatrix} \\
&=  \begin{bmatrix} \lambda_1\textbf{u}_1 & \lambda_2\textbf{u}_2 & \cdots & \lambda_n\textbf{u}_n\end{bmatrix}\begin{bmatrix} \textbf{u}_1^T \\ \textbf{u}_2^T \\ \vdots \\ \textbf{u}_n^T\end{bmatrix} \\
&=  \lambda_1\textbf{u}_1\textbf{u}_1^T+\lambda_2\textbf{u}_2\textbf{u}_2^T+\cdots+\lambda_n\textbf{u}_n\textbf{u}_n^T
\end{align*} 
$$

* Each term, $$\lambda_i\textbf{u}_i\textbf{u}_i^T$$  can be viewed as a projection matrix onto
the subspace spanned by $$\textbf{u}_i$$, scaled by its eigenvalue $$\lambda_i$$
.

#### Note
* $$A$$가 실수이며, symmetric matrix인 경우, A의 eigenvector들은 orthonormal이므로 이들을 column vector로 가지는 $$Q$$는 **orthonormal matrix(or orthogonal matrix, 직교행렬)** 임.
* 이 경우, $$Q^{-1}=Q^T$$임.

## $$A$$가 Hermitian matrix인 경우,

$$
\begin{align*}
A &= UDU^{-1} \\
&=U\Lambda U^{-1} \\
&=U\Lambda U^{H} \\
\end{align*}
$$
where
* $$U$$ is an eigenvector matrix like $$P$$ and $$Q$$. $$U$$ is an **unitary matrix**

## Unitary matrix

다음이 성립하는 matrix.

$$
U^HU = I, U^H = U^{-1}
$$

* 모든 column vector들이 orthonormal임.
* 모든 eigenvalue들의 절대값이 1임.
* Unitary matrix는 normal matrix의 하나임.

#### Note
Fourier Transform을 matrix multiplication으로 표현할 경우, 사용되는 matrix(Fourier matrix라고 불림)는 Unitary matrix임.

## Normal matrix(정규행렬)

complex square matrix 중 다음을 만족하는 matrix A를 normal matrix라고 부름.

$$
AA^H = A^HA
$$





