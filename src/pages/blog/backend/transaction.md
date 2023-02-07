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

Ví dụ giờ thằng `Bình` muốn gửi tiết kiệm **200k** thì phải đi qua ít nhất 3 bước sau: 

1. Kiểm tra tài khoản thằng **Bình** có >= 200k hay không
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