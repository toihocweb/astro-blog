---
layout: ../../../layouts/Blog.astro
title: Rust - Types
description: learn fundamental type in Rust
date: 2023-01-29T15:11:53.064Z
thumbnail: /assets/download.png
---

## F﻿undamental Types

### S﻿tring

```rust
let speech = "\"Ouch!\" said the well.\n";

println!("In the room the women come and go,
    Singing of Mount Abora");

let default_win_install_path = r"C:\Program Files\Gorillas";

// regex
let pattern = Regex::new(r"\d+(\.\d+)*");
```

### Fixed-Width Numeric Types

1. u﻿nsignd integer: u8, u16, u32, u64, u128, usize
2. s﻿igned integer: i8, i16, i32, i64, i128, isize
3. f﻿loating point: f32, f64

### B﻿oolean Types

t﻿rue, false

b﻿ool -> integer

```rust
assert_eq!(false as i32, 0);
assert_eq!(true  as i32, 1);
```

### C﻿haracters

represents a single Unicode character, as a 32-bit value.

![](/assets/screenshot-2023-01-29-at-22.24.26.png)

### Tuples

```rust
let t = (1, "hello", 3.14);

let (a, b, c) = t;

println!("a = {}", a); // a = 1
println!("b = {}", b); // b = "hello"
println!("c = {}", c); // c = 3.14

// You can also access individual elements of a tuple using indexing, starting from zero:
let x = t.0;
println!("x = {}", x); // x = 1
```

### Reference Type

```rust
let mut s = String::from("hello");

let r1 = &s; // immutable reference
let r2 = &s; // immutable reference
println!("{} and {}", r1, r2); // "hello" and "hello"

let r3 = &mut s; // mutable reference
println!("{}", r3); // "hello"
```

d﻿iff **_immutable reference_** vs **_mutable reference_**

```rust
let mut s = String::from("hello");

let r3 = &mut s;
*r3 += ", world";

println!("{}", s); // "hello, world"
```

### A﻿rray

Arrays have a fixed length, meaning that the length of an array cannot be changed once it has been defined

Arrays are stored on the stack, meaning that their memory is automatically freed when they go out of scope

Arrays have a homogeneous type, meaning that all elements in an array must have the same type

```rust
let lazy_caterer: [u32; 6] = [1, 2, 4, 7, 11, 16];
assert_eq!(lazy_caterer[3], 7);

let mut sieve = [true; 10000];
for i in 2..100 {
    if sieve[i] {
        let mut j = i * i;
        while j < 10000 {
            sieve[j] = false;
            j += i;
        }
    }
}

assert!(sieve[211]);
assert!(!sieve[9876]);
```

### V﻿ector

Vectors can grow or shrink in size at runtime.

Vectors are stored on the heap, meaning that they have to be explicitly deallocated when they are no longer needed.

Vectors can store elements of any type.

```rust
let mut pal = Vec::new();
pal.push("step");
pal.push("on");
pal.push("no");
pal.push("pets");
assert_eq!(pal, vec!["step", "on", "no", "pets"]);
```

### S﻿lice

*Slices* let you reference a contiguous sequence of elements in a collection rather than the whole collection. A slice is a kind of reference, so it does not have ownership.

r﻿emeber use: **{:?}**

println!("The slice is: **{:?}**", s);

**S﻿lice for array**

```rust
let mut a = [1, 2, 3, 4, 5];
let s = &mut a[1..4];
for x in &mut *s {
*x += 10;
}
println!("The slice is: {:?}", s);
```

**S﻿lice for string**

```rust
let s = String::from("Hello, world!");
let hello = &s[0..5];
println!("{}", hello);
```

**S﻿lice for vector**

```rust
let v = vec![1, 2, 3, 4, 5];
let s = &v[1..4];

println!("The slice is: {:?}", s);
// The slice is: [2, 3, 4]
```
