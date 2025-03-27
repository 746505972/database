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
