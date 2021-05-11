Solve $ax+by = \gcd(a,b)$.

With implicitly knowing solution $bx' + (a \mod b)y' = g$, and with $a\mod b = a - \lfloor\dfrac{a}{b}\rfloor b$. Rearrange coefficients:

$$ \Rightarrow x = y', y = x' - y'\cdot \lfloor\dfrac{a}{b}\rfloor $$