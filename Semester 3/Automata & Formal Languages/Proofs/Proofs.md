The class of Regular languages is closed under the union operation.

Closure Under the regular Operations

Regular languages is closed under the Concatenation Operations

Regular Languages is closed under the star operation

  

  

  

  

  

  

  

  

  

  

  

  

  

  

  

  

  

  

  

# The class of Regular languages is closed under the union operation.

M1 = (Q1, Σ, δ1 , q1 , F1),

M2 = (Q2, Σ, δ2 , q2 , F2),

M = M1 ∪ M2

M = (Q, Σ, δ, q0 , F)

1. Q = {(r1 , r2 )| r1 ∈ Q1 and r2 ∈ Q2 }
    
    Cartesian Product of Q1 and Q2
    
2. Σ = Σ1 ∪ Σ2
3. δ ((r1 , r2 ), a) = (δ1 (r1 , a), δ2 (r2 , a))
    
    while a ∈ Σ
    
4. qo is the pair (q1, q2)
5. F = {(r1 , r2 )| r1 ∈ F1 or r2 ∈ F2 }

  

# Closure Under the regular Operations

N1 = (Q1 , Σ, δ1 , q1 , F1 )

N2 = (Q2 , Σ, δ2 , q2 , F2 )

N = N1 ∪ N2

N = (Q, Σ, δ, q0 , F )

1. Q = {q0 } ∪ Q1 ∪ Q2 .
2. q0 is the start state
3. set of accept states = F = F1 ∪ F2

![[../../../Attachments/Untitled 50.png|Untitled 50.png]]

# Regular languages is closed under the Concatenation Operations

N1 = (Q1 , Σ, δ1 , q1 , F1 )

N2 = (Q2 , Σ, δ2 , q2 , F2 )

1. Q = Q1 ∪ Q2
2. The state q1 is the same as the start state of N1 .
3. The state q1 is the same as the start state of N1 .

![[../../../Attachments/Untitled 1 22.png|Untitled 1 22.png]]

# Regular Languages is closed under the star operation

N1 = (Q1 , Σ, δ1 , q1 , F1 )

N = (Q, Σ, δ, q0 , F )

1. Q = {q0 } ∪ Q1
2. The state q0 is the new start state
3. F = {q0 } ∪ F1 .

![[../../../Attachments/Untitled 2 18.png|Untitled 2 18.png]]