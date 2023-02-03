---
layout: ../../../layouts/Blog.astro
title: Image Loading [part 2]
description: load hình ảnh dựa vào viewport, sử dụng intersection
date: 2023-02-03T03:58:40.901Z
thumbnail: /assets/1-1477901-1450843193145.webp
---
## **Load hình sử dụng intersection**

giả sử giờ web chúng ta có 100 tấm hình, nếu không có gì đặc biệt thì có phải khi user vào web, phải đợi tải hết 100 tấm hình này về thì mới sử dụng web mượt mà được phải khum nào.

Hmmm, không có gì để nói nếu các tấm hình đó nhẹ, và mạng wifi nhà user đủ nhanh để tải về, nhưng thường thì đời không như mơ, 

để giải quyết vấn đề đó thì giang hồ hay sử dụng lazy load, có 2 kiểu phổ biến là

1. Load số lượng hình cụ thể, ví dụ 1 lần load của tui sẽ là 10 hình, giờ user click vào “load more”, hay là scroll xuống thì load thêm 10 hình nữa…
2. Load số lượng hình dựa vào viewport thường áp dụng cho sự kiện scroll, nghĩa là user scroll tới đâu, thì mới load hình ở phần đó

***Lưu ý: load hình đc để cập ở trên chính là việc tải hình + show hình nha,*** 

Kiểu 1 ai cũng biết làm nên thôi mình qua kiểu 2 cho nó lạ lạ xíu nhé 

### Intersection

Intersection trong js cho phép bạn quan sát các DOM, và DOM nào trong viewport thì sẽ thực thi một hành động nào \
\
HTML

```html
<style>
   body {
    display: flex;
    flex-wrap: wrap;
    margin: 0;
    padding: 0;
   }
   img {
    width: 200px;
    height: 200px;
   }
</style>
<body>
   <img data-src="https://picsum.photos/200/301" alt="">
   <img data-src="https://picsum.photos/200/302" alt="">
   <img data-src="https://picsum.photos/200/303" alt="">
   <img data-src="https://picsum.photos/200/304" alt="">
   <img data-src="https://picsum.photos/200/305" alt="">
   <img data-src="https://picsum.photos/200/306" alt="">
   <img data-src="https://picsum.photos/200/307" alt="">
   <img data-src="https://picsum.photos/200/308" alt="">
   <img data-src="https://picsum.photos/200/309" alt="">
   <img data-src="https://picsum.photos/200/310" alt="">
   <img data-src="https://picsum.photos/200/311" alt="">
   <img data-src="https://picsum.photos/200/312" alt="">
   <img data-src="https://picsum.photos/200/313" alt="">
</body>
```

\
để ý là, link hình ảnh được đặt vào trong dataset là `data-src` nhé, không phải trong `src` nha, lí do là nếu để trong `src` thì trình duyệt sẽ download toàn bộ về, v thì không còn ý nghĩa gì nữa

Add thêm đoạn js sau

```javascript
const images = document.querySelectorAll('img'); // các DOM cần quan sát, ở đây ta lấy tất cả hình ảnh

const options = {
    root: null, // browser window 
    rootMargin: '0px', // root margin top, left, right, bottom = 0
    threshold: 0.5 // kéo xuống >50% thì hình bắt đầu load
}

// định nghĩa observer 
const observer = new IntersectionObserver((entries, observer) => {
   entries.forEach((entry, idx) => {
        // xác định xem target nằm trong hay ngoài viewport, 
        if(entry.isIntersecting) {
            const image = entry.target;
          
            // khúc này là lấy cái giá trị trong data-src và set vào src nè
            image.src = image.dataset.src;
          
            // hình nào load rồi thì mình k theo dõi nữa
            observer.unobserve(image);
        }
    })
}, options);

// quan sát tất cả các <img> DOM
images.forEach(image => {
    observer.observe(image);
})
```

**giải thích**

`root`: là DOM mà bạn muốn quan sát, null nghĩa là đang quan sát browser window

`rootMargin`: khoảng margin xung quanh root element(định nghĩa ở trên) dùng để xác định xem element(img) có đang intersecting hay không

`threshold`: có giá trị từ 0.0 đến 1.0 tương ứng với 0% đến 100%, là giá trị phần trăm của target(img) ở trong viewport thì target đó sẽ đc set intersecting, giá trị có thể là array \[0.5,0.8] tương ứng 50%, 80%, callback function sẽ chạy khi viewport đạt đến giá trị threshhold này

**`intersecting`**: là trạng thái mà element nằm trong hay ngoài viewport hoặc root element

Demo: [Click here](<https://player.vimeo.com/video/795469857?h=1a274dbd7e&badge=0&autopause=0&player_id=0&app_id=58479" frameborder="0" allow="autoplay; fullscreen; picture-in-picture>)