---
layout: ../../../layouts/Blog.astro
title: Phân biệt "in" và hasOwnProperty trong javascript
description: cả 2 đều có thể dùng để kiểm tra 1 property có tồn tại trong object
  hay không, vậy có khác nhau gì không nhỉ?
date: 2023-03-30T02:34:35.905Z
thumbnail: /assets/js-15429579443112042672363-crop-1542957949936317424252.webp
---
## Phân biệt "in" và hasOwnProperty trong javascript

![](/assets/js-15429579443112042672363-crop-1542957949936317424252.webp)

### "in" trong js

Có thể dùng "in" để kiểm tra 1 property có tồn tại trong object hay không, nhưng ngoài ra nó còn có thể dùng để kiểm tra 1 property có tồn tại trong prototype chain.

### "hasOwnProperty"

Có thể dùng hasOwnProperty dùng để kiểm tra 1 property có tồn tại trong object hay không, `không bao gồm `property của prototype chain.

```javascript
const user = {
  name: 'John',
  age: 30
};

console.log('name' in user); // true
console.log(user.hasOwnProperty('name')); // true
```

giờ check thêm prototype nhé

```javascript
const user = {
  name: 'John',
  age: 30
};

// trong object cũng có phương thức toString nhoaa
console.log('toString' in user); // true
console.log(user.hasOwnProperty('toString')); // false
```

```javascript
function Person() {
  this.name = 'Nguyen Van A';
}

Person.prototype.age = 20;

const person = new Person();

console.log('name' in person); // true
console.log('age' in person); // true

console.log(person.hasOwnProperty('name')); // true
console.log(person.hasOwnProperty('age')); // false
```