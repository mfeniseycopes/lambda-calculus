# Chapter 2 Exercises

### 1.
a) `λa.(a λb.(b a))`
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

b) `λx.λy.λz.((z x) (z y))`
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

c) `(λf.λg.(λh.(g h) f) λp.λq.p)`
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

d) `λfee.λfi.λfo.λfum.(fum (fo (fi fee)))`
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

e) `((λp.(λq.p λx.(x p)) λi.λj.(j i)) λa.λb.(a (a b)))`
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
