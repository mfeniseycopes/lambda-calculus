# Chapter 3 Exercises

### 3.1
Define a calculus implementation of `implies`.

`def implies = λx.λy.(x y true)`

| x | y | `x => y` | `λx.λy.(x y true)` |
|:-:|:-:|:------:|  |
| true | true |    true   |`(true true true) => true` |
| true | false |    false   |`(true false true) => false`|
| false | true |    true   |`(false true true) => true` |
| false | false |    true   |`(false false true) => true` |

### 3.2
Define a calculus implementation of `equiv`.

`def equiv = λx.λy.(x y (not y))`

| x | y | `x == y` | `(x y (not y))`                                   |
|:-:|:-:|:------:|--------------------------------------------------|
| true | true |    true   | `(true true (not true)) => true`                   |
| true | false |    false   | `(true false (not false)) => false`                |
| false | true |    false   | `(false true (not true)) => (not true) => false`   |
| false | false |    true   | `(false false (not false)) => (not false) => true` |


### 3.3
Show that pairs are equivalent.

* (a)
  * (1) `λx.λy.(and (not x) (not y))`
  * (2) `λx.λy.(not (or x y))`

```
x = true; y = true

(λx.λy.(and (not x) (not y)) true true) =>
(and (not true) (not true)) =>
((not true) (not true) false) =>
(false false false) => false

(λx.λy.(not (or x y)) true true) =>
(not (or true true)) =>
(not true) => false

x = true; y = false

(λx.λy.(and (not x) (not y)) true false) =>
(and (not true) (not false)) =>
((not true) (not false) false) =>
(false true false) => false

(λx.λy.(not (or x y)) true false) =>
(not (or true false)) =>
(not (true true false)) =>
(not true) => false

x = false; y = true

(λx.λy.(and (not x) (not y)) false true) =>
(and (not false) (not true)) =>
(and true false) => (true false false) => false

(λx.λy.(not (or x y)) false true) =>
(not (or false true)) =>
(not (false true true)) => (not true) => false

x = false; y = false

(λx.λy.(and (not x) (not y)) false false) =>
(and (not false) (not false)) =>
(and true true) => (true true false) => true

(λx.λy.(not (or x y)) false false) =>
(not (or false false)) =>
(not (false true false)) =>
(not false) => true
```

* (b)
  * (1) `implies`
  * (2) `λx.λy.(implies (not y) (not x))`

```
x = true; y = true

(implies true true) =>
(true true true) => true

(λx.λy.(implies (not y) (not x)) true true) =>
(implies false false) =>
(false false true) => true

x = true; y = false

(implies true false) =>
(true false true) => false

(λx.λy.(implies (not y) (not x)) true false) =>
(implies (not false) (not true)) =>
(implies true false) =>
(true false true) => false

x = false; y = true

(implies false true) =>
(false true true) => true

(λx.λy.(implies (not y) (not x)) false true) =>
(implies (not true) (not false)) =>
(implies false true) =>
(false true true) => true

x = false; y = false

(implies false false) =>
(false false true) => true

(λx.λy.(implies (not y) (not x)) false false) =>
(implies (not false) (not false)) =>
(implies true true) =>
(true true true) => true
```

### 3.4
Show `λx.(succ (pred x))` is equivalent to `λx(pred (succ x))` for nonzero x and not equivalent for zero x.

**Definitions**
```
def succ = λn.λs(s false n)
def pred = λn.((iszero n) zero (n select_second))
```

```
n > 0

(λx.(succ (pred x)) n) =>
(succ (pred n)) =>
(succ (n - 1)) => n

(λx(pred (succ x) n) =>
(pred (succ n)) =>
(pred (n + 1)) => n

n = 0

Here we have defined pred function to return identity if applied to zero, so we are unable to decrement initial argument of zero.

(λx.(succ (pred x)) n) =>
(succ (pred n)) =>
(succ zero) => one

(λx(pred (succ x) n) =>
(pred (succ n)) =>
(pred one) => zero
```
