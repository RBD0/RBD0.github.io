---
layout: post
title: Merten's Theorem for Arithmetic Progressions
date: 2024-10-20 11:12:00-0400
description:
tags: formatting, math
categories: sample-posts
related_posts: false
---

This content was prepared as part of a course project for Analytic Number Theory, conducted under the guidance of Prof. Biswajyoti Saha. The primary objective is to analyze equation (2.6) in \cite{williams1974merten}. Although we found the reference to equation (2.6), we were unable to fully understand it. As a result, we did some further investigation and provided a clarification of the equation.

## Lemma  
*(Tao, 2014)*  
Let $ \chi $ be a non-principal character of modulus $ k $, and let $ f $ be an arithmetic function that is monotone on an interval $ [x,y] $. Then  

$$
\sum_{x\leq n<y} f(n)\chi(n) = \mathcal{O}(k(|f(x)|+|f(y)|)).
$$

### Proof  
We begin by observing that we can assume $ f $ is monotone non-increasing, as the argument relies only on the behavior of $ f $, not its specific ordering. Next, we modify $ x $ and $ y $ by rounding $ x $ up and $ y $ down to the nearest multiples of $ k $. This ensures $ x $ and $ y $ are multiples of $ k $, which simplifies the analysis. Consequently, the sum on the left-hand side can now be expressed as a sum over blocks of size $ k $:  

$$
\sum_{x\leq n<y} f(n)\chi(n) = \sum_{j} \sum_{jk \leq n < (j+1)k} f(n)\chi(n),
$$  

where $ j $ ranges over integers satisfying $ x\leq jk < (j+1)k <y $.  

Now, using the fact that $ \chi $ is non-principal, we know it is orthogonal to the principal character. This implies:  

$$
\sum_{jk \leq n < (j+1)k} \chi(n) = 0.
$$  

Therefore, we can rewrite each inner sum as:  

$$
\sum_{jk \leq n < (j+1)k} f(n)\chi(n) = \sum_{jk \leq n < (j+1)k} (f(n) - f(jk))\chi(n).
$$  

Next, we use the trivial bound $ |\chi(n)| \leq 1 $ to estimate the magnitude of this sum. Since $ f $ is monotone non-increasing,  

$$
|f(n) - f(jk)| \leq f(jk) - f((j+1)k) \quad \text{for } n \in [jk, (j+1)k).
$$  

Thus, the entire sum can be bounded as:  

$$
\left| \sum_{jk \leq n < (j+1)k} f(n)\chi(n) \right| \leq k \big(f(jk) - f((j+1)k)\big).
$$  

Finally, summing over $ j $, we observe that the terms $ f(jk) - f((j+1)k) $ form a telescoping series. This causes most terms to cancel, leaving a bound dependent on the endpoints. The claim follows directly from this telescoping argument.  

---

## Corollary  
Let $ \chi $ be a non-principal Dirichlet character of modulus $ k $. Then  

$$
\sum_{n\leq x} \frac{\Lambda(n)\chi(n)}{n} = \mathcal{O}_{\chi}(1),
$$  

for any $ x\geq 1 $.  

### Proof  
From the lemma, we have that  

$$
\sum_{n\leq x} f(n)\chi(n) = \mathcal{O}_{k}(|f(x)|).
$$  

Therefore,  

$$
\sum_{n\leq x} \frac{\Lambda(n)\chi(n)}{n} = \mathcal{O}_k(\Lambda(x)/x) = \mathcal{O}_k(1).
$$  

---

## Lemma  
Let $ \chi $ be a non-principal Dirichlet character of modulus $ k $. Then  

$$
\sum_{p\geq x} \frac{\chi(p)}{p} = \mathcal{O}\left(\frac{1}{\log{x}}\right).
$$  

### Proof  
We start by rewriting the summation on the left-hand side. Using the Abel Summation Formula, we express:  

$$
\sum_{x \leq p \leq y} \frac{\chi(p)}{p} = \frac{1}{\log y} \sum_{x \leq p \leq y} \frac{\chi(p)\log p}{p} + \int_x^y \frac{1}{t \log^2 t} \sum_{x \leq p \leq t} \frac{\chi(p)\log p}{p} \, dt.
$$  

To proceed, we need an asymptotic estimate for  

$$
\sum_{p \leq x} \frac{\chi(p)\log p}{p}.
$$  

By combining this result with the previous corollary, it follows that:  

$$
\sum_{p \leq x} \frac{\chi(p)\log p}{p} = \mathcal{O}_{\chi}(1).
$$  

Hence, for all $ x \leq t \leq y $, we have:  

$$
\sum_{x \leq p \leq t} \frac{\chi(p)\log p}{p} = \mathcal{O}(1).
$$  

Substituting this back, we find:  

$$
\sum_{x \leq p \leq y} \frac{\chi(p)}{p} = \mathcal{O}\left(\frac{1}{\log y} + \frac{1}{\log x}\right).
$$  

Finally, letting $ y \to \infty $ gives the desired result.  

---

## Theorem  
Let $ \chi $ be a non-principal Dirichlet character of modulus $ k $. Then  

$$
\prod_{p\leq x} \left(1-\frac{\chi(p)}{p}\right) = \frac{1}{L(1,\chi)} + \mathcal{O}\left(\frac{1}{\log{x}}\right),
$$  

as $ x\to \infty $.  

### Proof  
Since  

$$
L(1,\chi) = \prod_{p}\left(1-\frac{\chi(p)}{p}\right)^{-1},
$$  

we note that:  

$$
L(1,\chi)\prod_{p\leq x}\left(1-\frac{\chi(p)}{p}\right) = \prod_{p>x} \left(1-\frac{\chi(p)}{p}\right)^{-1}.
$$  

It suffices to show that:  

$$
\log\left(L(1,\chi)\prod_{p>x} \left(1-\frac{\chi(p)}{p}\right)^{-1}\right) = \mathcal{O}\left(\frac{1}{\log{x}}\right).
$$  

Now,  

$$
\log{\prod_{p>x} \left(1-\frac{\chi(p)}{p}\right)^{-1}} = \sum_{p>x}\frac{\chi(p)}{p} + \sum_{p>x}\sum_{m\geq 2}\frac{\chi^m(p)}{mp^m}.
$$  

Using the previous lemma, we obtain:  

$$
\sum_{p>x} \frac{\chi(p)}{p} = \mathcal{O}\left(\frac{1}{\log{x}}\right).
$$  

Similarly,  

$$
\sum_{p>x}\sum_{m\geq 2}\frac{\chi^m(p)}{mp^m} = \mathcal{O}(1/x).
$$  

Substituting these results, we conclude:  

$$
\log{\prod_{p>x} \left(1-\frac{\chi(p)}{p}\right)^{-1}} = \mathcal{O}\left(\frac{1}{\log{x}}\right),
$$  

completing the proof.