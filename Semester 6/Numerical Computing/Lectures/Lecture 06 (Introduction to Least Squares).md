# Inconsistent System of Equations
- The following are inconsistent system of 3 equations in 2 unknowns:
	1. $2x_1 - x_2 = 3$
	2. $x_1 + 2x_2 = 7$
	3. $2x_1 - x_2 = 4$
- **Problems:** The left-hand side of the first ad thirst equations are the same, while the right-hand side is different. Thus we can say that there does not exist a vector $x \in \mathbb{R}^2$ which satisfies the three equations simultaneously. 
- However we can still be interested in finding a vector x which is *close enough to be a solution*, since this kind of problem arises frequently in all the cases where the number of equations *m* is greater the number of unknowns *n*.
# Solving an Inconsistent System of Equations
- In other words, starting from a system of equations in the form:
$$
Ax = b
$$
- With a matrix of coefficients $A \in \mathbb{R}^{m \times n}$ and right hand side $b \in \mathbb{R}^n$, we are interested in finding the vector $x \in \mathbb{R}^n$ which minimizes the following quantity.
$$
||Ax - b||^2_2 = 0
$$
- The least-square solutions x* can be found by solving the system of *normal equations*:
$$
(A^TA)x^* = A^Tb
$$
# Quality of the Approximation: Residual Vector
- After we have computed the least square solution x*, we can evaluate the quality of our approximation by computing the residual vector $r \in \mathbb{R}^n$, which is defined as follows:
$$
r = b - Ax^*
$$
- Of course, fit he system is **consistent** and r = 0, the solution $x^*$ corresponds to the exact solution of the given system of equations. If instead -- as we expect -- we have that $r \neq 0$, we need to define some metrics to measure the quality of our approximation.
# Quality of the Approximation: Metrics
1. The **Euclidean Norm** of the residual, which is simply given by:
$$
||r||_2 = \sqrt{\sum^n_{i=1}r^2_i}
$$
2. The **SE**, or squared error, simply corresponding to:
$$
SE = ||r||^2_2 = \sum_{i+1}^nr^2_i
$$
3. The **RMSE**, or root-mean-square error, which is given by
$$
RMSE = \sqrt{\frac{SE}{m}} = \frac{||R||_2}{\sqrt{m}}
$$
# Exercise 1
![[../../../Attachments/Pasted image 20231123160923.png|675]]

![[../../../Attachments/Pasted image 20231123161006.png|675]]
![[../../../Attachments/Pasted image 20231123161057.png|675]]
![[../../../Attachments/Pasted image 20231123161339.png|675]]
![[../../../Attachments/Pasted image 20231123161412.png|675]]
# Least Square Fitting of a Model to Data
- Sometimes we are given a set of data and we interested in developing and testing a model which summaries the dataset in the best possible way.
- For example, we can have a collection of point in the plane $(x_1, y_1), ...., (x_m, y_m)$ and we can be interested in finding their best approximation, given a specific class of models. We could, e.g., consider a linear model as $y = \alpha_1 + \alpha_2x$, where $\alpha_1$ and $\alpha_2$ represents the unknown coefficients that we need to calculate on the basis of our data points.
- Least square can be considered an example of data compression: in other words, we want to find a model (with the smallest number possible of parameters) which fits the data points in the Euclidean norm. The model obtained can then be used to make predictions and explore scenarios beyond the data points we have collected with our measurements. 
## How to Fit Data by Least Squares
- Given a dataset consistent of $m$ data points $(x_1, y_1), ...., (x_m, y_m)$, we do the following:
	1. **Model selection:** We pick the class of models which will be sued to fit the data. An example could be given by the linear model $y = \alpha_1 + \alpha_2x$.
	2. **Write the system in the form $Ax = b$** We force the model to fit the data by inserting each of the $m$ data points inside the model. This will result in $m$ equations with $n$ unknowns (in case of the linear model $y = \alpha_1 + \alpha_2x$ we have $n = 2$), that can be easily written down in matrix form as explained at the beginning of the lecture.
	3. **Find the least-squares solution:** The least-squares solution can be found by solving the system of normal equations arising from the system $Ax = b$
	4. **Evaluate the Model:** Compute the Euclidean norm of the residual, the Se and the RMSE to evaluate the quality of the approximation given by the chosen model and, eventually to compare it against another candidate model.