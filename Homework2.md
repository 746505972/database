# **方乾 42233017**
## **题目一**

```SQL
CREATE TABLE users  
  (name varchar(20) primary key,  
  pswd varchar(20),  
  gender char(1));
```

## **题目二**

```SQL
SELECT course_id, title, credits
FROM course
WHERE dept_name = '计算机' AND credits >= 3
ORDER BY credits ASC;
```

```SQL
SELECT DISTINCT takes.ID
FROM takes
JOIN teaches ON takes.course_id = teaches.course_id
              AND takes.sec_id = teaches.sec_id
              AND takes.semester = teaches.semester
              AND takes.year = teaches.year
JOIN instructor ON teaches.ID = instructor.ID
WHERE instructor.name = '图灵';
```

## **题目三**

查询所有工资高于`会计`学院至少一名教师的教师`姓名`，并排除重复姓名。
