# Usage
Convolution in O($n\log n$).

# Notations
Polynomial $a(x) = \sum_{i=0}^{n-1} a_i x^i$.

Coefficients $a = (a_0,\cdots, a_{n-1})$.

n-th root of unity $\omega=\omega_n: \omega^n = 1$.

Transform $\text{DFT}(a) = \mathcal{F}(a) = (a(\omega^0),\cdots, a(\omega^{n-1})) = a(\omega..)$.

Convolution $\mathcal{F}(a * b) = (a * b)(\omega..) =  (a(\omega^k)b(\omega^k),\cdots) = a(\omega..)b(\omega..) = \mathcal{F}(a)\mathcal{F}(b)$.

Matrix view $\mathcal{F}(a) = \Omega a$, where $\Omega = (\omega^{ij})$.

Inverse $\mathcal{F}^{-1}: \Omega^{-1} = \dfrac{1}{n} \Omega^*$.

## Butterfly
**Lemma.** Assume $n$ even.

$$
  a(x) = a_{even}(x^2) + x a_{odd} (x^2) \\\\ 
  \omega_d^{dk} = \omega^k, \omega_n^{n/2} = \omega_2^1 = -1 \\\\
  \omega^{k+n/2} = -\omega^k \\\\
  (\omega^{k + n/2})^2 = (\omega^k)^2 = \omega_{1/2}^k
$$

**FFT.**

$$
  a(\omega^k) = a_{even}(\omega_{1/2}^k) + \omega^k a_{odd} (\omega_{1/2}^k) \\\\
  a(\omega^{k+n/2}) = a_{even}(\omega_{1/2}^k) - \omega^k a_{odd} (\omega_{1/2}^k)
$$

**radix 2 trick.** bit-reversal permutation.

# Groups
## Complex
$\omega = e^{-\dfrac{2\pi i}{n}}$.

## NTT
$\omega = g^c, p = cn+1$: [generator/primitive root](https://cp-algorithms.com/algebra/primitive-root.html).

# FWHT

Generalize $\sum$'s `+` in $x^{k+j}$ with `&,^,|`. 

## properties
No need bit-reversal nor generator.

let $H_m$ be the tranform matrix c.to $n=2^m$.

$H_m = H_1 \otimes H_{m-1}$.

$H_1$ could not be unique, as long as it stores recoverable information.

### Xor
$H_1 = (|+\rangle, |-\rangle) = \dfrac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\\\ 1 & -1\end{pmatrix}$.

$H_m^{-1} = H_m$, $H_m^2 = I$.

### And
$H_1 = \begin{pmatrix} 1 & 1 \\\\ 0 & 1\end{pmatrix}$. $\Leftrightarrow$ Zeta superset.

### Or
$H_1 = \begin{pmatrix} 1 & 0 \\\\ 1 & 1\end{pmatrix}$. $\Leftrightarrow$ Zeta.