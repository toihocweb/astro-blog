---
layout: ../../../layouts/Blog.astro
title: Phân biệt CSS initial và inherit
description: Phân biệt css initial và inherit, hiểu để không sử dụng sai
date: 2023-01-30T08:21:59.484Z
thumbnail: /assets/css.png
---
## Phân biệt CSS initial và inherit

### I﻿nherit

T﻿rong css, một element có thể kế thừa các thuộc tính CSS từ ***thằng cha gần nhất*** có thuộc tính đó, ví dụ

H﻿TML:

```html
<div class="grandparent">
  <div class="parent">
    <p class="child">This is some text in the child element.</p>
  </div>
</div>
```

C﻿SS:

```css
.grandparent {
  color: blue;
  font-size: 20px;
}

.child {
  color: inherit;
  font-size: inherit;
}
```

K﻿hi đó `.child` sẽ có color và font-size kế thừa từ class `.grandparent`, do đó sẽ có color là **blue** và font size **20px**

### I﻿nitial

khi 1 thuộc tính css có giá trị `initial`nghĩa là, giá trị của nó sẽ được xác định bởi user agent(ví dụ như browser), browser là trình duyệt web đang sử dụng như chrome, firefox...

H﻿TML:

```html
<p class="text">This is some text.</p>
```

C﻿SS: 

```css
.text {
  background-color: yellow;
}

.text {
  background-color: initial; 
  display: initial;
}
```

khi giờ hãy đoán xem background của `.text` là gì nào? 

n﻿ó sẽ có giá trị là `transparent` vì giá trị mặc định của `background-color` là `transparent`ở tất cả các trình duyệt  

T﻿ương tự k﻿hi set initial value cho display, nếu bạn nghĩ giá trị của display là `block`, thì chúc mừng bạn đã sai rồi 

Chính xác thì giá trị initial của display là `inline`, nghĩa là `.text` sẽ có display là `inline`

V﻿ậy để có thể sử dụng được chính xác `initial`, thì bạn **`phải biết đc giá trị mặc định của thuộc tính đó`**, ở trình duyệt tương ứng,

***ở thời điểm  hiện tại, hầu như tất cả các trình duyệt đều có initial value như nhau, nên chúng ta không cần quan tâm nhiều đến trình duyệt nữa.***