# 方乾 42233017

## 题目一

![image](https://github.com/user-attachments/assets/43edff7a-4292-401c-80db-4a6a2f0bddfe)

```sql
CREATE TABLE products (
    product_no VARCHAR(100),
    name VARCHAR(100),
    price numeric);
```
```postgresql
postgres=# \copy products from 'F:\\我的\\大学\\大三\\数据库原理\\product_data.csv' WITH (FORMAT csv, DELIMITER ',')
COPY 100000
```
![image](https://github.com/user-attachments/assets/b3fb4df6-3b4b-4dfd-afea-f4cd8b5a9250)

## 题目二

```sql
--2.1
insert into products(product_no, name)
values (666,'cake');
--2.2
insert into products(product_no, name,price)
values (100001,'kobe',240),
(114514,'yu',800),
(191919,'be',810);
--2.3
update products
set price = price * 0.8;
--2.4
update products
set price = case
    when price > 100 then price * 1.02
    else price * 1.04
    end;
--2.5
delete from products
where name like '%cake%';
--2.6
delete from products
where price > (select avg(price) from products);
```

## 题目三
```sql
Delete on product  (cost=0.00..834.47 rows=0 width=0) (actual time=573.782..573.783 rows=0 loops=1)
  ->  Seq Scan on product  (cost=0.00..834.47 rows=19747 width=6) (actual time=0.013..13.539 rows=100000 loops=1)
Planning Time: 0.111 ms
Execution Time: 573.848 ms
```
```sql
postgres.public> TRUNCATE product
[2025-04-10 22:19:34] 在 17 ms 内完成
```
| 操作         | DELETE                          | TRUNCATE                      |
|--------------|---------------------------------|-------------------------------|
| 数据删除     | 逐行标记为"死元组"              | 直接删除整个数据文件          |
| 空间回收     | 需要 `VACUUM` 或 `AUTOVACUUM `      | 立即释放给操作系统            |
| WAL日志      | 记录每行删除                    | 仅记录元数据变更              |
| 触发器       | 触发 `BEFORE/AFTER DELETE` 触发器 | 不触发任何行级触发器          |
| 索引         | 需要更新所有索引                | 直接清空索引文件              |
