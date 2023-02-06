---
layout: ../../../layouts/Blog.astro
title: Rust - Structure in Rust
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

### Mut a struct instance

```rust
struct Employee {
   name:String,
   company:String,
   age:u32
}
fn main() {
   let mut emp = Employee { // add mut here
      company:String::from("TOIHOCWEB"),
      name:String::from("Nath"),
      age:18
   };
   emp.age = 20;
   println!("Name is :{} company is {} age is {}",emp.name,emp.company,emp.age);
}
```

### Use struct in function as parameter

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
   
   // call print function with emp argument
   print(emp);
}

fn print(emp: Employee) { 
    println!("Name is :{} company is {} age is {}",emp.name,emp.company,emp.age);
} 
```

### Function return struct

```rust
struct Employee {
    name: String,
    company: String,
    age: u32,
}
fn main() {
    let emp1 = Employee {
        company: String::from("TOIHOCWEB1"),
        name: String::from("Nath1"),
        age: 18,
    };

    let emp2 = Employee {
        company: String::from("TOIHOCWEB2"),
        name: String::from("Nath2"),
        age: 20,
    };

    let elder = who_is_elder(emp1, emp2);
    print(elder);
}

fn print(emp: Employee) {
    println!(
        "Name is :{} company is {} age is {}",
        emp.name, emp.company, emp.age
    );
}

fn who_is_elder(emp1: Employee, emp2: Employee) -> Employee {
    if emp1.age > emp2.age {
        return emp1;
    }
    return emp2;
}

```

### Add method to struct

use ***impl***

The first parameter of a method will be **always** ***self***, which represents the calling instance of the structure

```rust
//define dimensions of a rectangle
struct Rectangle {
    width: u32,
    height: u32,
}

//logic to calculate area of a rectangle
impl Rectangle {
    fn area(&self, a: u32) -> u32 {
        //use the . operator to fetch the value of a field via the self keyword
        self.width * self.height + a
    }
}
fn main() {
    // instanatiate the structure
    let small = Rectangle {
        width: 10,
        height: 20,
    };
    //print the rectangle's area
    println!("width is {} height is {} area of Rectangle plus 10 is {}",
        small.width,
        small.height,
        small.area(10)
    );
}

```

### Add static method to struct

Unlike normal methods, a static method will **not take the *&self* parameter**

```rust
//declare a structure
struct Point {
   x: i32,
   y: i32,
}
impl Point {
   //static method that creates objects of the Point structure
   fn getInstance(x: i32, y: i32) -> Point {
      Point { x: x, y: y }
   }
   //display values of the structure's field
   fn display(&self){
      println!("x ={} y={}",self.x,self.y );
   }
}
fn main(){
   // Invoke the static method
   let p1 = Point::getInstance(10,20);
   p1.display();
}
```