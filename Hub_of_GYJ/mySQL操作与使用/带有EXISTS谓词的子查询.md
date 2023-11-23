1. EXISTS谓词  
	- 存在量词（反E）
	- 带有EXISTS谓词的子查询不返回任何数据，只产生逻辑<font color="#9bbb59">真值“true</font>”或逻辑<font color="#c0504d">假值“false”</font>。
		- 若内层查询结果<font color="#f79646">非空</font>，则外层的WHERE子句返回<font color="#f79646">真值</font>
		- 若内层查询结果<font color="#8064a2">为空</font>，则外层的WHERE子句返回<font color="#8064a2">假值</font>
	-   由EXISTS引出的子查询，其目标列表达式通常都用* ，因为带EXISTS的子查询只返回真值或假值，给出列名无实际意义
2. NOT EXISTS谓词  
	- 若内层查询结果非空，则外层的WHERE子句返回假值  
	- 若内层查询结果为空，则外层的WHERE子句返回真值   

```sql
SELECT Sname
FROM Student
WHERE EXISTS
      (SELECT *
       FROM SC
       WHERE Sno=Student.Sno AND Cno= ' 1 ')；
```