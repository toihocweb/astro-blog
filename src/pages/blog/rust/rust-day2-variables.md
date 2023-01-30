---
layout: ../../../layouts/Blog.astro
title: Rust [Day2] - Variables
description: learn how to use variable in Rust
date: 2023-01-30T02:49:59.131Z
thumbnail: /assets/download.png
---

## Rust \[Day2] - Variables

In Rust, a variable is a named storage location that holds a value of a specific type. Variables in Rust are **immutable by default,** meaning their value cannot be changed after they are declared. To make a variable mutable, you need to add the keyword `mut` before its declaration.

Here's an example of declaring and using a variable in Rust:

```rust
let x = 42;  // x is an immutable variable with value 42
println!("The value of x is: {}", x);

let mut y = 33;  // y is a mutable variable with value 33
println!("The value of y is: {}", y);

y = 44;  // changing the value of y
println!("The value of y is now: {}", y);
```

Constants are declared using the `const` keyword and **must be annotated with a type,** as the type cannot be inferred from the value.

```rust
const MAX_ITEMS: u32 = 100;
println!("The maximum number of items is: {}", MAX_ITEMS);

```

`static` is a keyword in Rust used to declare a global variable. `static` variables have a fixed address in memory and are stored in the data segment of a program. Unlike local variables, `static` variables persist throughout the lifetime of the program and **maintain their values across function calls.**

`static` variables can either be mutable (with the keyword `static mut`) or immutable (with the keyword `static`). When declaring an immutable `static` variable, you must also annotate it with its type and provide an initial value.

Here's an example to illustrate how to declare an immutable `static` variable in Rust:

```rust
const MAX_ITEMS: u32 = 100;

static mut COUNTER: u32 = 0;

fn main() {
    println!("The maximum number of items is: {}", MAX_ITEMS);

    unsafe {
        COUNTER += 1;
        println!("The value of the counter is: {}", COUNTER);
    }
}

```

**c﻿onst vs static**

1. Scope: `const` variables are local to the current module, while `static` variables have a global scope.
2. Type inference: `const` variables can have their types inferred from the value they are assigned to, while `static` variables must be annotated with a type.
3. Mutability: `const` variables are always immutable, while `static` variables can be either mutable or immutable.
4. Lifetime: `const` variables have a shorter lifetime than `static` variables. `const` variables are created at compile time and stored in the binary, while `static` variables are created at runtime and stored on the heap.
