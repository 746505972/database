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

SELECT dept_name
FROM instructor
group by dept_name
having AVG(salary) > 20000;
```
