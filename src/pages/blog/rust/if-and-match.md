---
layout: ../../../layouts/Blog.astro
title: If and match
description: understand "if, match" in rust, "match" is like "switch-case" in
  another language
date: 2023-01-30T06:44:58.278Z
thumbnail: /assets/download.png
---
## If and match

\-﻿--------------------

**i﻿f - else** is so easy to understand

```rust
if condition1 {
    block1
} else if condition2 {
    block2
} else {
    block_n
}
```

**m﻿atch** is like "switch-case" in another languages

```rust
match code {
    0 => println!("OK"),
    1 => println!("Wires Tangled"),
    2 => println!("User Asleep"),
    
    // _ is like default: 
    _ => println!("Unrecognized Error {}", code)
}
```