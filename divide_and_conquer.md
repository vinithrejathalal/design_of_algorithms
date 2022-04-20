# Divide and Conquer

The divide-and-conquer technique involves solving a particular computational problem by dividing it into one or more subproblems of smaller size, recursively solving each subproblem, and then “merging” or “marrying” the solutions to the subproblem(s) to produce a solution to the original problem.

- **We have a problem $S(n)$ ($n$ is the size of the problem).**

We break it up into $k$ sub-problems $S(n_1),S(n_2),S(n_3)....S(n_k)$ of sizes $n_1,n_2,n_3....n_k$ respectively, solve them recursively and combine their solutions to get the solution of the larger problem $S(n)$

- Merge Sort, Quick Sort, Binary Search etc

Complexity of divide and conquer algorithms is computed using recurrence relations, as we have seen earlier.

## Master Theorem

Master theorem gives a cookbook method of determining the asymptotic characterization of a wide variety of recurrences.

It is used for recurrences of the form:

$T(n) = \begin{cases} c &\text{if} ~n < 1 \\aT(n/b) + f(n)~& n \geq d  \end{cases} $

where $d \geq 1$ is an integer constant and $a \geq 1, b>0, c>0$ are all real constants and $f(n)$ is a function that is positive for $n \geq d$

![master_theorem](master_theorem.png)

- Examples

   - $T(n) = 4T(n/2) + n $

       - $a = 4, b = 2, f(n) = n, f(n) = O(n^{log_b(a)}) = O(n^2)$
         Choose $\epsilon = 1$. Case 1 and therefore $T(n) = \Theta(n^2)$
   - $T(n) = 2 T(n) + nlog(n)$  : Case 2
   - $T(n) = T(n/3) + n$ : Case 3

------------------------------------------------------

## Integer Multiplication

- Two big integers $I$ and $J$ of $n$ bits each (assumed a power of $2$)
- $I_h, J_h$ : Corresponding to the higher order bits
- $I_l, J_l$ : Corresponding to the lower order bits

$I.J = (I_h 2^{n/2} + I_l)(J_h 2^{n/2} + J_l) = I_hJ_h 2^n+I_hJ_l2^{n/1}+I_lJ_h2^{n/1}+I_lJ_l$

- $T(n) = \begin{cases} c &\text{if} ~n < 2 \\4T(n/2) + cn ~& n \geq 2  \end{cases} $
  - Solution??

No better than high school grade algorithm

- Let us consider another way of the doing the same.
![integer multiplication](integer_multiplication.png)

- $T(n) = \begin{cases} c &\text{if} ~n < 2 \\3T(n/2) + cn ~& n \geq 2  \end{cases} $

  - Solution??  
------------------------------------------------------

## POLYNOMIALS (FROM ALL WE KNOW TO IMPLEMENTATION)

- $p(x) = \sum_{i=0}^{n} a_i x^i $ : $n^{th}$ degree polynomial if $a_n \neq 0 $.

- Polynomials viewed as a programming structure should support the following operations:

  - Evaluation at a point $x$
  - Addition/Subtraction
  - Multiplication

- Before getting into all of them, we have to figure a way to represent them programmatically

    - ### array representing coefficients

      - Example: $3x^4+2x+4$ can be represented as the array  :  [4,2,0,0,3] (The powers increase from left(index 0) end which represents $x^0$)
    - How do we accomplish the operations using this representation?

      - **evaluate($P,x$)**
          
          1. $n = length(P)$ $~~~~~~~~~~~--->1$
          2. $X = 1, sum = 0$ $~~~~~~~~~~--->2$
          3. for $i=0$ to $n-1$:  $~~~~~~~~~~~~~~~~~--->n$
          4.   - $sum=sum + XP[i]$ $---> n $ 
          5.   - $X = X.x$ $---> n $ 
          6. return $sum$ $---> 1 $
          ------------------------------
          Total number of operations : $O(n)$

      - **add($P,Q$)** //Assume both are of the same degree $n$

        - Quite straightforward, simply add the corresponding elements of the two arrays
        (Try writing the pseudo code and compute the run time)
      
      - **multiply($P,Q$)**
         
         - The result of multiplication will have a maximum degree $2n$
         - Coefficient of $x^k$ : $R[k] = \sum_{i=max(0,k-n)}^{min(k,n)}P[i]Q[k-i]; 0 \leq k \leq 2n$.
         - Procedure:

              **multiply($P,Q$)**
                
              1. $R : 2n$ long array
              2. for $i = 0$ to $n-1$:
              3.    - $R[i]=0$
              4. for $j=0$ to $n-1$:
              5.    - for $k=0$ to $n-1$:
              6.         R[j+k] = R[j+k] + P[j]Q[k]
              7. return R

         - Compute the run-time of the operation above program.(Also make sure that the above code routine and the formula for $R[k]$ are in agreement)

------------------------------------------------------
### *Can we do multiply in better run time?*


  - Alternate representations provide clue:

      - Sample representation

      


    




