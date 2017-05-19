# Chapter 2 Exercises

### 2.1
* (a) `λa.(a λb.(b a))`
```
<function>
  <bound variable> - a
  <body> - (a λb.(b a))
    <application>
      <function> - <name> - a
      <argument> - λb.(b a)
        <function>
          <bound variable> - b
          <body> - (b a)
            <application>
              <function> - <name> - b
              <argument> - <name> - a
```

* (b) `λx.λy.λz.((z x) (z y))`
```
<function>
  <bound variable> - x
  <bound variable> - y
  <bound variable> - z
  <body> - ((z x) (z y))
    <application>
      <function>
        <application> - (z x)
          <function> - z
          <argument> - x
      <argument>
        <application> (z y)
          <function> - z
          <argument> - y
```

* (c) `(λf.λg.(λh.(g h) f) λp.λq.p)`
```
<application>
  <function> - λf.λg.(λh.(g h) f)
    <bound variable> - f
    <body> - λg.(λh.(g h) f)
      <bound variable> - g
      <body> - (λh.(g h) f)
        <application>
          <function> - λh.(g h)
            <bound variable> - h
            <body> - (g h)
              <application>
                <function> - g
                <argument> - h
          <argument> - f
  <argument> - λp.λq.p
    <bound variable> - p
    <body> λq.p
      <bound variable> - q
      <body> - p
```

* (d) `λfee.λfi.λfo.λfum.(fum (fo (fi fee)))`
```
<function> - λfee.λfi.λfo.λfum.(fum (fo (fi fee)))
  <bound variable> - λfee
  <body> - λfi.λfo.λfum.(fum (fo (fi fee)))
    <bound variable> - λfi
    <body> - λfo.λfum.(fum (fo (fi fee)))
      <bound variable> - λfo
      <body> - λfum.(fum (fo (fi fee)))
        <bound variable> - λfum
        <body> - (fum (fo (fi fee)))
          <application>
            <function> - fum
            <argument> - (fo (fi fee))
              <application>
                <function> - fo
                <argument> - (fi fee)
                  <application>
                    <function> - fi
                    <argument> - fum
```

* (e) `((λp.(λq.p λx.(x p)) λi.λj.(j i)) λa.λb.(a (a b)))`
```
<application> - ((λp.(λq.p λx.(x p)) λi.λj.(j i)) λa.λb.(a (a b)))
  <function> - (λp.(λq.p λx.(x p)) λi.λj.(j i))
    <application>
      <function> - λp.(λq.p λx.(x p))
        <bound variable> - p
        <body> - (λq.p λx.(x p))
          <application>
            <function> - λq.p
              <bound variable> - q
              <body> - p
            <argument> - λx.(x p)
              <bound variable> - x
              <body> - (x p)
                <application>
                  <function> - x
                  <argument> - p
      <argument> - λi.λj.(j i)
        <bound variable> - i
        <body> - λj.(j i)
          <bound variable> - j
          <body> - (j i)
            <application>
              <function> - j
              <argument> - i
  <argument> - λa.λb.(a (a b))
    <bound variable> - a
    <body> - λb.(a (a b))
      <bound variable> - b
      <body> - (a (a b))
        <application>
          <function> - a
          <argument> - (a b)
            <application>
              <function> - a
              <argument> - b
```

### 2.2
* (a) `((λx.λy.(y x) λp.λq.p) λi.i)`
```
((λx.λy.(y x) λp.λq.p) λi.i) =>
(λy.(y λp.λq.p) λi.i) =>
(λi.i λp.λq.p) =>
λp.λq.p =>
```

* (b) `(((λx.λy.λz.((x y) z) λf.λa.(f a)) λi.i) λj.j)`
```
(((λx.λy.λz.((x y) z) λf.λa.(f a)) λi.i) λj.j) =>
((λy.λz.((λf.λa.(f a) y) z) λi.i) λj.j) =>
(λz.((λf.λa.(f a) λi.i) z) λj.j) =>
((λf.λa.(f a) λi.i) λj.j) =>
(λa.(λi.i a) λj.j) =>
(λi.i λj.j) =>
λj.j =>
```

