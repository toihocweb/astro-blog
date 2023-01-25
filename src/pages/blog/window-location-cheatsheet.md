---
layout: ../../layouts/Blog.astro
title: window.location Cheatsheet
description: Tìm hiểu về window.location để đi phỏng vấn 10đ
date: 2023-01-25T12:45:45.513Z
thumbnail: /assets/capture.jpg
---
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