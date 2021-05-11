`(key, priority)` s.t. key hold tree property, (randomized)priority hold heap property.

**Claim.** When order and priority determined, treap struture uniquely fixed.

## Non-rotate treap
- **split**: split into two treaps by some key. s.t. keys(left) $<$ key $\leq$ keys(right).
- **merge**: merge two treaps into one by priority heapify.

Use above two basic operations to retain treap property, we can achieve other tree operations.

### Lazy, range reverse
- **split_by_size**: as said.

However we use treap mostly in this fashion, index `[n]` implicitly as key to build initial treap.
Then doing reverse will destory (index-key)tree property, but (randomized)priority almost ensure balance still.

- get rank/position of original index after some reverse.
    - *method 1.* for the chain that node to root, accum left size decided by each edge is left or right.
    - *method 2.* maintain `u=min(l,r)` and erase min when monotonic, special case.