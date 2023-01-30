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
      console.log("InnerFunc::Hello, my name is " + this.name); // this = window, output "InnerFunc::Hello, my name is undefined"
    };
    innerFunc();
  },
};

user.greet(); // "Hello, my name is John" 
			  

```

this bên trong `innerFunc` không phải là object user nữa nhé, mà nó là window object (window object là khi chạy js trên browser mới có nha, còn chạy trên node thì là object rỗng {} )

Vậy làm sao để `this` trong function `innerFunc` là object user nhỉ, đơn giản thôi, ta có thể sử dụng `call`, `bind`, `apply,`hoặc `chuyển innerFunc thành arrow function`

```javascript
let user = {
  name: "John",
  greet: function () {
    console.log("Hello, my name is " + this.name); //  this = user
    const innerFunc = function () {
      console.log("InnerFunc::Hello, my name is " + this.name); //  output "InnerFunc::Hello, my name is John"
    }.bind(this); // sử dụng bind, khi đó this = user
    innerFunc();
  },
};

user.greet(); // "Hello, my name is John" 

```



### This bên trong function, không có strict mode

khi đó `this` chính là `global object`, nếu chạy js trên browser thì đó là window object, còn node thì là object rỗng

```javascript
function myFunction() {
  console.log(this);  // outputs the window object
}

```



### This bên trong function, có strict mode

```javascript
function myFunction() {
  "use strict";  // enable strict mode
  console.log(this);  // outputs undefined
}

myFunction();

```

lưu ý là trong object method, thì vẫn là object mà nó thuộc zề

```javascript
let obj = {
  name: "John",
  greet: function() {
    "use strict";  // enable strict mode
    console.log("Hello, my name is " + this.name);  // outputs "Hello, my name is John"
  }
};

obj.greet();

```



### This trong class

khi sử dụng từ khóa `new` thì 1 object rỗng được tạo ra, `this` chính là object rỗng đó

```javascript
class User {
  constructor() {
    this.name = "Maria;
  }
}

const user = new User();
console.log(user.name); // Maria
```



### This trong arrow function

có 2 trường hợp

1. arrow function đó không nằm trong regular function
2. arrow function đó nằm trong regular function

#### arrow function không nằm trong regular function

khi đó `this` chính là global object(window object nếu chạy trên trình duyệt)

```javascript
const test = () => {
  console.log(this); // this = window
};
test();

```

#### arrow function nằm trong regular function

```javascript
let obj = {
  name: "John",
  greet: function() {
    console.log("Hello, my name is " + this.name);  // outputs "Hello, my name is John"

    let arrowFunction = () => {
      console.log("Arrow function says: " + this.name);  // outputs "Arrow function says: John"
    };

    arrowFunction();
  }
};

obj.greet();

```

arrowFunction nằm trong regular function `greet`, khi đó `this` bên trong arrowFunction sẽ chính là `this` của `greet`

### This bên trong event

`this` bên trong event chính là phần tử đang thực hiện event đó, 

ở code bên dưới chúng ta add event vào `el` khi đó `this` chính là `el`

```javascript
const el = document.getElementById('my-id');

el.addEventListener('click', function() {
  console.log(this === el); // true
});
```

### This trong call, apply, bind