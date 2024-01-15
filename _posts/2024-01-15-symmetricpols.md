---
layout: post
author: Martin Trifonov
title: Symmetric Polynomials (pt. 1)
---
 
## Dear Mr Gauss, 
Today's theorem is called the **fundamental theorem on symmetric polynomials**. It's a rather chunky theorem, so we might take another week or two to fully finish it. I first encountered this theorem in my attempt to retrace the historical development of Galois theory, where it kept making appearances in various proofs. My gut tells me its an important theorem, so I would love to show it to you. 

Okay, enough babbling, lets go meet our theorem.

## Meet the theorem
Before we dive into the fundamental theorem on symmetric polynomials, let's first get comfortable of _symmetric polynomials_.    

>**Definition.** A polynomial $f(x_1,...,x_n)$ is called _symmetric_ if no permutation of the variables $x_1,...,x_n$ changes its value.

Consider, for example, polynomials in the variables $a,b$. The only possible way to permute the variables $a,b$ is to swap $a$ and $b$. The polynomial $a+b$ is _symmetric_, because when you swap $a,b$, you get $b+a$, and $a+b = b+a$. The polynomial $a-b$ is _not symmetric_, because when you swap $a,b$, you get $b-a$, and $a-b \neq b-a$.  

Let's now consider polynomials in 3 variables, $a,b,c$. A very important class of symmetric polynomials are the "elementary symmetric polynomials" in 3 variables, listed below:  

$$\begin{align}&a+b+c
\\& ab+bc+ac
\\& abc\end{align}$$

In general, you can obtain the "elementary symmetric polynomials" in $n$ variables by the following recursive definition:
> Let $\tau_1,...,\tau_{n-1}$ be the elementary symmetric polynomials in $n-1$ variables $x_1,...,x_{n-1}$. The elementary symmetric polynomials in $n$ variables, let's denote them $\sigma_1,...,\sigma_n$ are constructed as   

$$\begin{align}\sigma_1 &= \tau_1 + x_n
\\\sigma_2 &= \tau_2 + x_n\tau_1
\\\vdots
\\\sigma_n &= 0 + x_n\tau_n\end{align}$$

> **Follow along:** Using the above definition, construct the elementary symmetric polynomials in 4 variables

Now that we're comfortable with the notion of symmetric polynomials, we can state the fundamental theorem
> **Fundamental theorem on symmetric polynomials**  
There exists an algorithm that rewrites any symmetric polynomial in $n$ variables $x_1,...,x_n$ as a polynomial in the elementary symmetric polynomials in $n$ variables

For example, the symmetric polynomial $a^2+b^2$ in 2 variables can be rewritten as $(\sigma_1)^2-2(\sigma_2)$, where $\sigma_1 = (a+b),\sigma_2 = (ab)$ are the elementary symmetric polynomials in 2 variables.

> **Pause for a second** Is this suprising to you? Can you see a straightforward way to express the polynomial $a^3+b^3+c^3$ in terms of the elementary symmetric polynomials in 3 variables?

## The algorithm

Let $f(x_1,...,x_n)$ be a symmetric polynomial in $n$ variables. We will describe a procedure by which you can rewrite $f$ as a polynomial $g(\sigma_1,...,\sigma_n)$ in the elementary symmetric polynomials in $n$ variables.

