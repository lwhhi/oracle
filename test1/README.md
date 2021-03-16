







# 实验1：SQL语句的执行计划分析与优化指导





#### 学号：201810414213 	班级：软工二班 	姓名：刘炜浩

## 实验目的

分析SQL执行计划，执行SQL语句的优化指导。理解分析SQL语句的执行计划的重要作用。

## 实验内容

- 对Oracle12c中的HR人力资源管理系统中的表进行查询与分析。

  1.连接上实验需要的Oracle地址：202.115.82.8 

  ​		用户名：system ， 密码123， 数据库名称：pdborcl，端口号：1521

  ![image-20210308143349137](D:/大学学习 文档/大三/大三下册/oracle/实验/参考/experience1-1.png)

运行教材的脚本

- 首先运行和分析教材中的样例：本训练任务目的是查询两个部门('IT'和'Sales')的部门总人数和平均工资，以下两个查询的结果是一样的。但效率不相同。

查询一：

![img](file:///C:\Users\76302\AppData\Local\Temp\ksohtml19060\wps1.jpg)



查询结果一：

![img](file:///C:\Users\76302\AppData\Local\Temp\ksohtml19060\wps2.jpg)

查询二：

![img](file:///C:\Users\76302\AppData\Local\Temp\ksohtml19060\wps3.jpg)

查询结果二：

![img](file:///C:\Users\76302\AppData\Local\Temp\ksohtml19060\wps4.jpg)

## 分析

在运行两个语句中，通过对比对CPU以及内存的占比发现：语句1的占有率要低于语句2的占有率，所以语句一的占有率更快

由对比可发现 查询语句1的CPU占用率要低于查询语句2，故查询语句1执行速度快些。并且耗时多的都在进行函数运行的时候。

- 设计自己的查询语句，并作相应的分析，查询语句不能太简单。

自定义查询：

set autotrace on

SELECT d.department_name,count(e.job_id)as "部门总人数",
sum(e.salary)as "总工资"
FROM hr.departments d,hr.employees e
WHERE d.department_id = e.department_id
GROUP BY d.department_name
HAVING d.department_name in ('IT','Sales');

自定义查询结果:

![image-20210316221407799](C:\Users\76302\AppData\Roaming\Typora\typora-user-images\image-20210316221407799.png)

## 分析

算法越优秀，运行的时间越短，执行效率更高

## 实验总结



通过这次试验，我对oracle有了初步的认识，也对也以前的sql语句有了一定的回顾，在这次试验中我学会了如何用SQL developer进行远程连接数据库，以及运行查询脚本。更重要的是学会了分析程序之间的不足与优点，希望在接下里的学习里，自己能再接再厉，努力向前。

