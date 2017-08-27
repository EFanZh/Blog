---
title: Essentials of Programming Languages Exercises
enable_mathjax: true
---

## Codes

Code for the exercises can be found [here](https://github.com/EFanZh/EFanZh/tree/master/Racket/eopl-exercises).

## Exercises

> Exercise 0.1 [🟉] We often use phrases like “some languages have property X.” For each such phrase, find one or more
> languages that have the property and one or more languages that do not have the property. Feel free to ferret out this
> information from any descriptive book on programming languages (say Scott (2005), Sebesta (2007), or Pratt & Zelkowitz
> (2001)).

*Skipped for now.*

> Exercise 1.1 [🟉] Write inductive definitions of the following sets. Write each definition in all three styles
> (top-down, bottom-up, and rules of inference). Using your rules, show the derivation of some sample elements of each
> set.
>
> 1. \$$ {3n + 2 \| n in N } $$
> 2. \$$ {2n + 3m + 1 \| n, m in N} $$
> 3. \$$ {(n, 2n + 1) \| n in N} $$
> 4. $$ {(n, n ^ 2) \| n in N} $$ Do not mention squaring in your rules. As a hint, remember the equation
>    $$ (n + 1) ^ 2 = n ^ 2 + 2n + 1 $$.

1. \$$ {3n + 2 \| n in N } $$
   - Top-down:

     $$ n in S $$ if

     - $$ n = 2 $$, or
     - \$$ n - 3 in S $$
   - Bottom-up:

     $$ S $$ is the smallest set that satisfying the following two properties:

     - $$ 2 in S $$, and
     - If $$ n in S $$, then $$ n + 3 in S $$
   - Rules of inference:
     - \$$ () / (2 in S) $$
     - \$$ (n in S) / ((n + 3) in S) $$
2. \$$ {2n + 3m + 1 \| n, m in N} $$
   - Top-down:

     $$ n in S $$ if

     - $$ n = 1 $$, or
     - $$ n - 2 in S $$, or
     - \$$ n - 3 in S $$
   - Bottom-up:

     $$ S $$ is the smallest set that satisfying the following two properties:

     - $$ 1 in S $$, and
     - If $$ n in S $$, then $$ n + 2 in S $$, and
     - If $$ n in S $$, then $$ n + 3 in S $$
   - Rules of inference:
     - \$$ () / (1 in S) $$
     - \$$ (n in S) / ((n + 2) in S) $$
     - \$$ (n in S) / ((n + 3) in S) $$
3.  \$$ {(n, 2n + 1) \| n in N} $$
    - Top-down:

      $$ (m, n) in S $$ if

      - $$ m = 0 $$ and $$ n = 1 $$, or
      - \$$ (m - 1, n - 2) in S $$
    - Bottom-up:

      $$ S $$ is the smallest set that satisfying the following two properties:

      - $$ (0, 1) in S $$, and
      - If $$ (m, n) in S $$, then $$ (m + 1, n + 2) in S $$
    - Rules of inference:
      - \$$ () / ((0, 1) in S) $$
      - \$$ ((m, n) in S) / ((m + 1, n + 2) in S) $$
4. \$$ {(n, n ^ 2) \| n in N} $$

    - Top-down:

      $$ (m, n) in S $$ if

      - $$ m = 0 $$ and $$ n = 0 $$, or
      - \$$ (m - 1, n - 2m + 1) in S $$
    - Bottom-up:

      $$ S $$ is the smallest set that satisfying the following two properties:

      - $$ (0, 0) in S $$, and
      - If $$ (m, n) in S $$, then $$ (m + 1, n + 2m + 1) in S $$
    - Rules of inference:
      - \$$ () / ((0, 0) in S) $$
      - \$$ ((m, n) in S) / ((m + 1, n + 2m + 1) in S) $$

> Exercise 1.2 [🟉🟉] What sets are defined by the following pairs of rules? Explain why.
>
> 1. \$$ (0, 1) in S quad ((n, k) in S) / ((n + 1, k + 7) in S) $$
> 2. \$$ (0, 1) in S quad ((n, k) in S) / ((n + 1, 2k) in S) $$
> 3. \$$ (0, 0, 1) in S quad ((n, i, j) in S) / ((n + 1, j, i + j) in S) $$
> 4. [🟉🟉🟉] $$ (0, 1, 0) in S quad ((n, i, j) in S) / ((n + 1, i + 2, i + j) in S) $$

1. \$$ (0, 1) in S quad ((n, k) in S) / ((n + 1, k + 7) in S) $$

   \$$ {(n, 7n + 1) \| n in N} $$
2. \$$ (0, 1) in S quad ((n, k) in S) / ((n + 1, 2k) in S) $$

   \$$ {(n, 2 ^ n) \| n in N} $$
3. \$$ (0, 0, 1) in S quad ((n, i, j) in S) / ((n + 1, j, i + j) in S) $$

   \$$ {(n, f(n), f(n + 1)) \| n in N, f(0) = 0, f(1) = 1, f(n + 2) = f(n) + f(n + 1)} $$
4. \$$ (0, 1, 0) in S quad ((n, i, j) in S) / ((n + 1, i + 2, i + j) in S) $$

   \$$ {(n, 2n + 1, n ^ 2) \| n in N} $$

> Exercise 1.3 [🟉🟉🟉] Find a set $$ T $$ of natural numbers such that $$ 0 in T $$, and whenever $$ n in T $$, then
> $$ n + 3 in T $$, but $$ T != S $$, where $$ S $$ is the set defined in definition 1.1.2.

Let $$ T = N $$.

> Exercise 1.4 [🟉] Write a derivation from *List-of-Int* to `(-7 . (3 . (14 . ())))`.

*List-of-Int* \\
⇒ `(`*Int*` . `*List-of-Int*`)` \\
⇒ `(-7 . `*List-of-Int*`)` \\
⇒ `(-7 . (`*Int*` . `*List-of-Int*`))` \\
⇒ `(-7 . (3 . `*List-of-Int*`))` \\
⇒ `(-7 . (3 . (`*Int*` . `*List-of-Int*`)))` \\
⇒ `(-7 . (3 . (14 . `*List-of-Int*`)))` \\
⇒ `(-7 . (3 . (14 . ())))`

> Exercise 1.5 [🟉🟉] Prove that if *e* ∈ *LcExp*, then there are the same number of left and right parentheses in *e*.

By induction on the structre of *LcExp*.

If *e* is of *Identifier* form, it has $$ 0 $$ left parenthesis and $$ 0 $$ right parenthesis, the hypothesis holds.

If *e* is of `(lambda (`*Identifier*`) `*LcExp*`)` form, the *Identifier* has $$ 0 $$ parenthese. By induction, *LcExp*
has the same number of left and right parentheses. Let the number be $$ n $$, then *e* has $$ n + 2 $$ left parentheses
and $$ n + 2 $$ right parentheses. The hypothesis holds.

If *e* is of `(`*LcExp*` `*LcExp*`)` form, let $$ m $$ be the number of left or right parentheses in the first *LcExp*,
let $$ n $$ be the number of left or right parentheses in the second *LcExp*, then *e* has $$ m + n + 1 $$ left
parentheses and $$ m + n + 1 $$ right parentheses. The hypothesis holds.

> Exercise 1.6 [🟉] If we reversed the order of the tests in `nth-element`, what would go wrong?

`car` may be applied to empty list.

> Exercise 1.7 [🟉🟉] The error message from `nth-element` is uninformative. Rewrite `nth-element` so that it produces a
> more informative error message, such as “`(a b c)` does not have 8 elements.”

```scheme
(define report-list-too-short
  (lambda (lst n)
    (eopl:error 'nth-element
                "~s does not have ~s elements.~%" lst (+ n 1))))

(define nth-element-helper
  (lambda (lst n current-list i)
    (if (null? current-list)
        (report-list-too-short lst n)
        (if (zero? i)
            (car current-list)
            (nth-element-helper lst n (cdr current-list) (- i 1))))))

(define nth-element
  (lambda (lst n)
    (nth-element-helper lst n lst n)))
```

> Exercise 1.8 [🟉] In the definition of remove-first, if the last line were replaced by `(remove-first s (cdr los))`,
> what function would the resulting procedure compute? Give the contract, including the usage statement, for the revised
> procedure.

**remove-first** : *Sym* × *Listof*(*Sym*) → *Listof*(*Sym*)

**usage**: `(remove-first `*s*` `*los*`)` returns a sub of list from *los*, starting from the symbol after the first
*s*. If *los* doesn’t contain *s*, an empty list is returned.

```scheme
(define remove-first
  (lambda (s los)
    (if (null? los)
        '()
        (if (eqv? (car los) s)
            (cdr los)
            (remove-first s (cdr los))))))
```

> Exercise 1.9 [🟉🟉] Define `remove`, which is like `remove-first`, except that it removes all occurrences of a given
> symbol from a list of symbols, not just the first.

```scheme
(define remove
  (lambda (s los)
    (if (null? los)
        '()
        (if (eqv? (car los) s)
            (remove s (cdr los))
            (cons (car los) (remove s (cdr los)))))))
```

> Exercise 1.10 [🟉] We typically use “or” to mean “inclusive or”. What other meanings can “or” have?

Exclusive or.

> Exercise 1.11 [🟉] In the last line of `subst-in-s-exp`, the recursion is on sexp and not a smaller substructure. Why
> is the recursion guaranteed to halt?

Because `subst` recurs on smaller substructure. We can replace the call to `subst-in-s-exp` with the body of
`subst-in-s-exp`, then `subst` becomes a normal recursive on a smaller substructure.

> Exercise 1.12 [🟉] Eliminate the one call to `subst-in-s-exp` in subst by replacing it by its definition and
> simplifying the resulting procedure. The result will be a version of subst that does not need `subst-in-s-exp`. This
> technique is called *inlining*, and is used by optimizing compilers.

```racket
(define subst
  (lambda (new old slist)
    (if (null? slist)
        '()
        (cons (let ([sexp (car slist)])
                (if (symbol? sexp)
                    (if (eqv? sexp old) new sexp)
                    (subst new old sexp)))
              (subst new old (cdr slist))))))
```

> Exercise 1.13 [🟉🟉] In our example, we began by eliminating the Kleene star in the grammar for *S-list*. Write
> `subst` following the original grammar by using `map`.

```scheme
(define subst-in-s-exp
  (lambda (new old sexp)
    (if (symbol? sexp)
        (if (eqv? sexp old) new sexp)
        (subst new old sexp))))

(define subst
  (lambda (new old slist)
    (map (lambda (sexp) (subst-in-s-exp new old sexp))
         slist)))
```

> Exercise 1.14 [🟉🟉] Given the assumption 0 ≤ *n* < *length*(*v*), prove that `partial-vector-sum` is correct.

Since 0 ≤ *n* < *length*(*v*), we know that *length*(*v*) is at leat 1, so that *v* contains at least one element. We
prove `partial-vector-sum` is correct by induction over *n*.

Base case: if *n* equals to 0, `(partial-vector-sum `*v*` `*n*`)` equals to `(vector-ref `*v*` 0)`, which equals to
$$ sum _ (i = 0) ^ (i = 0) v _ i $$, the claim holds.

Inductive case: if *n* ≠ 0, *n* `(partial-vector-sum `*v*` `*n*`)` equals to
`(add (vector-ref `*v*` `*n*`) (partial-vector-sum `*v*` (- `*n*` 1)))`, which equals to
$$ v _ n + sum _ (i = 0) ^ (i = n - 1) v _ i $$, which equals to $$ sum _ (i = 0) ^ (i = n) v _ i $$, the claim holds.

> Exercise 1.15 [🟉] `(duple n x)` returns a list containing `n` copies of `x`.
>
> ```scheme
> > (duple 2 3)
> (3 3)
> > (duple 4 '(ha ha))
> ((ha ha) (ha ha) (ha ha) (ha ha))
> > (duple 0 '(blah))
> ()
> ```

```scheme
(define duple-helper
  (lambda (lst n x)
    (if (zero? n)
        lst
        (duple-helper (cons x lst) (- n 1) x))))

(define duple
  (lambda (n x)
    (duple-helper '() n x)))
```

> Exercise 1.16 [🟉] `(invert lst)`, where lst is a list of 2-lists (lists of length two), returns a list with each
> 2-list reversed.
>
> ```scheme
> > (invert '((a 1) (a 2) (1 b) (2 b)))
> ((1 a) (2 a) (b 1) (b 2))
> ```

```scheme
(define invert
  (lambda (lst)
    (map (lambda (x) (list (cadr x) (car x)))
         lst)))
```

> Exercise 1.17 [🟉] `(down lst)` wraps parentheses around each top-level element of `lst`.
>
> ```scheme
> > (down '(1 2 3))
> ((1) (2) (3))
> > (down '((a) (fine) (idea)))
> (((a)) ((fine)) ((idea)))
> > (down '(a (more (complicated)) object))
> ((a) ((more (complicated))) (object))
> ```

```scheme
(define down
  (lambda (lst)
    (map (lambda (x) (list x))
         lst)))
```

> Exercise 1.18 [🟉] `(swapper s1 s2 slist)` returns a list the same as slist, but with all occurrences of `s1` replaced
> by `s2` and all occurrences of `s2` replaced by `s1`.
>
> ```scheme
> > (swapper 'a 'd '(a b c d))
> (d b c a)
> > (swapper 'a 'd '(a d () c d))
> (d a () c a)
> > (swapper 'x 'y '((x) y (z (x))))
> ((y) x (z (y)))
> ```

```scheme
(define swapper
  (lambda (s1 s2 slist)
    (map (lambda (sexp)
           (if (symbol? sexp)
               (if (eqv? sexp s1)
                   s2
                   (if (eqv? sexp s2)
                       s1
                       sexp))
               (swapper s1 s2 sexp)))
         slist)))
```

> Exercise 1.19 [🟉] `(list-set lst n x)` returns a list like `lst`, except that the `n`-th element, using zero-based
> indexing, is `x`.
>
> ```scheme
> > (list-set '(a b c d) 2 '(1 2))
> (a b (1 2) d)
> > (list-ref (list-set '(a b c d) 3 '(1 5 10)) 3)
> (1 5 10)
> ```

```scheme
(define list-set
  (lambda (lst n x)
    (if (zero? n)
        (cons x (cdr lst))
        (cons (car lst) (list-set (cdr lst) (- n 1) x)))))
```

> Exercise 1.20 [🟉] `(count-occurrences s slist)` returns the number of occurrences of `s` in `slist`.
>
> ```scheme
> > (count-occurrences 'x '((f x) y (((x z) x))))
> 3
> > (count-occurrences 'x '((f x) y (((x z) () x))))
> 3
> > (count-occurrences 'w '((f x) y (((x z) x))))
> 0
> ```

```scheme
(define count-occurrences-sexp
  (lambda (s sexp)
    (if (symbol? sexp)
        (if (eqv? sexp s) 1 0)
        (count-occurrences s sexp))))

(define count-occurrences
  (lambda (s slist)
    (if (null? slist)
        0
        (+ (count-occurrences-sexp s (car slist))
           (count-occurrences s (cdr slist))))))
```
