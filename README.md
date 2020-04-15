# rapi - A safe and user friendly R extension interface.

Low-level R library bindings

[![Travis Build Status](https://api.travis-ci.org/extendr/rapi.svg?branch=master)](https://travis-ci.org/extendr/rapi)
[![Crates.io](http://meritbadge.herokuapp.com/rapi)](https://crates.io/crates/ndarray)
[![License: Apache-2.0](https://img.shields.io/crates/l/rustr.svg)](#License)

[API Documentation](https://extendr.github.io/rapi/master/rapi/index.html)

This library aims to provide an interface that will be familiar to
first-time users of Rust or indeed any compiled language.

Anyone who knows the R library should be able to write R extensions.

This library is just being born, but goals are:

Implement common R functions such as c() and print()

Example:

```
let v = c!(1, 2, 3);
let l = list!(a=1, b=2);
print!(v, l);
```

Provide a wrapper for r objects.

Example:

```
let s = RObj::from("hello");
let i = RObj::from(1);
let r = RObj::from(1.0);
```

Provide iterator support for creation and consumption of r vectors.

Example:

```
let res = (1..=100).iter().collect::<RObj>();
for x in res {
    print!(x);
}
```

Provide a procedural macro to adapt Rust functions to R

Example:

```
#[derive(RCallable)]
fn fred(a: i32) -> i32 {
    a + 1
}
```

In R:

```

result <- .Call("fred", 1)

```