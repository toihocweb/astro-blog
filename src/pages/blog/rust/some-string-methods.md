---
layout: ../../../layouts/Blog.astro
title: Rust - String methods
description: some common methods for String in rust
date: 2023-01-30T08:02:11.365Z
thumbnail: /assets/download.png
---
## Some String methods

1. `len`: Returns the length of the string.
2. `is_empty`: Returns `true` if the string is empty, `false` otherwise.
3. `push_str`: Adds a string slice to the end of the string.
4. `pop`: Removes the last character from the string.
5. `trim`: Returns a string slice with leading and trailing whitespaces removed.
6. `split`: Splits the string into multiple sub-strings based on a specified delimiter.
7. `replace`: Replaces all occurrences of one string with another.
8. `to_lowercase`: Converts the string to lowercase.
9. `to_uppercase`: Converts the string to uppercase.
10. `parse`: Parses the string into a specified numeric or boolean type.



```rust
let mut s = String::from("   Hello, World!   ");
println!("Length: {}", s.len()); // Length: 19

println!("Is Empty: {}", s.is_empty()); // Is Empty: false

s.push_str(" How are you?");
println!("After push: {}", s); // After push:    Hello, World!    How are you?

s.pop();
println!("After pop: {}", s); // After pop:    Hello, World!    How are you

let s = s.trim();
println!("After trim: {}", s); // After trim: Hello, World!    How are you

let words: Vec<&str> = s.split(" ").collect();
println!("Words: {:?}", words); // Words: ["Hello,", "World!", "", "", "", "How", "are", "you"]

let s = s.replace("Hello", "Goodbye");
println!("After replace: {}", s); // After replace: Goodbye, World!    How are you

let s = s.to_lowercase();
println!("After to_lowercase: {}", s); // After to_lowercase: goodbye, world!    how are you

let s = s.to_uppercase();
println!("After to_uppercase: {}", s); // After to_uppercase: GOODBYE, WORLD!    HOW ARE YOU

let a = "10";
let n = match a.parse::<i32>() {
    Ok(num) => num,
    Err(_) => panic!("Failed to parse integer"),
};
println!("{}", n + 1); // 11
```