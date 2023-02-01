---
layout: ../../../layouts/Blog.astro
title: Image Loading [part 1]
description: kĩ thuật load ảnh dựa vào screen
date: 2023-02-01T04:32:47.290Z
thumbnail: /assets/1-1477901-1450843193145.webp
---
## Kĩ thuật **load hình ảnh dựa vào screen**

![](/assets/1-1477901-1450843193145.webp)

1 tấm ảnh để có thể hiện trên trình duyệt thì nó trải qua những giai đoạn nào nhỉ ? 

Nó sẽ qua 2 giai đoạn chính sau:

1. Tải ảnh
2. Load ảnh 

thường thì giai đoạn `tải ảnh` sẽ mất nhiều thời gian, vì giả sử tấm ảnh của bạn có kích thước 10Mb, thì nó phải tải xong 10Mb đó thì mới có thể load tấm hình ra web được

vậy giả sử người dùng sử dụng điện thoại, sài mạng 3G thì sao đây, 

đợi nó tải 10Mb xong chắc k còn muốn sử dụng web của chúng ta nữa

> vậy có cách nào để website hiện các tấm hình khác nhau, trên các screen khác nhau không ?

ví dụ, nếu user sử dụng điện thoại để lướt web, thì chúng ta sẽ sử dụng tấm hình có kích thước nhỏ hơn, 1Mb chẳng hạn…

Khi đó việc trải nghiệm của user sẽ được tốt hơn, khi việc load tấm hình 1Mb sẽ nhanh hơn rất nhiều so với 10Mb

***Hãy xem chúng ta có những solution nào phổ biến nhé***

##### Solution 1: viết đoạn script để detect xem kích thước hiện tại là bao nhiêu, sau đó load hình tương ứng

```javascript
// Define the different image sources for each screen size
const smallScreenImg = '1.jpg'; // 1MB 
const mediumScreenImg = '2.jpg'; // 2MB
const largeScreenImg = '3.jpg'; // 10MB

// Get the current screen width
const screenWidth = window.innerWidth;

// Choose the appropriate image source based on the screen width
let imgSource;
if (screenWidth < 600) {
  imgSource = smallScreenImg;
} else if (screenWidth < 900) {
  imgSource = mediumScreenImg;
} else {
  imgSource = largeScreenImg;
}

// Get the image element
const imgElement = document.querySelector('#myImage');

// Set the src attribute of the image element to the appropriate image source
imgElement.setAttribute('src', imgSource);
```

**Ưu điểm:**

1. chỉ load những tấm hình phù hợp với kích thước màn hình 
2. trải nghiệm người dùng tốt hơn vì hình đc load nhanh và được optimize phù hợp

**Nhược điểm:**

1. server cần nhiều dung lượng để chứa nhiều hình hơn 
2. kĩ thuật này cần phải có javascript mới chạy, nghĩa là nếu js bị disable thì k chạy được

##### Solution 2: sử dụng thẻ html <picture>

```html
<picture>
    <source srcset="images/1.jpg" media="(max-width: 600px)">
    <source srcset="images/2.jpg" media="(max-width: 900px)">
    <img src="images/3.jpg" alt="">
</picture>
```

đọc thôi cũng hiểu rồi, khỏi giải thích nhé

**trình duyệt hổ trợ**

![](/assets/screenshot-2023-02-01-at-12.37.31.png)

**Ưu điểm:**

1. chỉ load những tấm hình phù hợp với kích thước màn hình 
2. trải nghiệm người dùng tốt hơn vì hình đc load nhanh và được optimize phù hợp

**Nhược điểm:**

1. server cần nhiều dung lượng để chứa nhiều hình hơn 
2. bị giới hạn về trình duyệt
3. hi thay đổi kích thước màn hình thì trình duyệt sẽ phải tính toán lại media, và tải hình tương ứng, dẫn đến việc nếu hình ảnh không được cache thì trình duyệt sẽ liên tục download hình về

[![](https://i.ytimg.com/vi/_vo0yHPdYfY/maxresdefault.jpg)](https://www.youtube.com/watch?v=_vo0yHPdYfY)