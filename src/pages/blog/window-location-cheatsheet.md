---
layout: ../../layouts/Blog.astro
title: window.location Cheatsheet
description: Tìm hiểu về window.location để đi phỏng vấn 10đ
date: 2023-01-25T13:17:28.023Z
thumbnail: https://i.ibb.co/MGc76hw/Capture.jpg
---
## window.location Cheatsheet

> `https://www.samanthaming.com/tidbits/?filter=JS#2`

```javascript
window.location.origin   → 'https://www.samanthaming.com'
               .protocol → 'https:'
               .host     → 'www.samanthaming.com'
               .hostname → 'www.samanthaming.com'
               .port     → ''
               .pathname → '/tidbits/'
               .search   → '?filter=JS'
               .hash     → '#2'
               .href     → 'https://www.samanthaming.com/tidbits/?filter=JS#2'
```

### S﻿ự khác nhau giữa *host* và *hostname*

c﻿húng ta sẽ thấy sự khác nhau rõ rệt khi có PORT

#### **c﻿ó port**

> `https://www.samanthaming.com:8080`

```javascript
window.location.host; // 'www.samanthaming.com:8080'
window.location.hostname; // 'www.samanthaming.com'

window.location.port; // '8080'
```

#### **không có port**

> **`https://www.samanthaming.com/`**

```javascript
window.location.host; // 'www.samanthaming.com'
window.location.hostname; // 'www.samanthaming.com'

window.location.port; // ''
```