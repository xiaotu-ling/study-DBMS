1.最开始从规范开始讲起，本章节以及后续章节都是讲==SQL==语句，本章节讲解的是SELECT语句。想要保证数据的==持久化==就要和数据库打交道。
***解释：DB（Database）相当于一个.docx文件，DBMS（Database Management System）相当于word这个软件，而SQL（Structured Query Language）是DBMS控制DB要用到的语言。***

2.SQL语言分为三大类：
==**DDL**==（Data Definition Language，数据定义语言）例如CREATE，DROP，ALTER，RENAME，TRUNCATE等等。
==**DML**==（Data Manipulation Language，数据操作语言）例如INSERT，DELETE，UPDATE，==***SELECT***==等等。
==**DCL**==（Data Control Language，数据控制语言）例如GRANT，REVOKE，COMMIT，ROLLBACK，SAVEPOINT等等。

3.SQL语言的规则与规范
规则是必须遵守，规范是建议遵守
==**规则：**==
USE dbtest2;
SELECT * FROM emp;
INSERT INTO emp VALUES(1002，'TOM');
 ①SQL可以写在一行或多行。为了提高可读性，各子句分行写，必要时使用缩进
 ②每条命令以 ==;== 或 ==\g== 或 ==\G== 结束
 ③关键字不能被缩写也不能被分行
 ④关于标点符号
   必须保证所有的()，单引号，双引号是成对出现的
   必须使用英文状态下的半角输入方式
   字符串型和日期时间类型
   



