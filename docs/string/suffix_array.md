# Usage

Sort suffix strings `s[i..]` of `s`, store `i`s in `sa`.

*View.* Suffix trie/tree, by the help of lcp array.

1. Append 0 to `s`, thus could treat length $<k$ still be $k$ as cyclic string.
2. $k=1,2,4,8...$, sort all length $=k$. By compare `(i, i+k)` as key corresponding to `(s[i..i+k], s[i+k..i+2k])`. O($n\log^2 n$).
3. Radix sort `(i,i+k)` by counting sort. O($n\log n$).
4. [Kasai's](https://web.stanford.edu/class/archive/cs/cs166/cs166.1206/lectures/03/Small03.pdf). Build lcp/height array, i.e. lcp of adjacents(rank).
    - **Claim.** Adjacents(original)'s `lcp(i+1) >= lcp(i)-1`, where`lcp(i) = lcp[rk[i]]`.


**Claim 1.** lcp of rank l and r is $\min_{i=l..r} \text{lcp}[i]$.

# Applications

- \#distinct substrings. i.e. \#nodes in trie. $= n(n+1)/2 - \sum_i \text{lcp}[i]$.
- Longest length among substrings occurence $> k$. $= \max_i \min \text{lcp}[i..i+k]$.
- Lcp of 3 or more strings. Concat $S_1\#_1 S_2\#_2 S_3 \#_3$. Z's algorithm also work.