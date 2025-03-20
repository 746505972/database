# 方乾 42233017

## 题目一

![image](https://github.com/user-attachments/assets/8e307798-ba48-4492-b7d4-3dff25585cb1)

![image](https://github.com/user-attachments/assets/00a53773-2532-431e-9f80-2290564c40b3)

没有'History'科目的老师

## 题目二

```sql
select name from instructor
where name like 'S%';
```
```sql
select name from instructor
where LEFT(name, 1) = 'S';
```
```sql
select name from instructor
where name similar to 'S%';
```
```sql
select name from instructor
where name ~ '^S';
```

## 题目三

