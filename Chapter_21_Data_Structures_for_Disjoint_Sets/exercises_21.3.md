## 21.3 Disjoint-set forests

### 21.3-1

> Redo Exercise 21.2-2 using a disjoint-set forest with union by rank and path compression.

$\dots$

### 21.3-2

> Write a nonrecursive version of FIND-SET with path compression.

$\dots$

### 21.3-3

> Give a sequence of $m$ MAKE-SET, UNION, and FIND-SET operations, $n$ of which are MAKE-SET operations, that takes $\Omega(m \lg n)$ time when we use union by rank only.

$\Omega((m - 2n) \lg n) = \Omega(m \lg n)$

### 21.3-4

> Suppose that we wish to add the operation PRINT-SET$(x)$, which is given a node $x$ and prints all the members of $x$'s set, in any order. Show how we can add just a single attribute to each node in a disjoint-set forest so that PRINT-SET$(x)$ takes time linear in the number of members of $x$'s set and the asymptotic running times of the other operations are unchanged. Assume that we can print each member of the set in $O(1)$ time.

Each member has a pointer points to the next element in the set, which forms a circular linked list. When union two sets $x$ and $y$, swap $x.next$ and $y.next$ to merged the two linked lists.

### 21.3-5 $\star$

> Show that any sequence of $m$ MAKE-SET, FIND-SET, and LINK operations, where all the LINK operations appear before any of the FIND-SET operations, takes only $O(m)$ time if we use both path compression and union by rank. What happens in the same situation if we use only the path-compression heuristic?

Suppose that there are $n$ MAKE_SET, then after the LINKs, there are only $n$ elements to compress, thus it takes $O(m)$ time. It doesn't matter whether we use union by rank or not.
