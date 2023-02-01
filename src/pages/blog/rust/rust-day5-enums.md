---
layout: ../../../layouts/Blog.astro
title: Rust [Day5] - Enums
description: "how to use enums in Rust, let check "
date: 2023-02-01T03:17:14.500Z
thumbnail: /assets/download.png
---
## Enums in Rust

![](/assets/download.png)

### Simple Enum

`#[derive(Debug)]` - make this `enum` printable

```rust
// The `derive` attribute automatically creates the implementation
// required to make this `enum` printable with `fmt::Debug`.
#[derive(Debug)]
enum GenderCategory {
   Male,
   Female
}
fn main() {
   let male = GenderCategory::Male;
   let female = GenderCategory::Female;

   println!("{:?}",male);
   println!("{:?}",female);
}
```



* **Male, Female** is called "`variant`"

### Struct and Enum

`#[derive(Debug)]` - make this `struct` printable

```rust
#[derive(Debug)]
enum GenderCategory {
    Male,
    Female,
}

#[derive(Debug)]
struct Person {
   name:String,
   gender:GenderCategory
}

fn main() {
   let p1 = Person {
      name:String::from("Mohtashim"),
      gender:GenderCategory::Male
   };
   let p2 = Person {
      name:String::from("Amy"),
      gender:GenderCategory::Female
   };
   println!("{:?}",p1);
   println!("{:?}",p2);
}

```

### Option Enum

Rust already define this enum, we dont need to define, this is how Option enum defined

```rust
enum Option<T> {
   Some(T), // used to return a value
   None // used to return null, as Rust doesn't support the null keyword
}
```

example😜

```rust
fn main() {
   let result = is_even(3);
   println!("{:?}",result); // None
   println!("{:?}",is_even(30)); // Some(true)
}

fn is_even(no:i32)->Option<bool> {
   if no%2 == 0 {
      Some(true)
   } else {
      None
   }
}
```