# 方乾 42233017

## 题目一

```sql
postgres.public> SELECT dept_name, min(salary)
                 FROM instructor
[2025-03-27 20:03:39] [42803] 错误: 字段 "instructor.dept_name" 必须出现在 GROUP BY 子句中或者在聚合函数中使用
[2025-03-27 20:03:39] 位置：8
postgres.public> SELECT dept_name, min(salary)
                 FROM instructor
                 GROUP BY dept_name
                 HAVING name LIKE '%at%'
[2025-03-27 20:04:14] [42803] 错误: 字段 "instructor.name" 必须出现在 GROUP BY 子句中或者在聚合函数中使用
[2025-03-27 20:04:14] 位置：76
postgres.public> SELECT dept_name
                 FROM instructor
                 WHERE AVG(salary) > 20000
[2025-03-27 20:05:24] [42803] 错误: 聚合函数不允许出现在WHERE中
[2025-03-27 20:05:24] 位置：42
```

都不合法。

第一题select了dept_name, min(salary)，dept_name应出现在`GROUP BY`里。

第二题GROUP BY中没有`name`，但却在`HAVING`中出现了。

第三题`WHERE`是按行处理的，但`AVG`需要遍历所有行。

应为
```sql
SELECT dept_name, min(salary)
FROM instructor
group by dept_name ;

SELECT dept_name, min(salary)
FROM instructor
where name LIKE '%at%'
GROUP BY dept_name;

SELECT dept_name,AVG(salary)
FROM instructor
group by dept_name
having AVG(salary) > 20000;
```

## 题目二
### 1
```sql
select name
from instructor
where salary=(select max(salary) as a from instructor);
```
### 2
```sql
SELECT name FROM instructor
where salary=(select max(salary) from instructor);

SELECT name FROM instructor
WHERE salary IN (SELECT MAX(salary) FROM instructor);

SELECT name
FROM (
    SELECT name, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
    FROM instructor
) ranked
WHERE rnk = 1;

SELECT i.name
FROM instructor i
JOIN (SELECT MAX(salary) AS max_salary FROM instructor) max_s
ON i.salary = max_s.max_salary;
```
### 3

1.检查`1`是否在集合`(1)`中

2.这里的`(1)`等价于数字`1`，检查`1`是否等于`1`

3.检查元组`(1,2)`是否等于元组`(1,2)`

4.这里的`(1)`等价于数字`1`，检查`1`是否在集合`(1,2)`中
