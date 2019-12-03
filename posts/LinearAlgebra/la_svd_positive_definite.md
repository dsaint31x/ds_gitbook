# Positive Definite Matrices
@(LinearAlgebra)

### Definition: 

$$A \in \mathbb{R}^{n \times n}$$ is **positive definite** if $$\textbf{x}^T A \textbf{x} > 0, \forall \textbf{x} \ne \textbf{0}$$.

### Definition: 
$$A \in \mathbb{R}^{n \times n}$$ is **positive semi-definite** if $$\textbf{x}^T A \textbf{x} \ge 0, \forall \textbf{x} \ne \textbf{0}$$.

## Theorem: 

$$A \in \mathbb{R}^{n \times n}$$ is positive definite if and only if the eigenvalues of $$A$$ are **all positive**.

* Proofs in Lay Ch7.2

## Note : Symmetric Positive Definite Matrices and Spectral Decomposition

• If $$S \in \mathbb{R}^{n \times n}$$ is **symmetric** and **positive-definite**, then the spectral decomposition will have all positive eigvenvalues: 

$$
\begin{align*}
S = UDU^T &= \begin{bmatrix} \textbf{u}_1 & \textbf{u}_2 & \cdots & \textbf{u}_n\end{bmatrix} \begin{bmatrix} \lambda_1 & 0 & \cdots & 0 \\
0 & \lambda_2 & \ddots & \vdots \\
\vdots & \ddots & \ddots & 0 \\
0 & \dots & 0 & \lambda_n \end{bmatrix}
\begin{bmatrix} \textbf{u}_1^T \\ \textbf{u}_2^T \\ \vdots \\ \textbf{u}_n^T\end{bmatrix} \\
&=  \lambda_1\textbf{u}_1\textbf{u}_1^T+\lambda_2\textbf{u}_2\textbf{u}_2^T+\cdots+\lambda_n\textbf{u}_n\textbf{u}_n^T
\end{align*} 
$$

where $$\lambda_j \ge 0, \forall j=1, \cdots, n$$.


