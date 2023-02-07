---
layout: ../../../layouts/Blog.astro
title: Rust - Borrowing
description: understand rust borrowing
date: 2023-02-07T04:18:12.529Z
thumbnail: /assets/download.png
---
## Borrowing

Reference: [tutorialspoint](https://www.tutorialspoint.com/rust/rust_borrowing.htm)

![](/assets/download.png)

In order to understand why we have borrowing, you need to take a look at ownership first, read here [rust-ownership.](https://nath-blog.netlify.app/blog/rust/rust-ownership/)

It is very **inconvenient** to pass the ownership of a variable to another function and then return the ownership. Rust supports a concept, `borrowing`, where the ownership of a value is transferred temporarily to an entity and then returned to the original owner entity.

consider this example 

```rust
fn main(){
   // a list of nos
   let v = vec![10,20,30];
   print_vector(v);
   println!("{}",v[0]); // this line gives error, 
}
fn print_vector(x:Vec<i32>){
   println!("Inside print_vector function {:?}",x);
}
```

`println!("{}",v[0]);` this line gives error, because `v` is no longer the ownership of `vec![10,20,30];`

### What is Borrowing?

Borrowing in Rust is a mechanism for allowing safe, concurrent access to data ***without giving up ownership***.

This is achieved by passing a reference to the variable ***(& var_name)*** rather than passing the variable/value itself to the function

```rust
fn main(){
   // a list of nos
   let v = vec![10,20,30];
   print_vector(&v); // passing reference
   println!("Printing the value from main() v[0]={}",v[0]); // Printing the value from main() v[0] = 10
}
fn print_vector(x:&Vec<i32>){
   println!("Inside print_vector function {:?}",x); // Inside print_vector function [10, 20, 30]
}
```



### Mutable References

```rust
fn add_one(e: &mut i32) {
   *e+= 1;
}
fn main() {
   let mut i = 3;
   add_one(&mut i);
   println!("{}", i); // 4
}
```



## Mutating a string reference

```rust
fn main() {
   let mut name:String = String::from("TutorialsPoint");
   display(&mut name); 
   //pass a mutable reference of name
   println!("The value of name after modification is:{}",name); // The value of name after modification is:TutorialsPoint Rocks
}
fn display(param_name:&mut String){
   println!("param_name value is :{}",param_name); // param_name value is :TutorialsPoint
   param_name.push_str(" Rocks"); 
   //Modify the actual string,name
}
```