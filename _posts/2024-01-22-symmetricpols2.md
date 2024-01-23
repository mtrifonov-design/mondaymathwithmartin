---
layout: post
author: Martin Trifonov
title: Symmetric Polynomials (pt. 2)
---
 
## Honorable reader, 
Thanks for tuning in to todays show. We are continuing our discussion of the  **fundamental theorem on symmetric polynomials**. Do have a look at last weeks show, in case you missed it. 

There is no time for small talk, we have some work to do.

## Let's refresh our memory

In case you forgot, the theorem we are working on is the following:
> **Fundamental theorem on symmetric polynomials** 
There exists an algorithm that rewrites any symmetric polynomial in $n$ variables $x_1,...,x_n$ as a polynomial in the elementary symmetric polynomials in $n$ variables



For example, the symmetric polynomial $a^2+b^2$ in 2 variables can be rewritten as $\sigma_1^2-2\sigma_2$, where $\sigma_1 = a+b,\sigma_2 = ab$ are the elementary symmetric polynomials in 2 variables.

Last week, we detailed an algorithm to transform symmetric polynomials in $n$ variables into polynomials in the elementary symmetric polynomials in $n$ variables, illustrating it with a concrete example. Let's revisit this algorithm.




## The algorithm

Let $f(x_1,...,x_n)$ be a symmetric polynomial in $n$ variables. We will describe a procedure by which you can rewrite $f$ as a polynomial $g(\sigma_1,...,\sigma_n)$ in the elementary symmetric polynomials in $n$ variables.

As we go along, we will be using the following example polynomial: $f(a,b,c) = a^3bc+b^3ac+c^3ab$.
1. **Base case**. If the number of variables in our polynomial is 1, then return the polynomial as it is. Otherwise, continue with step 2. 
2. **Variable selection and rearrangement**. Pick a variable of your choice, like $c$ and rearrange your expression as a polynomial in this variable. We write $(a^3b+b^3a)c+(ab)c^3$
3. **Recursive rewriting**. Recursively rewrite each of the coefficients, which are now symmetric polynomials in 2 variables, as polynomials in the elementary symmetric polynomials in 2 variables. In terms of our example, you get an expression of the form:  
$Q_1(\tau_1,\tau_2)c+Q_2(\tau_1,\tau_2)c^3$, where $Q_i(\tau_1,\tau_2)$ are the coefficients rewritten in terms of the elementary symmetric polynomials in 2 variables. 
4. **Substitution and rearrangement**. Observe that the recursive definition of elementary symmetric polynomials allows us to obtain the following relations:  
$$\begin{align}\tau_1& = \sigma_1-c\\
\tau_2 &= \sigma_2 - c\tau_1 = \sigma_2-\sigma_1c+c^2
\\
0 &=\sigma_3-c\tau_{2}=\sigma_3-c\sigma_{2}+c^2\sigma_{1}-c^3\end{align}$$  
Using the first two relations, substitute $\tau_1$ for $\sigma_1-c$ and $\tau_2$ for $\sigma_2-\sigma_1c+c^2$ in both $Q_1,Q_2$. Rearrange the expression as a polynomial in $c$.
5. **Division and remainder**. Divide your resultant polynomial by the polynomial in the righthandside of relation (3) from the previous step, and return the remainder of this operation. 

## Correctness of the algorithm

The instructions of the algorithm are straightforward (albeit tedious to follow). If we assume the algorithm to work correctly for symmetric polynomials for $n-1$ variables, it is easy to believe that following the algorithm we can convert a symmetric polynomial $f(x_1,...,x_n)$ with rational coefficients into a polynomial $p(x_n)$ with coefficients that themselves are polynomials in the elementary symmetric polynomials in $n$ variables. It is also straightforward to see, from this construction, that the polynomial $p(x_n)$, being the remainder of a division by a polynomial of degree $n$ (see step 5 of algorithm), is of degree at most $n-1$. It is **not clear** that it is necessarily a constant polynomial, thereby simply some expression in the elementary symmetric polynomials in $n$ variables.   
The magic of the algorithm lies in understanding why this follows. Once we understand this connection, a proof by induction spells itself out naturally.

