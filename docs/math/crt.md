Solve $a$ for $a \equiv a_i (\mod p_i)$, coprime $\gcd(p_i,p_j)=1, \forall i,j$.

**Claim 1.** $\exists$ unique $a (\mod P)$, where $P = \prod p_i$.

**Claim 2.** $a = \sum a_ib_ib_i'$, where $b_i = P/p_i$, $b_i' = b_i^{-1} (\mod p_i)$.

## Extended crt

Fold with start $(0,1)$, $(a,p)$ by next $(a_1,p_1)$.

**Claim.** $a := a + p p' \dfrac{a_1-a}{\gcd(p,p_1)}$, when $a_1-a \equiv 0(\mod g)$.

**Proof.** Replace $pp'=g-p_1p_1'$, result symmetry form $a_1 + (0 \mod p_1)$.