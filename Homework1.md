方乾 42233017
---
**题目一**

>GitHub不能正确显示  
>$\Pi_{branch\_name}(\sigma_{branch\_city="成都"}(branch))$  
>$\Pi_{ID}({\sigma_{branch\_name="杨柳"}(loan) }⨝ borrower)$

![image](https://github.com/user-attachments/assets/c8bcfb8d-2a51-4d35-94e5-7546750b0132)

**题目二**

1.用户在前端填入用户名（input_name）、密码（input_pswd）  

2.后端验证与数据库中存放的用户名（name）和密码（pswd）是否匹配，即

>$\sigma_{name=input\_name∧pswd=input\_pswd}(users)$

![image](https://github.com/user-attachments/assets/71d72924-ab34-4f4b-a722-ff5000f8dea7)

3.将判断结果（是否为空集）返回前端，若为空，登录失败；若不为空，登录成功