* (c) `(λh.((λa.λf.(f a) h) h) λf.(f f))`
```
(λh.((λa.λf.(f a) h) h) λf.(f f)) =>
((λa.λf.(f a) λf.(f f)) λf.(f f)) =>
(λf.(f λf.(f f)) λf.(f f)) =>
(λf.(f f) λf.(f f))  =>  
(λf.(f f) λf.(f f))  => ...
```

* (d) `((λp.λq.(p q) (λx.x λa.λb.b)) λx.λy.x)`
```
((λp.λq.(p q) (λx.x λa.λb.b)) λx.λy.x) =>
(λq.((λx.x λa.λb.b) q) λx.λy.x) =>
((λx.x λa.λb.b) λx.λy.x) =>
(λa.λb.b λx.λy.x) =>
λb.b
```

* (e) `(((λf.λg.λx.(f (g x)) λs.(s s)) λa.λb.b) λx.λy.x)`
```
(((λf.λg.λx.(f (g x)) λs.(s s)) λa.λb.b) λx.λy.x) =>
((λg.λx.(λs.(s s) (g x)) λa.λb.b) λx.λy.x) =>
((λg.λx.((g x) (g x)) λa.λb.b) λx.λy.x) =>
((λx.((λa.λb.b x) (λa.λb.b x)) λx.λy.x) =>
((λa.λb.b λx.λy.x) (λa.λb.b λx.λy.x)) =>
(λb.b λb.b) =>
λb.b
```

### 2.3
* (a) `identity === (apply (apply identity))`
```
(identity <arg>) =>
<arg>
===
((apply (apply identity)) <arg>) =>
((apply identity) <arg>) =>
(identity <arg>) =>
<arg>
```

* (b) `apply === λx.λy.(((make_pair x) y) identity)`
```
((apply <func>) <arg>) =>
(<func> <arg>)
===
((λx.λy.(((make_pair x) y) identity) <func>) <arg>) =>
(λy.(((make_pair <arg>) y) identity) <func>) =>
(((make_pair <arg>) <func>) identity) ->
(((λfirst.λsecond.λfunc.((func first) second) <arg>) <func>) identity) =>
((λsecond.λfunc.((func <func>) second) <arg>) identity) =>
(λfunc.((func <func>) <arg>) identity) =>
((identity <func>) <arg>) =>
(<func> <arg>)
```

* (c) `identity === (self_apply (self_apply select_second))`
```
(identity <func>) =>
<func>
===
((self_apply (self_apply select_second)) <func>) =>
((λs.(s s) (λs.(s s) select_second)) <func>) =>
(((select_second select_second) (select_second select_second)) <func>) =>
((λsecond.second λsecond.second) <func>) =>
<func>
```

### 2.4
```
# define a function which collects a triplet and takes a selector function
def make_triplet = λfirst.λsecond.λthird.λfunc.(((func first) second) third)

# define selector functions
def triplet_first = λfirst.λsecond.λthird.first
def triplet_second = λfirst.λsecond.λthird.second
def triplet_third = λfirst.λsecond.λthird.third

# proof
((((make_triplet <selector>) third) second) first) =>
((((λfirst.λsecond.λthird.λfunc.(((func first) second) third) <selector>) <arg3>) <arg2>) <arg1>) =>
(((λsecond.λthird.λfunc.(((func <arg1>) second) third) <selector>) <arg3>) <arg2>) =>
((λthird.λfunc.(((func <arg1>) <arg2>) third) <selector>) <arg3>) =>
(λfunc.(((func <arg1>) <arg2>) <arg3>) <selector>) =>
(((<selector> <arg1>) <arg2>) <arg3>) =>

# <selector> = triplet_first
(((λfirst.λsecond.λthird.first <arg1>) <arg2>) <arg3>) =>
((λsecond.λthird.<arg1> <arg2>) <arg3>) =>
(λthird.<arg1> <arg3>) =>
<arg1>

# <selector> = triplet_second
(((λfirst.λsecond.λthird.second <arg1>) <arg2>) <arg3>) =>
((λsecond.λthird.second <arg2>) <arg3>) =>
(λthird.<arg2> <arg3>) =>
<arg2>

# <selector> = triplet_third
(((λfirst.λsecond.λthird.first <arg1>) <arg2>) <arg3>) =>
((λsecond.λthird.third <arg2>) <arg3>) =>
(λthird.third <arg3>) =>
<arg3>
```

