---
layout: ../../../layouts/Blog.astro
title: Rust - Ownership
description: if you already know reference type in js, it's easy for you to
  understand ownership, but a bit diff, let's check
date: 2023-02-06T16:25:33.753Z
thumbnail: /assets/download.png
---
## Ownership

Reference: [tutorialspoint](https://www.tutorialspoint.com/rust/rust_ownership.htm)

![](/assets/download.png)

### What is Ownership?

Each value in Rust has a **variable** that is called **owner** of the value. 

* Each data can have **only one** owner at a time.
* Two variables cannot point to the same memory location. The variables will always be pointing to different memory locations.

### Transferring Ownership

3 ways to transfer ownership

* Assigning value of one variable to another variable.
* Passing value to a function.
* Returning value from a function.

#### Assigning value of one variable to another variable

```rust
fn main(){
   let v = vec![1,2,3]; 
   // vector v owns the object in heap

   //only a single variable owns the heap memory at any given time
   let v2 = v; 
   // here two variables owns heap value,
   //two pointers to the same content is not allowed in rust

   //Rust is very smart in terms of memory access ,so it detects a race condition
   //as two variables point to same heap

   println!("{:?}",v);
}
```

#### Passing value to a function

```rust
fn main(){
   let v = vec![1,2,3];     // vector v owns the object in heap
   let v2 = v;              // moves ownership to v2
   display(v2);             // v2 is moved to display and v2 is invalidated
   println!("In main {:?}",v2); // v2 is No longer usable here
}
fn display(v:Vec<i32>){
   println!("inside display {:?}",v);
}
```

#### Returning value from a function

```rust
fn main(){
   let v = vec![1,2,3];       // vector v owns the object in heap
   let v2 = v;                // moves ownership to v2
   let v2_return = display(v2); // v2_return becomes the owner of the vector, and v and v2 no longer have ownership.
   println!("In main {:?}",v2_return);
}
fn display(v:Vec<i32>)->Vec<i32> { 
   println!("inside display {:?}",v);
   return v;
}
```

#### Ownership and Primitive Types

In case of **primitive** **types**, contents from one variable is copied to another. So, there is **no ownership** move happening. This is because a primitive variable needs less resources than an object and **stored in the stack**, not heap. Consider the following example

```rust
fn main(){
   let u1 = 10;
   let u2 = u1;  // u1 value copied(not moved) to u2

   println!("u1 = {}",u1);
}
```