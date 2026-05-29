一.**最开始从规范开始讲起，本章节以及后续章节都是讲==SQL==语句，本章节讲解的是SELECT语句。想要保证数据的==持久化==就要和数据库打交道。
***解释：DB（Database）相当于一个.docx文件，DBMS（Database Management System）相当于word这个软件，而SQL（Structured Query Language）是DBMS控制DB要用到的语言。***

二.SQL语言分为三大类：
    1.==**DDL**==（Data Definition Language，数据定义语言）例如CREATE，DROP，ALTER，RENAME，TRUNCATE等等。
    2.==**DML**==（Data Manipulation Language，数据操作语言）例如INSERT，DELETE，UPDATE，==***SELECT***==等等。
    3.==**DCL**==（Data Control Language，数据控制语言）例如GRANT，REVOKE，COMMIT，ROLLBACK，SAVEPOINT等等。

三.SQL语言的规则与规范(规则是必须遵守，规范是建议遵守)
 1.==**规则：**==
    ①SQL可以写在一行或多行。为了提高可读性，各子句分行写，必要时使用缩进
    ②每条命令以 ==;== 或 ==\g== 或 ==\G== 结束
    ③关键字不能被缩写也不能被分行
    ④关于标点符号
        必须保证所有的( )，单引号，双引号是==成对出现==的
        必须使用==英文状态==下的半角输入方式
        ==字符串型==和==日期时间类型==的数据可以使用==单引号==(' ')表示
        列的==别名==，尽量==使用双引号==(" ")，而且==不建议省略as==
    两个==例句：==
    ***NSERT INTO emp
    VALUES(1003，'TOM');
    SELECT employee_id ==''emp_id''==,last_name ==''lname''==,department_id 
    FROM employees;

 2.==大小写规范：==
    ①==windows==下SQL对大小写==不敏感==,==linux==下对大小写==敏感==(数据库名，表名，表的别名，变量名严格区分；关键字，函数名，列名，列的别名是忽略大小写的。)
    ②推荐采用统一的书写规范(*数据库名，表名，表的别名，字段名也就是列名，字段别名等都小写；SQL关键字，函数名，绑定变量等都大写。*)
 
 3.==注释==可以使用以下注释结构：
    ①使用 ==*#*== 后直接跟注释内容，是单行注释。
    ②/ *  * / 是==多行注释==
    ③-- 注释文字 --也是单行注释，注意要--==加空格==

 4.命名规则
    ①数据库，表名不得超过30个字符，变量名限制为29个
    ②必须只包含A-Z，a-z，0-9，_共63个字符
    ③数据库名，表名，字段名等对象名字中间不要包含空格
    ④同一个MySQL软件中，数据库不能同名；同一个库中，表不能重名；同一个表中，字段不能重名
     ⑤必须==保证自己的字段没有和保留字，数据库系统或常用方法冲突==，若要坚持使用，请在SQL语句中使用着重号引起来
    ⑥保持==字段名和类型的一致性==，在命名字段并为其指定数据类型的时候一定要保证一致性。假如数据类型在一个表里是整数，在另一个表里可别是字符型了。

四.SELECT查询(要先有表，数据，才能进行查询)
    1.导入现有的数据表，表的数据：==source 文件的全路径==(这个要使用命令行，用cmd面板) 或 ==基于具体的图形化界面的工具导入数据==
    2.基本的SELECT语句：
         ①==SELECT... ...== ：**SELECT 1；**，**SELECT 9/2；**
         ②==SELECT   字段   FROM  表名==; 例如**SELECT * FROM employees;**  * 是代表所有列，也就是所有字段。
    3.列的别名
         SELECT employee_id,last_name,department_id FROM employees;
         ![[屏幕截图 2026-05-29 161442 1.png|160]]
         SELECT employee_id ==emp_id==,last_name ==AS lname==,department_id FROM employees;
         (两个黄色高亮意思一样都是别名的意思，AS也就是alias(别名)，可以省略)
         ![[屏幕截图 2026-05-29 161835.png|158]]
         或者用双引号引起来,==不要使用单引号==和上述效果一致!
         SELECT employee_id ==''emp_id''==,last_name ==''lname''==,department_id FROM employees;
    4.去除重复行
        ①查询员工表里有多少个部门：
        SELECT department_id
        FROM employees;    
            ![[屏幕截图 2026-05-29 175337.png]]
        可以看见有很多重复的部门编号输出
        ②使用DISTINCT去重：
        SELECT ==DISTINCT== department_id
        FROM employees;
         ![[屏幕截图 2026-05-29 175517.png]]
     5.空值参与运算:NULL
        ==控制不等同于0==
        SELECT employee_id,salary "月工资",salary * (1 + commission_pct) * 12 "年工资" 
        FROM emloyees;
        ![[屏幕截图 2026-05-29 180504.png|160]]
        ==空值做运算后还是空值==
        SELECT employee_id,salary "月工资",salary * (1 +  ==IFNULL(commission_pct,0)==) * 12 "年工资" 
        FROM emloyees;
        引入INFNULL来，如果是NULL，就拿0来替换。
    6.着重号: 
        SELECT * FROM ==着重号==order==着重号==;
        当表明或字段与关键字一样是要加着重号
    7.查询常数:
        SELECT =='尚硅谷'==，employee_id,last_name
        FROM employees;
         ![[屏幕截图 2026-05-29 181503.png|278]]
        在最前面一列加上了==常数== 尚硅谷。
        SELECT =='尚硅谷'==,==123==,employee_id,last_name
        FROM employees;
        这样就在上面表里又加了一列123.
    8.显示表结构:
        ==DESCRIBE== employees;
        ![[屏幕截图 2026-05-29 181915.png|345]]
        显示了表中==字段的详细信息==，用DESC也行，DECS employees;
        
        
     
     
     



