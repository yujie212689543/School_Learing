---
date created: 2023-09-20 08:33
tags:
  - SELECT关键字
  - DISTINCT关键字
  - BETWEEN_AND
  - IN_NOTIN
  - WHERE关键字
  - 固定字符匹配_LIKE关键字
  - 通配字符匹配
  - 转换字符：ESCAPE
  - 升序降序_ORDER_BY
  - 聚集函数
---
### SQL语言的动词  
| SQL功能  | 动词                 |
| -------- | -------------------- |
| 数据查询 | SELECT               |
| 数据定义 | CREATE,DROP,ALTER    |
| 数据操控 | INSERT,UODATE,DELETE |
| 数据控制 | GRANT,REVOKE         | 

### SQL的数据定义语句   
| 操作对象 | 操作方式      |             |             |
| -------- |:------------- |:----------- |:-----------:|
|          | 创建          | 删除        |    修改     |
| 模式     | CREATE SCHEMA | DROP SCHEMA |             |
| 表       | CREATE TABLE  | DROP TABLE  | ALTER TABLE |
| 视图     | CREATE VIEW   | DROP VIEW   |             |
| 索引     | CREATE INDEX  | DROP INDEX  |             |

### 常用的查询条件   
| 查询条件             | 谓词                                       |
| -------------------- | ------------------------------------------ |
| 比较                 | =,>,<,>=,<=,!=,<>,!>,!<;NOT+上述比较运算符 |
| 确定范围             | BETWEEN AND,NOT BETWEEN AND                |
| 确定集合             | IN,NOT IN                                  |
| 字符匹配             | LIKE,NOT LIKE                              |
| 空值                 | IS NULL,IS NOT NULL                        |
| 多重条件（逻辑运算） | AND,OR,NOT                                 | 





---
# 表的定义、删除与修改  
## 一、定义基本表  
（详细见[[创建教务系统]]）   

## 二、数据查询  
*语句格式*
```
SELECT [ALL|DISTINCT] <目标列表达式>[，<目标列表达式>] …
FROM <表名或视图名>[， <表名或视图名> ] …
[ WHERE <条件表达式> ]
[ GROUP BY <列名1> [ HAVING <条件表达式> ] ]
[ ORDER BY <列名2> [ ASC|DESC ] ]；
```
### 查询指定(全体)列  
**例题1 查询全体学生的学号和姓名**  
```sql
SELECT Sno，Sname
FROM Student；
```
**例题2 查询全体学生的详细记录**
```sql
SELECT  Sno，Sname，Ssex，Sage，Sdept
FROM Student；
 或
SELECT  *
FROM Student；
```
<mark style="background: #BBFABBA6;">***注意*** </mark>
* SELECT子句的<<mark style="background: #FFB86CA6;">目标列</mark>表达式>可以为： #SELECT关键字
	* 算数表达式
	* 字符串常量
	* 函数
	* 列别名    

**例题4 查全体学生的姓名及其出生年份**  
```sql
SELECT Sname，2013-Sage    /*假定当年的年份为2013年*/
FROM Student；
```
*输出结果*  

| Sname  | 2013-Sage |
| ------ | --------- |
| 韩立   | 1984      |
| 历飞羽 | 1985      |
**例题5 使用列别名改变查询结果的列标题**  
```sql
SELECT Sname NAME，'Year of Birth: ’  BIRTH，2013-Sage  BIRTHDAY，LOWER(Sdept)  DEPARTMENT
FROM Student；
```
*输出结果*  

| NAME   | BIRTH          | BIRTHDAY | DEPARTMENT |
| ------ | -------------- | -------- | ---------- |
| 韩立   | Year of Birth: | 1984     | cs         |
| 历飞羽 | Year of Birth: | 1985     | is         |
| 董宣儿 | Year of Birth: | 1986     | ma           |

=================================================================
### 选择表中的若干元组  
 #DISTINCT关键字
	指定DISTINCT关键字，<font color="#f79646">去掉表中重复的行</font>  
```sql
SELECT DISTINCT Sno
FROM SC；
```
*结果*  

