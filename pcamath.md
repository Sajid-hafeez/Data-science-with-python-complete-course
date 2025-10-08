# 🧮 Principal Component Analysis (PCA) — Mathematical Explanation (GitHub‑friendly)

> This version uses **$$ ... $$** math blocks so it renders on GitHub, VS Code, and most Markdown viewers that support math.

---

## 🎯 Goal

PCA finds **new orthogonal axes (principal components)** that:
1. Capture the **maximum variance** in the data.
2. Are **uncorrelated** (perpendicular).
3. Enable **dimensionality reduction** with minimal information loss.

---

## 1️⃣ Data Setup

Given a dataset:
$$
X =
\begin{bmatrix}
x_{11} & x_{12} & \dots & x_{1p} \\
x_{21} & x_{22} & \dots & x_{2p} \\
\vdots & \vdots & \ddots & \vdots \\
x_{n1} & x_{n2} & \dots & x_{np}
\end{bmatrix}
$$

- \( n \): number of samples  
- \( p \): number of variables

---

## 2️⃣ Center the Data

Subtract the mean of each column:
$$
X_{\text{centered}} = X - \mu
$$
where \( \mu \) is the vector of column means. After centering, each variable has mean 0.

---

## 3️⃣ Covariance Matrix

Compute the covariance matrix:
$$
\Sigma = \frac{1}{n-1} \, X_{\text{centered}}^{\top} X_{\text{centered}}
$$

---

## 4️⃣ Eigen Decomposition

Solve for eigenvalues and eigenvectors:
$$
\Sigma \, v_i \,=\, \lambda_i \, v_i
$$

- \( v_i \): eigenvector (direction of the \(i^{\text{th}}\) principal component)  
- \( \lambda_i \): eigenvalue (variance explained along that component)

---

## 5️⃣ Principal Components (Scores)

Project the data onto these directions:
$$
\operatorname{PC}_i \;=\; X_{\text{centered}} \, v_i
$$

Each \(\operatorname{PC}_i\) is the coordinate of every sample along the \(i^{\text{th}}\) component.

---

## 6️⃣ Order by Variance

Sort components by decreasing eigenvalues:
$$
\lambda_1 \ge \lambda_2 \ge \dots \ge \lambda_p
$$

- **PC1** captures the most variance.  
- **PC2** captures the next most, and is **orthogonal** to PC1, etc.

---

## 7️⃣ Dimensionality Reduction

Keep only the top \(k\) components:
$$
Z \,=\, X_{\text{centered}} \, V_k
$$
where \(V_k = [v_1, v_2, \dots, v_k]\) contains the top \(k\) eigenvectors (as columns).

---

## 8️⃣ Orthogonality (Perpendicularity)

Because \(\Sigma\) is **symmetric**, its eigenvectors can be chosen **orthonormal**:
$$
v_i^{\top} v_j \,=\, \delta_{ij} \quad (\text{so components are perpendicular for } i\neq j).
$$

---

## 9️⃣ Explained Variance Ratio

Contribution of each component to total variance:
$$
\text{Explained Variance Ratio}_i
\;=\;
\frac{\lambda_i}{\sum_{j=1}^{p} \lambda_j}
$$

---

## 🔢 Example (2D Case)

With two centered variables \(X_1, X_2\), the covariance matrix is
$$
\Sigma =
\begin{bmatrix}
\sigma_{11} & \sigma_{12} \\
\sigma_{12} & \sigma_{22}
\end{bmatrix}.
$$

Eigenvalues solve the characteristic equation:
$$
\bigl\lvert \, \Sigma \, - \, \lambda I \, \bigr\rvert \,=\, 0.
$$

The corresponding eigenvectors \(v_1, v_2\) give **two perpendicular axes** (PC1 and PC2).

---

## ✅ Summary Table

| Step | Operation | Formula / Concept |
|---|---|---|
| 1 | Center data | \( X - \bar{X} \) |
| 2 | Covariance matrix | \( \Sigma = \tfrac{1}{n-1} X^{\top} X \) on centered data |
| 3 | Eigen decomposition | \( \Sigma v = \lambda v \) |
| 4 | Sort by eigenvalues | Rank by variance \(\lambda\) |
| 5 | Compute scores | \( \text{PC} = X v \) |
| 6 | Reduce dimensions | \( Z = X V_k \) |

---

### 🛠 Notes on Markdown Math Compatibility
- Use **$$ ... $$** for block equations (more portable than `\[ ... \]`).  
- Avoid rare LaTeX packages; stick to basic MathJax/KaTeX syntax.  
- If your viewer still doesn’t render math, consider exporting to PDF or using a renderer like Obsidian, GitHub, or VS Code with a math extension.