As we go along, we will be using the following example polynomial: $f(a,b,c) = a^3bc+b^3ac+c^3ab$.
1. If the number of variables in our polynomial is 1, then return the polynomial as it is. Otherwise, continue with step 2. (This is the base case for the recursion used in step 3.) 
2. Pick a variable of your choice, like $c$ and rearrange your expression as a polynomial in this variable. We write $(a^3b+b^3a)c+(ab)c^3$
3. Recursively rewrite each of the coefficients, which are now symmetric polynomials in 2 variables, as polynomials in the elementary symmetric polynomials in 2 variables. In terms of our example, you get an expression of the form:  
$Q_1(\tau_1,\tau_2)c+Q_2(\tau_1,\tau_2)c^3$, where $Q_i(\tau_1,\tau_2)$ are the coefficients rewritten in terms of the elementary symmetric polynomials in 2 variables. 
4. Observe that the recursive definition of elementary symmetric polynomials allows us to obtain the following relations:  
$$\begin{align}\tau_1& = \sigma_1-c\\
\tau_2 &= \sigma_2 - c\tau_1 = \sigma_2-\sigma_1c+c^2
\\
0 &=\sigma_3-c\tau_{2}=\sigma_3-c\sigma_{2}+c^2\sigma_{1}-c^3\end{align}$$  
Using the first two relations, substitute $\tau_1$ for $\sigma_1-c$ and $\tau_2$ for $\sigma_2-\sigma_1c+c^2$ in both $Q_1,Q_2$.
5. Rearrange the expression as a polynomial in $c$. If necessary, use relation (3) from step 3 to reduce its degree.  Verify that after simplifying you are left with a polynomial in the elementary symmetric polynomials. 

To make sure we know what's going on, let's simulate a proper run of this algorithm.

## A demonstration

We start with $f(a,b,c) = a^3bc+b^3ac+c^3ab$. 

**Step 1**. We rewrite our expression as $(a^3b+b^3a)c+(ab)c^3$.

**Step 2**. Here, the algorithm relies on the magic of recursion to find an expression of the coefficients $(a^3b+b^3a),(ab)$ in terms of the elementary symmetric polynomials in $a,b$, namely $\tau_1 = a+b,\tau_2 = ab$.  
One of our coefficients is already in this form, since $(ab) =\tau_2$. To figure out the expression of the second coefficient, $a^3b+b^3a$, we must step into a recursive call. However, that seems like a rather tedious thing to do, so we will skip forward to the result of the call:
$a^3b+b^3a = \tau_1^2\tau_2-2\tau_2^2$

**Step 3**. Now we construct the relations between the elementary symmetric polynomials in $a,b$: $\tau_1,\tau_2$ and the elementary symmetric polynomials in $a,b,c$: $\sigma_1,\sigma_2,\sigma_3$

$$\begin{align}
\tau_1 &= \sigma_1-c\\
\tau_2 &= \sigma_2-\sigma_1c+c^2\\
0 &=\sigma_3-\sigma_2c+\sigma_1c^2-c^3\\
\end{align}$$

Now we substitute these identities in our expression $(\tau_1^2\tau_2-2\tau_2^2)c+(\tau_2)c^3$ and obtain
$$c^{3} (\sigma_1^{2} - 2 \sigma_2) + c^{2} (- \sigma_1^{3} + 2 \sigma_1 \sigma_2) + c (\sigma_1^{2} \sigma_2 - 2 \sigma_2^{2})$$
Now divide by the polynomial in the third relation, $\sigma_3-\sigma_2c+\sigma_1c^2-c^3$ and obtain:
$$\sigma_1^{2} \sigma_3 - 2 \sigma_2 \sigma_3$$
> **Follow along:** Verify that indeed  
$\sigma_1^{2} \sigma_3 - 2 \sigma_2 \sigma_3 = a^3bc+b^3ac+c^3ab$. When preparing this post, I ran the calculations through the computer, as they can get quite tedious. However, this last step, I did by hand, and I was positively charmed by the magic of this algorithm.
> **Challenge:** Express the polynomial $a^3+b^3+c^3$ in terms of the elementary symmetric polynomials. 

## Magic? 

The magic in this theorem happens in the third step. After the polynomial division, all terms that contain $c$ vanish. Why does this happen?  

Stay tuned, as we verify the correctness of todays algorithm next Monday!

## References / Literature / Further reading

I am working with the book "Galois theory" by "Harold M. Edwards". Pages 8-13 contain the fundamental theorem on symmetric polynomials. My interpretation follows the text closely.