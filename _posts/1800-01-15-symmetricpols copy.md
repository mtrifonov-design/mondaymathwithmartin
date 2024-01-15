---
layout: post
author: Martin Trifonov
---
Hi, It's Monday, I'm Martin, and this is math.  
Today's theorem is called the **fundamental theorem on symmetric polynomials**. I first encountered this theorem in my attempt to retrace the historical development of Galois theory, where it kept making appearances in various proofs. My gut tells me its an important theorem, so I want to show it to you. 

Okay, enough babbling, lets go meet our theorem.

### Meet the theorem
Let's start with something super concrete. Consider, for example, the following polynomial $f(x) = x^{5}+2x^{4}-2x^{3}+4x-5$. We know that over the complex numbers, this polynomial will have $5$ roots, let's call them $\alpha_1,..,\alpha_5$. 

Now, the value of these roots is not directly accessible to us. Unlike quadratic polynomials, there doesn't exist a generic formula for solving polynomials of degree $5$ where we could just plug in our coefficients.

However, whilst we can't always know the roots directly, it turns out that we can always find the value of certain expressions _in the roots_. For example, consider the expression $\alpha_1^3+\alpha_2^3+\alpha_3^3+\alpha_4^3+\alpha_5^3$. We will show how we can derive the value of this expression using only the coefficients $2,-2,0,4,-5$ of our polynomial $f(x)$.


 The reason we will be able to evaluate $\alpha_1^3+\alpha_2^3+\alpha_3^3+\alpha_4^3+\alpha_5^3$  is because this expression is said to be _symmetric_, by which we mean that we could apply any permutation of the roots $\alpha_1,...,\alpha_5$ to it, and its value will not change. For example, if we swap all occurences of $\alpha_1$ with $\alpha_3$ (this is a  permutation of the roots), we obtain the new expression $\alpha_3^3+\alpha_2^3+\alpha_1^3+\alpha_4^3+\alpha_5^3$, which has equal value to the original expression.  

The juiciest way to state the **fundamental theorem on symmetric polynomials** is the following:
> There exists an algorithm, by which we can express symmetric polynomials in the roots of an equation $\alpha_1,...,\alpha_n$ in terms of the coefficients of the equation $c_0,...,c_{n-1}$

That's the flashy way to introduce the theorem. However, a more general statement, that makes no reference to "roots of an equation", is the following:

> There exists an algorithm by which we can express symmetric polynomials in $x_1,...,x_n$ in terms of the elementary symmetric polynomials $\sigma_1,...,\sigma_n$ in $n$ variables.

This warrants a little explanation on what "elementary symmetric polynomials in $n$ variables" might be. For this, observe that we can factorise our polynomial $f(x)$ as $(x-\alpha_1)(x-\alpha_2)...(x-\alpha_5)$, and the value of this equals $x^5+2x^4-2x^3+4x-5$. If you expand out the former expression, you obtain $f(x) = x^5-(\alpha_1+\alpha_2+...+\alpha_5)x^4+...-(\alpha_1\alpha_2...\alpha_5)$. The expressions 
$$\alpha_1+\alpha_2+\alpha_3+\alpha_4+\alpha_5 \\
\alpha_1\alpha_2+\alpha_1\alpha_3+...\\\vdots\\\alpha_1\alpha_2\alpha_3\alpha_4\alpha_5$$
are called the "elementary symmetric polynomials in $\alpha_1,...,\alpha_5$", and they are equal to our coefficents (with an occasional minus sign).

The fundamental theorem, in full generality, says that symmetric polynomials can be expressed in terms of elementary symmetric polynomials. When working with equations, this implies that you can express symmetric polynomials in terms of the coefficients.

### The algorithm



### Newtons Theorem
### Properties of symmetric polynomials
Let's investigate the nature of symmetric polynomials. 
Supose we start with any polynomial $f(x_1,...,x_n)$. For simple polynomials, it is easy to determine if they are symmetric at a glance. 
$$2x^2+2y^2+2z^2 \in \mathbb Q[x,y,z] \text{ is symmetric}$$
But what about more complicated expressions?
$$2xy^3(x^2+z)(y+x^2)$$
Let's consider the following algorithm to determine the symmetry of polynomials:
>1. Fully expand out your given polynomial, so that it is written as sum of monomials. Example:  
$2xy^3(x^2+z)(y+x^2)=2 x^5 y^3 + 2 x^3 y^4 + 2 x^3 y^3 z + 2 x y^4 z$
>2. For the first monomial in your expression, say $x^5y^3 = x^5y^3z^0$, generate all distinct monomials that can be obtained by permuting the variables, in this case:  
$x^5y^3z^0,x^5z^3y^0,y^5x^3z^0,y^5z^3y^0,z^5x^3y^0,z^5y^3x^0$  
If all monomials exist in the expression and share the same coefficients, then cross them of from the expression and repeat step 2. If some monomial doesn't exist, or if two monomials have different coefficients, the polynomial isn't symmetric.     


The important takeaway here is that monomials can be grouped together in the specified way. They are, in some sense, the building blocks of symmetric polynomials. We can identify these building blocks in the following way:
5-3-0 shall denote the symmetric polynomial 
$$x^5y^3z^0+x^5z^3y^0+y^5x^3z^0+y^5z^3y^0+z^5x^3y^0+z^5y^3x^0$$
whereas 1-0-0 denotes
$$x+y+z$$
The elementary symmetric polynomials are exactly 1-0-0,1-1-0,1-1-1.
Now there is a slightly larger class of symmetric polynomials generated by the elementary symmetric polynomials, which we will show now: 


### Newtons Theorem
>The symmetric polynomials of the form
>$$s_k =\alpha_1^k+\alpha_2^k+...+\alpha_n^k$$
>can be expressed in terms of the elementary symmetric polynomials $\sigma_1,...,\sigma_n$.
___
Proof.  
The polynomials $s_k$ are exactly those described by k-0-0.
There is a natural law here, which says:
(k-1-0)()
### The general proof
### Outlook