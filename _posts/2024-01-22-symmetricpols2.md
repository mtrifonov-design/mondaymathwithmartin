
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