### 2.5
* (a) `λx.λy.(λx.y λy.x)`
```
x bound: λx.λy.(λx.y λy.{x})
x free : λy.(λx.y λy.{x})
         (λx.y λy.{x})
         λy.{x}
         {x}
y bound: λx.λy.(λx.{y} λy.x)
         λy.(λx.{y} λy.x)
y free : (λx.{y} λy.x)
         λx.{y}
         {y}
```        

* (b) `λx.(x (λy.(λx.x y) x))`
```
x bound: λx.({x} (λy.(λx.x y) {x}))
x free : ({x} (λy.(λx.x y) {x}))
         (λy.(λx.x y) {x})
         {x}
y bound: λx.({x} (λy.(λx.x {y}) x))
         ...
         (λy.(λx.x {y}) x)
y free : (λx.x {y})
         {y}
```

* (c) `λa.(λb.a λb.(λa.a b))`
```
a bound: λa.(λb.{a} λb.(λa.a b))
         λa.(λb.a λb.(λa.{a} b))
         ...
         λa.{a}
a free : (λb.{a} λb.(λa.a b)
         ...
         {a}
b bound: λa.(λb.a λb.(λa.a {b}))
         ...
         λb.(λa.a {b})
b free : (λa.a {b})
         {b}
```

* (d) `λfree.bound λbound.(λfree.free bound)`
```
free bound : λfree.bound λbound.(λfree.{free} bound)
             ...
             λfree.{free}
free free  : {free}
bound bound: λfree.bound λbound.(λfree.free {bound})
             ...
             λbound.(λfree.free {bound})
bound free : λfree.{bound} λbound.(λfree.free bound)
             (λfree.free {bound})
             ...
             {bound}
```

* (e) `λp.λq.(λr.(p (λq.(λp.(r q)))) (q p))`
```
p bound: λp.λq.(λr.({p} (λq.(λp.(r q)))) (q p))
         λp.λq.(λr.(p (λq.(λp.(r q)))) (q {p}))
p free : λq.(λr.({p} (λq.(λp.(r q)))) (q p))
         ...
         {p}
         λq.(λr.(p (λq.(λp.(r q)))) (q {p}))
         ...
         {p}
q bound: λp.λq.(λr.(p (λq.(λp.(r q)))) ({q} p))
         λq.(λr.(p (λq.(λp.(r q)))) ({q} p))
         λp.λq.(λr.(p (λq.(λp.(r {q})))) (q p))
         ...
         λq.(λp.(r {q}))
q free : (λr.(p (λq.(λp.(r q)))) ({q} p))
         ...
         {q}
         (λp.(r {q}))
         ...
         {q}
r bound: λp.λq.(λr.(p (λq.(λp.({r} q)))) (q p))
         ...
         λr.(p (λq.(λp.(r q))))
r free : (p (λq.(λp.(r q))))
         ...
         {r}
```

### 2.6
* (a)
```
λx.λy.(λx.y λy.x) ɑ->
λx1.λy1.(λx2.y1 λy2.x1)
```

* (b)
```
λx.(x (λy.(λx.x y) x)) ɑ->
λx1.(x1 (λy.(λx2.x2 y) x1)) ɑ->
λx1.(x1 (λy.(λx2.x2 y) x1))
```

* (c)
```
λa.(λb.a λb.(λa.a b)) ɑ->
λa1.(λb1.a1 λb2.(λa2.a2 b2))
```

* (d)
```
λfree.bound λbound.(λfree.free bound) ɑ->
λfree1.bound1 λbound2.(λfree2.free2 bound2)
```

* (e)
```
λp.λq.(λr.(p (λq.(λp.(r q)))) (q p)) ɑ->
λp1.λq1.(λr.(p1 (λq2.(λp2.(r q2)))) (q1 p1)) ɑ->
```
