---
layout: ../../../layouts/Blog.astro
title: Image Loading [part 1]
description: kĩ thuật load ảnh dựa vào screen
date: 2023-02-01T04:32:47.290Z
thumbnail: /assets/1-1477901-1450843193145.webp
---
## **huật load hình ảnh dựa vào screen**

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

**ãy xem chúng ta có những solution nào phổ biến nhé**

##### Solution 1: viết đoạn script để detect xem kích thước hiện tại là bao nhiêu, sau đó load hình tương ứng

```javascript
// Define the different image sources for each screen size
const smallScreenImg = 'https://picsum.photos/200/200';
const mediumScreenImg = 'https://picsum.photos/300/300';
const largeScreenImg = 'https://picsum.photos/400/400';

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