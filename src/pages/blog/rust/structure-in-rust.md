---
layout: ../../../layouts/Blog.astro
title: Structure in Rust
description: Structure is one of the most important concept when start learning
  Rust, let check it
date: 2023-01-31T04:03:30.197Z
thumbnail: /assets/download.png
---
## Structure in Rust

![](/assets/download.png)

### Define Structure

```rust
struct Name_of_structure {
   field1:data_type,
   field2:data_type,
   field3:data_type
}

// example
struct Employee {
   name:String,
   company:String,
   age:u32
}
```

### Initializing a structure

```rust
struct Employee {
   name:String,
   company:String,
   age:u32
}
fn main() {
   let emp = Employee {
      company:String::from("TOIHOCWEB"),
      name:String::from("Nath"),
      age:18
   };
   println!("Name is :{} company is {} age is {}",emp.name,emp.company,emp.age);
  // output - Name is :Nath company is TOIHOCWEB age is 18
}
```