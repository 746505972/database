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
