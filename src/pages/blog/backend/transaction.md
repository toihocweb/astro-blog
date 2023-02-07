---
layout: ../../../layouts/Blog.astro
title: Transaction
description: Tìm hiểu về transaction nói chung và transaction trong MySQL nói riêng
date: 2023-02-07T05:51:46.306Z
thumbnail: /assets/transaction-640.jpg
---
## Transaction

![](/assets/transaction-640.jpg)

### Transaction là gì?

A *transaction* is a group of SQL statements that are treated atomically, as a single unit of work. 

Hiểu đơn giản là "Transition là nhóm các câu lệnh SQL để thực hiện một công việc nào đó". 

Giả sử **Bình** gửi tiền trong 1 ngân hàng nọ, và database gồm 2 table sau `checking` và `saving`(table lưu tiền tiết kiệm)

Ví dụ giờ  `Bình` muốn gửi tiết kiệm **200k** thì phải đi qua ít nhất 3 bước sau: 

1. Kiểm tra tài khoản **Bình** có >= 200k hay không
2. Trừ 200k trong tài khoản gốc (được lưu trong table `checking`)
3. Cộng 200k vào tài khoản tiết kiệm (được lưu trong table `saving`)

Toàn bộ quá trình trên sẽ được bọc trong 1 transaction, và 1 transaction được gọi là thành công khi không bị lỗi ở bất cứ step nào,

khi đó ta có thể định nghĩa 1 transaction đơn giản như sau: 🥳

```sql
1  START  TRANSACTION;
2  SELECT balance FROM checking WHERE customer_id = 10233276;
3  UPDATE checking SET balance = balance - 200.00 WHERE customer_id = 10233276;
4  UPDATE savings SET balance = balance + 200.00 WHERE customer_id = 10233276;
5  COMMIT;
```

\
Chuyện gì xảy ra nếu database `saving` bị crash ở bước số 4 hoặc có một ai đó xoá cmn account của **Bình** ở giữa bước 3 và 4, rất nhiều thứ có thể xảy ra phải không nào...

### ACID - tiêu chuẩn của 1 transaction

**Atomicity (A):** một transaction sẽ thực hiện chỉ một unit of work, nghĩa là thực hiện 1 logic nào đó, ví dụ trên là logic về chuyển tiền, trừ tiền của Bình ở table `checking` và cộng vào table `saving` **,** đảm bảo một transaction chỉ có 2 trạng thái

1. thành công hay còn gọi là **committed** - (tất cả các bước đều không có lỗi)
2. thất bại - (chỉ 1 lỗi phát sinh)

Khi **thất bại**, database sẽ lấy lại gía trị ở trước đó, tất cả thay đổi sẽ được **roll back**

**Consistency (C):** database sẽ luôn chuyển từ trạng thái nhất quán này, sang trạng thái nhất quán khác. ở ví dụ trên có nghĩa là nếu như có lỗi ở step 3 và step 4, thì sẽ không có chuyện tài khoản của **Bình** sẽ bị trừ 200$ mà tk trong `saving` lại không được cộn. Nếu 1 transaction không được committed, thì tất cả cả thay đổi trong trong transaction sẽ không ảnh hưởng đến database, (sẽ không trừ 200$ trong table `checking`)