| Sno       |
| --------- |
| 200215122 |
| 200215122          |

---------------------

**例题6 查询考试成绩有不及格的学生的学号** #WHERE关键字
```sql
SELECT DISTINCT Sno
FROM  SC
WHERE Grade<60；
```
-------

**例题7 查询年龄在20~23岁（包括20岁和23岁）之间的学生的姓名、系别和年龄**  #BETWEEN_AND   
```sql
SELECT Sname，Sdept，Sage
FROM Student
WHERE Sage BETWEEN 20 AND 23
```
---------------

**例题8 查询信息系（IS）、数学系（MA）和计算机科学系（CS）学生的姓名和性别。** #IN_NOTIN   
```sql
SELECT Sname，Ssex
FROM Student
WHERE Sdept IN ( 'IS'，'MA'，'CS' );
```
```sql
SELECT Sname，Ssex
FROM Student
WHERE Sdept NOT IN ( 'IS'，'MA'，'CS' );
```  
--------------
## 字符匹配  
### 1.匹配串为固定字符串
**例题9 查询学号为200215121的学生的详细情况**  #固定字符匹配_LIKE关键字
```sql
SELECT *   
FROM  Student 
WHERE  Sno LIKE ‘200215121'；
等价于：
SELECT  *
FROM  Student
WHERE Sno = ' 200215121 '；
```
------------
### 2.匹配串为含通配符的字符串  #
**例题10 查询所有姓刘学生的姓名、学号和性别**  #通配字符匹配
```sql
SELECT Sname，Sno，Ssex
FROM Student
WHERE Sname LIKE ‘刘%’；
```
**例题11 查询名字中第2个字为"阳"字的学生的姓名和学号**  
```sql
SELECT Sname，Sno
FROM Student
WHERE Sname LIKE ‘__ 阳%’；
```
------------
### 3.使用换码字符将通配符转义为普通字符  
**例题12 查询以"DB_"开头，且倒数第3个字符为 i的课程的详细情况**  #转换字符：ESCAPE
```sql
SELECT  *
FROM Course
WHERE Cname LIKE 'DB\_%i_ _' ESCAPE'\‘；
```
***<mark style="background: #ABF7F7A6;">ESCAPE '＼' 表示“ ＼” 为换码字符</mark>***  

-------------
## ORDER BY子句   
* ORDER BY子句
	* 可以按一个或多个属性列排序
	* <font color="#f79646">升序</font>：ASC；<font color="#c3d69b">降序</font>：DESC；<span style="background:#d2cbff">缺省值为升序</span>  
- 当排序列含<span style="background:#d3f8b6">空值</span>时
	- ASC：排序列为空值的元组<font color="#c0504d">最后</font>显示
	- DESC：排序列为空值的元组<font color="#548dd4">最先</font>显示   

**例题13 查询全体学生情况，查询结果按所在系的系号升序排列，同一系中的学生按年龄降序排列**  
#升序降序_ORDER_BY
```sql
SELECT  *
FROM  Student
ORDER BY Sdept，Sage DESC
```   
----------------------
## 聚集函数  
#聚集函数
- 计数
	- COUNT（[DISTINCT|ALL] *）
	- COUNT（[DISTINCT|ALL] <列名>）
- 计算总和
	- SUM（[DISTINCT|ALL] <列名>）
- 计算平均值
	- AVG（[DISTINCT|ALL] <列名>）
- 最大值最小值
	- MAX（[DISTINCT|ALL] <列名>）
	- MIN（[DISTINCT|ALL] <列名>）  

**例题14 查询选修了课程的学生人数**
```sql
SELECT COUNT(DISTINCT Sno)
FROM SC；
```

**例题15 计算1号课程的学生平均成绩**
```sql
SELECT AVG(Grade)
FROM SC
WHERE Cno= ' 1 '；
```

**例题16 查询学生200215012选修课程的总学分数**  
```sql
SELECT SUM(Ccredit)
FROM SC，Course
WHER Sno='200215012' AND SC.Cno=Course.Cno;
```  

---------------
## GROUP BY子句   

