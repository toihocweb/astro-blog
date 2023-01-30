---
layout: ../../../layouts/Blog.astro
title: Understand this in javascript
description: Hiểu "this" trong javascript, giúp bạn tự tin hơn khi code với mấy ông senior
date: 2023-01-30T16:04:47.264Z
thumbnail: /assets/js-15429579443112042672363-crop-1542957949936317424252.webp
---
## Hiểu "this" trong javascript

"`T﻿his`" không còn là khái niệm quá xa lạ với những developer đã làm việc với javascript lâu năm, 

Cùng nhau tìm hiểu xem `this` có gì khó không nhé,



### This bên trong object method

**object method** là 1 cái function nằm bên trong object á

khi đó `this` sẽ có giá trị là object mà method đó thuộc zề

ở ví dụ bên dưới `this` chính là `user`

```javascript
let user = {
  name: "John",
  greet: function () {
    console.log("Hello, my name is " + this.name); //  this = user
  },
};


user.greet(); // outputs "Hello, my name is John"

```

Tuy nhiên hãy cẩn thẩn với ví dụ dưới đây

```javascript
let user = {
  name: "John",
  greet: function () {
    console.log("Hello, my name is " + this.name); //  this = user
    const innerFunc = function () {
      console.log("InnerFunc::Hello, my name is " + this.name); // this = window
    };
    innerFunc();
  },
};

user.greet(); // "Hello, my name is John" 
			  // "InnerFunc::Hello, my name is undefined"

```

this bên trong `innerFunc` không phải là object user nữa nhé, mà nó là window object (window object là khi chạy js trên browser mới có nha, còn chạy trên node thì là object rỗng {} )

Vậy làm sao để `this` trong function `innerFunc` là object user nhỉ, đơn giản thôi, ta có thể sử dụng `call`, `bind`, `apply`

```javascript
let user = {
  name: "John",
  greet: function () {
    console.log("Hello, my name is " + this.name); //  this = user
    const innerFunc = function () {
      console.log("InnerFunc::Hello, my name is " + this.name); // this = window
    }.bind(this); // sử dụng bind, khi đó this chính là user
    innerFunc();
  },
};

user.greet(); // "Hello, my name is John" 
			  // "InnerFunc::Hello, my name is John"

```



### This bên trong function, không có strict mode

khi đó `this` chính là `global object`, nếu chạy js trên browser thì đó là window object, còn node thì là object rỗng

```javascript
function myFunction() {
  console.log(this);  // outputs the window object
}

```