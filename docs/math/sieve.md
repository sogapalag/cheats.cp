## Linear

Break when hit least prime factor.

**Claim.** Each composite sieved once corresponding to its least prime.

[Multiplicative function](https://en.wikipedia.org/wiki/Multiplicative_function): $f(mn) = f(m)f(n)$, for coprime $m,n$.

$f(ip)$    | $\phi$             | $\mu$   | $\sigma_k$ | $e_k$
-----------|--------------------|---------|------------|------- 
$p\nmid i$ | $(p-1)\phi(i)$     |$-\mu(i)$| $(1+p^k)\sigma_k(i)$ |  $1+p^k$
$p\mid i$  | $p\phi(i)$         |    $0$  | $\sigma_k(i) e_k(ip)/e_k(i)$| $1 + e_k(i)*p^k$

Where $e_{k,p}(p^c) = 1 + p^k + p^{2k} + \cdots + p^{ck}$, a non-multy helper function.

Thus we can build above functions in linear time.

## Prefix of multiplicative functions

**Usage.** Find $F(n)=\sum f(i)$.

[Dirichlet ring](https://en.wikipedia.org/wiki/Dirichlet_convolution#Dirichlet_ring).
[Divisor sum identities](https://en.wikipedia.org/wiki/Divisor_sum_identities).

When $f*g$ is easy to calculate:

\begin{align}
\sum_{i=1}^n (f*g)(i) = \sum_{i=1}^n F\left(\left\lfloor \dfrac{n}{i} \right\rfloor\right) g(i)  \\\\
\Rightarrow F(n) \sim (F\left(\left\lfloor \dfrac{n}{2} \right\rfloor\right),\cdots)
\end{align}

### On prime factorization
Implicitly ignore $f(i=1)=1$.

**Usage.** Find $F$ when $f(p^c)$ easy to calculate.

**Notation.** $p_1=2,p_2=3,p_3=5,...$; $p_s = \max \{p: p \leq \sqrt{n} \}$.

**Define.** $S_k = \{x: p_i\nmid x, \forall i\leq k\}$. i.e. remain number sieved after first $k$ primes.
$$ [n] = S_0 \supset S_1 = \{\text{odd number}\} \supset S_2 \supset \cdots S_s = \\{ p: p > \sqrt{n} \\} $$

#### [Zhou](https://oi-wiki.org/math/zhou/)

Let $F_k(n) = \sum_{i\in S_k} f(i)$. Recurrence relation:
\begin{align}
    F(n) &= F_0(n) = \sum_i f(i) \\\\
    F_k(n) &= F_{k-1}(n) - f(p_k) F_{k-1} \left(\left\lfloor \dfrac{n}{p_k}  \right\rfloor\right) \\\\
    &= \begin{cases} F_{k-1}(n),  p_k^2 > n  \\\\  \cdots  \end{cases}
\end{align}
Thus we can calculate
$$ \sum_{\exists p > \sqrt{n}, p\mid i} f(i) = \sum_{i=1}^{\sqrt{n}} f(i)F_{s}\left(\left\lfloor\dfrac{n}{i} \right\rfloor \right) $$
Similarily we can define $H_k(n)= \sum_{i \sim (p_k..p_s]} f(i)$, to calculate remain part.

#### [Min_25](https://oi-wiki.org/math/min-25/)

**Usage.** Count number of primes, $\pi(n)$.

Let $G_k(n) = \sum_{S_k \cup P} g(i)$. Similarily:
$$
    G_k(n) = G_{k-1}(n) - g(p_k) \left(G_{k-1} \left(\left\lfloor \dfrac{n}{p_k}  \right\rfloor\right)  - G_{k-1}(p_{k-1}) \right)
$$
Set $g=1$, thus $\pi(n) = G_s(n)$.

#### [Meissel–Lehmer](https://en.wikipedia.org/wiki/Prime-counting_function#The_Meissel%E2%80%93Lehmer_algorithm)