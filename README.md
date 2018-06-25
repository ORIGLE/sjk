# sjk
数据库
#/*创建表*/
#CREATE TABLE student(sid INT,sname VARCHAR(10),age INT);
#/*改变表名*/
#ALTER TABLE student RENAME TO stu;
#/*查询表结构*/
#DESC student;
#/*删除表*/
#DROP TABLE stu;
#/*增加字段*/
#ALTER TABLE student ADD COLUMN phone VARCHAR(30);
#/*改变字段名称/数据类型*/
#ALTER TABLE student CHANGE COLUMN phone ph VARCHAR(30);
#ALTER TABLE student MODIFY ph int;
#/*删除字段*/
#ALTER TABLE student DROP ph;
#ALTER TABLE student DROP clas;
#/*增加一条数据*/
#INSERT INTO student VALUES(1,'好啊好啊',22);
#INSERT INTO student(sid,sname)VALUES(2,'猪猪');
#SELECT*FROM student;
#/*改变表数据*/
#UPDATE student set age=18 ;
#UPDATE student SET age=22 WHERE sid=1;
#/*查询所有表数据*/
#SELECT * FROM student;
#/*查询指定字段数据*/
#SELECT sname FROM student;
#/*查询出来的字段名字可以改变*/
#SELECT sname '名字',age '年龄'  FROM student;
#/*清空表数据*/
#DELETE FROM student;
#DELETE FROM student WHERE sid=2;
#/* 约束*/
# /* 主键*/
#	   /* 非空*/
#		 ALTER TABLE student MODIFY sname VARCHAR(30) NOT NULL;
#		 ALTER TABLE student MODIFY sname VARCHAR(30);
#		   /* 默认值*/
#			 ALTER TABLE student MODIFY age INT DEFAULT 20;
#			   /*外键
#				 一个表里面的外键必须是另一个表的主键
#				 */
#				 ALTER TABLE student ADD FOREIGN KEY(cla)REFERENCES clas(cid);
#				 /*自己定义外键名*/
#				 ALTER TABLE student ADD CONSTRAINT sc FOREIGN KEY(cla)REFERENCES clas(cid);

#				 /*删除外键  student_ibfk_1是约束别名 */
#				 ALTER TABLE student DROP FOREIGN KEY student_ibfk_1;
#				 /*唯一*/
#				 /*添加唯一约束时需要注意约束名称
#				 删除时需要根据约束名称删除
#				 当没有自定义约束名称时系统会自动生成一个
#				 可以通过show create table 表名;进行查询
#				 */
				 
#				ALTER TABLE student add UNIQUE(sname); 
#				ALTER TABLE student DROP INDEX sname;
				
#ALTER TABLE student ADD PRIMARY KEY(sid);	
#ALTER TABLE student DROP PRIMARY KEY;
#DESC student;
#INSERT INTO student(sid,sname)VALUES(2,'张三');
#SELECT * FROM student;
#/*删除sid=2和3的行*/
#DELETE FROM student WHERE sid=2;

#SHOW CREATE TABLE student;

#CREATE TABLE `student` (
#  `sid` int(11) NOT NULL default '0',
#  `sname` varchar(30) NOT NULL,
#  `age` int(11) default '20',
#  `cla` int(11) default NULL,
#  PRIMARY KEY  (`sid`),
#  KEY `cla` (`cla`),
#  CONSTRAINT `student_ibfk_1` FOREIGN KEY (`cla`) REFERENCES `clas` (`cid`)
#) ENGINE=InnoDB DEFAULT CHARSET=utf8
#/*自定义的外键名`sc`*/
#CREATE TABLE `student` (
 # `sid` int(11) NOT NULL default '0',
 # `sname` varchar(30) NOT NULL,
 # `age` int(11) default '20',
 # `cla` int(11) default NULL,
 # PRIMARY KEY  (`sid`),
 # KEY `sc` (`cla`),
 # CONSTRAINT `sc` FOREIGN KEY (`cla`) REFERENCES `clas` (`cid`)
#) ENGINE=InnoDB DEFAULT CHARSET=utf8

#/**/
#CREATE TABLE clas(cid INT PRIMARY KEY,canme VARCHAR(30));
#DROP TABLE clas;
#ALTER TABLE student ADD cla int;
#/*外键 student的cla 主键clas的cid*/
#ALTER TABLE student ADD FOREIGN KEY(cla)REFERENCES clas(cid);

#DESC clas;
#INSERT INTO clas VALUES (1,"1");
#INSERT INTO clas VALUES (2,"2");
#SELECT s.sid,s.sname,s.age,c.canme FROM student s JOIN clas c ON s.cla=c.cid; 