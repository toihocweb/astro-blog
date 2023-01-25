---
layout: ../../layouts/Layout.astro
title: Proxy trong javascript
description: Hiểu rõ về Proxy trong JS sẽ giúp bạn có thêm công cụ để xử lí object trong JS
date: 2023-01-25T08:25:04.381Z
thumbnail: https://i1.wp.com/blog.alexdevero.com/wp-content/uploads/2020/06/29-06-20-getting-started-with-javascript-proxy-object-blog.jpg?fit=1024%2C635&ssl=1
---
## P﻿ROXY trong Javascript

H﻿ỏi: proxy dùng để làm gì

T﻿rả lời: proxy giúp xử lí 1 object trong js

C﻿hẳng hạn chúng ta có object sau 

```javascript
const product = { 
    name: "Apple",
    price: 18
}

<p>{product.price} USD</p>
```

c﻿ó thể thấy, cứ mỗi lần muốn sử dụng **price** ta đều thêm hậu tố "**USD**" vào sau

g﻿iả sử giờ muốn thay đổi "**USD**" thành "VND" chúng ta phải tìm hết tất mọi file trong project,