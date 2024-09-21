# Accuracy of the Least-Squares Solution $\alpha^*$   
- When computing the least-squares solution $\alpha^*$ to the problem $A\alpha = b$, we always have to solve the system of normal equations $(A^TA)\alpha^* = A^Tb$.
- **Problem:** Depending on the condition number of matrix $A^TA$, we can obtain a solution which is not accurate in double precision arithmetic.