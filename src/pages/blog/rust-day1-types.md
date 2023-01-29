---
layout: ../../layouts/Blog.astro
title: Rust [Day1] - Types
description: learn fundamental type in Rust
date: 2023-01-29T15:11:53.064Z
thumbnail: data:image/png;base64,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
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

d﻿iff ***immutable reference*** vs ***mutable reference***

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

Vectors  can store elements of any type.

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