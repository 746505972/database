# 方乾 42233017（有很多图片）

## 题目一

![image](https://github.com/user-attachments/assets/8e307798-ba48-4492-b7d4-3dff25585cb1)

![image](https://github.com/user-attachments/assets/00a53773-2532-431e-9f80-2290564c40b3)

由于没有'History'科目的老师，`S.dept_name = 'History'`为False，导致返回为空，而不是所有老师。

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

![image](https://github.com/user-attachments/assets/578fc77b-adcc-4605-8744-6189bc05bde6)

![image](https://github.com/user-attachments/assets/bc7ba14a-8029-4947-bfb9-93a054ea751a)

![image](https://github.com/user-attachments/assets/1d9d5c35-0007-4667-aa9a-d326808a3028)