The critical observation one must make is that the algorithm allows for one degree of freedom: In step 2, we are asked to pick a variable of our choice, and to rearrange our given symmetric polynomial as a polynomial in this variable. In the example we gave, we rearranged $a^3bc+b^3ac+c^3ab$ as $(a^3b+b^3a)c+(ab)c^3$, as a polynomial in $c$ with coefficients being symmetric polynomials in $a,b$. However, we could have just as easily rearranged it to read $(a^3c+c^3a)b+(ac)b^3$ or $(b^3c+c^3b)a+(bc)a^3$. This means, that we could have continued the other steps making a different choice, other than $c$. 

>**Question:** how does the choice of variable in step 2 affect the rest of the algorithm?

That's right, it doesn't! **Any choice** we could have made would lead to an identical result. Let's make this more concrete. If we start with $f(x_1,...,x_n)$, in step 2 we choose $x_n$, then we end up with a polynomial $p_1(x_n)$ in $x_n$ with coefficients that are polynomials in the elementary symmetric polynomials. If instead we had chosen $x_1$, we would have ended up with a polynomial $p_2(x_1)$ in $x_1$ with coefficients that are polynomials in the elementary symmetric polynomials. However, it turns out that $p_1 = p_2$, the underlying polynomial we end up with does not depend on whether we proceed with $x_1$ or $x_n$, as a result of the symmetry of the polynomial $f(x_1,...,x_n)$ we started out with.
This implies that any initial choice of variable $x_1,...,x_n$ ends up as a root of the polynomial $g(Y) = p(Y)-f(x_1,...,x_n)$ . 
If $g(Y)$ is non-zero, and $x_1,..,x_n$ are all roots, this implies that $(Y-x_1),...,(Y-x_n)$ are all divisors of this polynomial. Ultimately, it follows that $g(Y)$ has degree at least $n$, which is a contradiction. Thus it must be the zero polynomial. This implies that all coefficients of $g(Y)$ are zero, which completes the proof.
## More generally...
The punchline of the correctness proof above underlies a simple setup. We constructed a polynomial with "symmetric coefficients" (the coefficients being symmetric polynomials in $x_1,...,x_n$), that has $x_k$ as a root for some $k \le n$. Whenever we have such a situation, we can immediately infer that the constructed polynomial has degree at least $n$ if it isn't the zero polynomial (**why?**). 

There is a natural way to generalise this setup and peek into some of the ideas underlying Galois theory. Suppose you have some polynomial $f(Y)$ with symmetric coefficients. Now, suppose it has $r(x_1,...,x_n)$ as a root, where $r$ is some polynomial (not necessarily symmetric). In other words:
$$s_mr^m+...+s_0 = 0$$
Then any permutation of the $n$ variables keeps the coefficients of the above polynomial constant, but possibly changes $r$ into another root of the same polynomial.  
Now if we call $r_1,...,r_k$ all the distinct polynomials we can obtain by applying any permutation to $r$, we know that $r_1,...,r_k$ must all be roots of the polynomial $$s_mY^m+...+s_0 = 0$$
Then, by the same logic as before, this implies that $m \ge k$.   
In some sense we can think of the number $k$ as a measure of how "asymmetric" the root $r$ is. In the case $r = x_n$, we have $k = n$. Once we start thinking of symmetry as a spectrum, not a binary state, we make a productive leap that launches us into Galois theory.

## Outlook

This concludes our exploration of the fundamental theorem on symmetric polynomials. The process of writing this has spurred on some important questions on how I should go about writing articles in this blog. The level of rigour I chose in this article was low, which could make for a more pleasant read, but can also come across as confusing. I am also quite uncertain what audience I want to be writing for. Whilst the last two articles are rather beginner-friendly, some foundation in algebraic thinking might be necessary for the material to make sense. I will aim to address some of these questions in the future.



## References / Literature / Further reading

I am working with the book "Galois theory" by Harold M. Edwards. Pages 8-13 contain the fundamental theorem on symmetric polynomials. My interpretation follows the text closely.