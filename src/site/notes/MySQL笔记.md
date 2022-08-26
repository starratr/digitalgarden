---
{"dg-publish":true,"permalink":"/my-sql/","tags":["inbox,","gardenEntry"],"dgHomeLink":true,"dgPassFrontmatter":false}
---



## 目录

1. [[MySQL笔记#1 数据库的好处|为什么要学习数据库]]
2. [[MySQL笔记#2 数据库的相关概念|MySQL笔记#2 数据库的相关概念]]
	1. DBMS、DB、SQL
3. [[MySQL笔记#3 数据库存储数据的特点|数据库存储数据的特点]]
4. [[MySQL笔记#4 初始MySQL|初始MySQL]]
	1. [[MySQL笔记#4 1 2 MySQL的介绍和安装|MySQL产品的介绍]]
	2. MySQL产品的安装
	3. [[MySQL笔记#4 3 MySQL服务的启动和停止|MySQL服务的启动和停止]]
	4. [[MySQL笔记#4 4 MySQL服务的登录和退出|MySQL服务的登录和退出]]
	5. MySQL的[[MySQL笔记#4 5 1 MySQL的常见命令|常见命令]]和[[MySQL笔记#4 5 2 MySQL的语法规范|语法规范]]
5. [[MySQL笔记#5 DQL语言的学习|DQL语言的学习]]
	1. [[MySQL笔记#5 1 基础查询|基础查询]]
	2. [[MySQL笔记#5 2 条件查询|条件查询]]
	3. [[MySQL笔记#5 3 排序查询|排序查询]]
	4. [[MySQL笔记#5 4 常见函数|常见函数]]
		1. [[MySQL笔记#5 4 1 概念：|概念]]
		2. [[MySQL笔记#5 4 2 好处：|好处]]
		3. [[MySQL笔记#5 4 3 调用：|调用]]
		4. [[MySQL笔记#5 4 4 特点：|特点]]
		5. [[MySQL笔记#5 4 5 分类：|分类]]
			1. [[MySQL笔记#5 4 5 1 单行函数|单行函数]]
				1. [[MySQL笔记#5 4 5 1 1 字符函数|字符函数]]
				2. [[MySQL笔记#5 4 5 1 2 数学函数|数学函数]]
				3. [[MySQL笔记#5 4 5 1 3 日期函数|日期函数]]
				4. [[MySQL笔记#5 4 5 1 4 其它函数|补充的其它函数]]
				5. [[MySQL笔记#5 4 5 1 5 流程控制函数|补充的流程控制函数]]
			2. [[MySQL笔记#5 4 5 2 分组函数|分组函数]]
	5. [[MySQL笔记#5 5 分组查询|分组查询]]
	6. 连接查询
	7. 子查询
	8. 分页查询
	9. union联合查询
6. [[MySQL笔记#6 DML语言的学习|DML语言的学习]]
	1. 插入语句
	2. 修改语句
	3. 删除语句
7. [[MySQL笔记#7 DDL语言的学习|DDL语言的学习]]
	1. 库和表的管理
	2. 常见数据类型介绍
	3. 常见约束
8. [[MySQL笔记#8 TCL语言的学习|TCL语言的学习]]
	1. 事务和事务处理
9. 视图的讲解
10. 存储过程和函数
11. 流程控制结构

# 1. 数据库的好处
1. 持久化数据到本地
2. 可以实现结构化查询，方便管理

# 2. 数据库的相关概念

1. DB：数据库，保存一组有组织的数据的容器
2. DBMS：数据库管理系统，又称为数据库软件（产品），用于管理DB中的数据
3. SQL：结构化查询语言，用于和DBMS通信的语言

# 3. 数据库存储数据的特点
1. 将数据放到表中，表再放到库中
2. 一个数据库可以有多个表，每个表都有一个名字，用来标识自己。表名具有唯一性。
3. 表具有一些特性，这些特性定义了数据在表中如何储存，类似java中“类”的设计
4. 表由列组成，我们也称为字段。所有表都是由一个或多个列组成的，每一列类似于java中的“属性”
5. 表中的数据是按行存储的，每一行类似于java中的“对象”

# 4. 初始MySQL
## 4.1.2 MySQL的介绍和安装
## 4.3 MySQL服务的启动和停止
方式一：此电脑——右击——管理——服务和应用程序
方式二：通过管理员身份运行cmd
	net start 服务名（启动服务）
	net stop 服务名（停止服务）
## 4.4 MySQL服务的登录和退出
方式一：通过MySQL自带的客户端
只限于root用户
方式二：通过Windows自带的客户端

登录：mysql (-h( )主机名 -P( )端口名 )-u( )用户名 -p(密码)
退出：exit或ctrl+Z键
## 4.5.1 MySQL的常见命令
1. 查看当前所有的数据库
	```
	show databases;
	```
2. 打开指定的库
	```
	use 库名;
	```
3. 查看所处的库
	```
	select database();
	```
4. 查看当前库的所有表
	```
	show tables;
	```
4. 查看其它库的所有表
	```
	show tables from 库名;
	```
5. 创建表
	```
	create table 表名（
		列名 列类型
		列名 列类型
		……
	);
	```
6. 查看表结构
	```
	desc 表名;
	```
7. 查看服务器的版本
	方式一：登录到mysql客户端
	```
	select version();
	```
	方式二：没有登录到musql客户端
	```
	mysql --version;
	```
	或
	```
	mysql --V;
	```
##### 4.5.2 MySQL的语法规范
1. 不区分大小写，但建议关键字大写，表名、列名
2. 每条命令最好用分号结尾（`\g`也是可以结尾的）
3. 每条命令根据需要，可以进行缩进或换行，建议关键字单独一行
4. 注释
	1. 单行注释：`#注释文字`
	2. 单行注释：`-- 注释文字`
	3. 多行注释：`/*注释文字*/`

# 5. DQL语言的学习
Data Query Language 数据查询语言
涉及到的关键字是select
([案例](file:///D:\MySQL\myemployees.sql))
```
D:\MySQL\myemployees.sql
```

## 5.1 基础查询
1. 语法：
	```
	select 查询列表 from 表名
	```
	·
2. 特点：
	1. 查询列表可以是：表中的字段、常量值、表达式、函数
	2. 查询的结果是一个虚拟的表格（就是临时性的）
3. 细节：
	注意注意右上方显示的所在的库
	USE myemployeess;
	选中相应的语句之后按下F9去执行；按下F12去格式化（企业版或旗舰版）
4. 具体操作：
	1.  查询表中的单个字段
		```
		SELECT last_name FROM employees;
		```
		·
	2. 查询表中的多个字段
		```
		SELECT last_name,salary,email FROM employees;
		```
		·
	3. 查询表中的所有字段
		妈妈再也不用担心我的英语了，哪里不会点哪里（双击左边的筛选表格不容易出错，记得加上逗号）
		方式一：
		```
		SELECT `employee_id`,`first_name`,`last_name`,`email`,`phone_number`,`job_id`,`salary`,`commission_pct`,`manager_id`,`department_id`,`hiredate` 
		FROM employees;
		```
		方式二：	
		```
		SELECT * FROM employees;
		```
		反引号\`用来防止关键字和字段名重，如
		```
		SELECT NAME FROM stuinfo; 
		```
		虽然系统仍然是可以识别的，但是加上反单引号可以增加可读性
	4. 查询常量值
		```
		SELECT 100;
		SELECT 'john';
		```
		·
	5. 查询表达式
		```
		SELECT 100%98;
		```
		·
	6. 查询函数
		```
		SELECT  VERSION();
		```
		·
	7. 起别名
		1. 提高可读性，更容易让人理解意思
		2. 如果查询的字段有重名的情况，可以使用别名区分开来
			方式一：
			```
			SELECT 100%98 AS 结果;
			SELECT last_name AS 姓,first_name AS 名 FROM employees;
			```
			方式二:
			```
			SELECT last_name 姓,first_name 名 FROM employees;
			```
			案例：
			```
			SELECT salary AS "out put" FROM employees;
			```
			字段里面出现#号或者空格，会报错，需要加上双引号（推荐）（单引号其实也可以）
	8. 去重
		查询员工表中涉及到的所有的部门编号
		```
		SELECT DISTINCT department_id FROM employees;
		```
		·
	9. +号的作用
		java中的+号:
			1. 运算符
			2. 连接符
		mysql中的+号:
		仅仅只有运算符的功能
		`select 100+90;`		两个操作数都为数值型
		`select '123'+90;`	其中一方为字符型，试图将字符型数值转换为数值型
			如果转换成功，则继续做加法运算
		`select 'john'+90;`	如果转换失败，则将字符型数值转换为0
		`select null+10;`		只要其中一方为null，则结果肯定为null
		案例：将员工名和姓连接成一个字段，并显示为姓名
		```
		SELECT 
			lase_name+first_name AS 姓名
		FROM
			employees;
		```
		结果是0
		正确的做法：
		```
		SELECT CONCAT('a','b','c') AS 结果 ;
		SELECT 
			CONCAT(last_name,first_name) AS 姓名 
		FROM 
			employees;
		```
		·
5. 测试：
	![[Pasted image 20220115111312.png|Pasted image 20220115111312.png]] 
	答案：
	![[Pasted image 20220115111446.png|Pasted image 20220115111446.png]]
	![[Pasted image 20220115111603.png|Pasted image 20220115111603.png]]
	![[Pasted image 20220115111813.png|Pasted image 20220115111813.png]]
	补充：
	```
		SELECT
		IFNULL(`commission_pct`,0) AS 奖金率
	FROM
		employees;
	```
	·
## 5.2 条件查询
1. 语法：
	```
	select
		查询列表
	from
		表名
	where
		筛选条件;
	```
	它的执行顺序是：表名、筛选条件、查询列表
2. 分类：
	1. 按条件表达式进行筛选
		条件运算符：> < \= ==（注意不是\=\=）== !=(推荐写法是<>)
	2. 按逻辑表达式进行筛选
		作用：用于连接条件表达式
		逻辑运算符：&& || ！（推荐写法是 and or not）
	3. 模糊查询
		like
		between and
		in
		is null
3. 案例：
	1. 按条件表达式进行筛选
		1. 查询工资>12000的员工信息
			```
			SELECT
				*
			FROM
				employees
			WHERE
				salary>12000;

			```
			·
		2. 查询部门编号不等于90号的员工名和部门编号
			```
			SELECT
				last_name,
				department_id
			FROM
				employees 
			WHERE 
				department_id!=90;
			```
			·
	2. 按逻辑表达式进行筛选
		1. 查询工资在10000到20000之间的员工名、工资以及奖金
			```
			SELECT 
				last_name,
				salary,
				commission_pct
			FROM
				employees
			WHERE
				salary>=10000
			AND
				salary<=20000;
			```
			·
		2. 查询部门编号不是在90到110之间，或者工资高于15000的员工信息
			```
			SELECT 
				*
			FROM 
				employees
			WHERE
				department_id<90 OR department_id>110 OR salary>15000;
			```
			·
	3. 其它的查询
		1. like（模糊查询）
			1. 特点：
				一般和通配符搭配使用
				通配符
				1. % 任意多个字符，包括0个字符
				2. \_ 任意单个字符
			2. 查询员工名中包含字符a的员工信息
				```
				SELECT 
					*
				FROM 
					employees
				WHERE 
					last_name LIKE '%a%';
				```
				注意字符型一定要用单引号引起来
				另外查询结果不区分大小写
			3. 查询员工名中第三个字符为n，第五个字符为l的员工名和工资
				```
				SELECT
					last_name,
					salary
				FROM
					employees
				WHERE
					last_name LIKE '__n_l%';
				```
				.
			4. 查询员工名中第二个字符为_的员工名
				```
				SELECT
					last_name
				FROM 
					employees
				WHERE 
					last_name LIKE '_\_%';
				```
				也可以使用自定义的转义字符
				```
				SELECT
					last_name
				FROM 
					employees
				WHERE 
					last_name LIKE '_$_%' ESCAPE '$';
				```
				注意只能使用英文字符
		2. between and
			1. 特点：
				1. 使用between and 能提高语句的简洁度
				2. 包含临界值
				3. 两个临界值不要调换顺序
			2. 案例：
				查询员工编号在100到120之间的员工信息
				```
				SELECT 
					*
				FROM
					employees
				WHERE
					`employee_id`>=100 AND `employee_id`<=120;

				```
				或者使用between and提高语句的简洁度
				```
				SELECT 
					*
				FROM
					employees
				WHERE
					`employee_id` BETWEEN 100 AND 120;
				```
				·
		3. in
			相当于=
			1. 含义：判断某字段的值是否属于in列表中的某一项
			2. 特点：
				1. 使用in提高语句简洁度
				2. in列表的值类型必须一致或兼容
				3. 不支持通配符和对应使用的转义字符
			3. 查询工种编号是IT_PROG、AD_VP、AD_PRES中的一个的员工名和工种编号
				```
				SELECT 
					last_name,
					job_id
				FROM
					`employees`
				WHERE
					job_id='IT\_PROG' OR job_id='AD\_VP' OR job_id='AD_PRES';
				```
				或者使用in
				```
				SELECT 
					last_name,
					job_id
				FROM
					employees
				WHERE
					job_id IN ('IT_PROG','AD_VP','AD_PRES');
				
				```
				·
		4. is null
			1. 特点：
				=或<>不能用于判断是否为null值
				is null或者 is not null可以判断null值
			2. 查询没有奖金的员工名和奖金率
				```
				SELECT 
					last_name,
					commission_pct
				FROM
					employees
				WHERE
					commission_pct IS NULL;
				```
				注意=不能判断是否为NULL
				如果要判断有奖金的，就使用is not null
				注意不能用is来判断具体的值
		5. 安全等于 < = >
			1. 查询没有奖金的员工名和奖金率
				```
				SELECT 
					last_name,
					commission_pct
				FROM
					employees
				WHERE
					commission_pct <=> NULL;
				```
				·
			2. 查询工资为12000的员工名和工资
				```
				SELECT 
					last_name,
					salary
				FROM
					employees
				WHERE
					salary <=> 12000;
				```
				·
		6. 安全等于和is null 的对比
			is null 仅可以判断null值，可读性较高，建议使用
			< = > 既可以判断null值，又可以判断普通的数值，可读性较低
	4. 综合案例
		![[Pasted image 20220115155820.png|Pasted image 20220115155820.png]]
		第二题
		```
		SELECT
			last_name,
			department_id
			salary*12*(1+IFNULL(commission_pct,0)) 年薪
		FROM
			employees;
		```
		.
4. 测试：
	![[Pasted image 20220115161437.png|Pasted image 20220115161437.png]]
	![[Pasted image 20220115161500.png|Pasted image 20220115161500.png]]
	第五题的补充，如果全加上，用or连接，就是一样的了
## 5.3 排序查询
1. 引入：
	```
	SELECT * FROM employees;
	```
	.
2. 语法：
	```
	select 查询列表
	from 表
	(where 筛选条件)
	order by 排序列表 asc|desc
	```
	顺序： 表 筛选条件 查询列表 排序列表
3. 案例：
	1. 查询员工信息，要求工资从高到低排序
		```
		SELECT * FROM employees ORDER BY salary DESC;
		```
		.
	2. 查询员工信息，要求工资从低到高排序
		```
		SELECT * FROM employees ORDER BY salary;
		```
		.
	3. 按年薪的高低显示员工的信息和年薪，按表达式排序
		```
		SELECT *,salary*12*(1+IFNULL(commission_pct,0)) 年薪
		FROM employees
		ORDER BY salary*12*(1+IFNULL(commission_pct,0)) DESC;
		```
		.
	4. 按年薪的高低显示员工的信息和年薪，按别名排序
		```
		SELECT *,salary*12*(1+IFNULL(commission_pct,0)) 年薪
		FROM employees
		ORDER BY 年薪 DESC;
		```
		.
	5. 按姓名长度显示员工的姓名和工资，按多个字段排序
		```
		SELECT LENGTH(last_name) 字节长度,last_name,salary
		FROM employees
		ORDER BY LENGTH(last_name) DESC;
		```
		.
	6. 查询员工信息，要求先按工资升序，再按员工编号降序，按多个字段排序
		```
		SELECT *
		FROM employees
		ORDER BY salary ASC,employee_id DESC;
		```
		.
4. 特点：
	1. ASC代表的是升序，DESC代表的是降序，如果不写默认是升序
	2. order by子句中可以支持单个字段、多个字段、表达式、函数、别名
	3. order by子句一般是放在查询语句的最后面，limit子句除外
5. 测试：
	![[Pasted image 20220115225406.png|Pasted image 20220115225406.png]]
	![[Pasted image 20220115225628.png|Pasted image 20220115225628.png]]
## 5.4 常见函数
### 5.4.1 概念：
类似于java中的方法，将一组逻辑语句封装在方法体中，对外暴露方法名
### 5.4.2 好处：
1. 隐藏了实现细节
2. 提高代码的重用性
### 5.4.3 调用：
```
select 函数名 (from 表)
```
from 表是根据函数的需求来决定是否加上
### 5.4.4 特点：
1. 叫什么（函数名）
2. 干什么（函数功能）
### 5.4.5 分类：
#### 5.4.5.1 单行函数
如concat、length、ifnull等等，包括字符函数、数学函数、日期函数、补充的其它函数及流程控制函数
##### 5.4.5.1.1 字符函数
1. length 获取参数值的字节个数
	案例：
	1. 
		```
		SELECT LENGTH('john');
		```
		结果是4
	2. 
		```
		SELECT LENGTH('张三丰hahaha');
		```
		结果是15
	这是根据客户端使用的字符集决定的。
	使用命令
	```
	SHOW VARIABLES LIKE '%char%';
	```
	结果如图
	![[Pasted image 20220116111954.png|Pasted image 20220116111954.png]]
	在utf8中一个汉字占三个字节，一个英文字母占1个字节
2. concat 拼接字符串
	案例：
	```
	SELECT CONCAT(last_name,'_',first_name) FROM employees;
	```
	.
3. upper、lower 变换大小写
	案例：
	1. 
		```
		SELECT UPPER('john');
		```
		结果是JOHN
	2. 
		```
		SELECT LOWER('JoHn');
		```
		结果是john
	3. 将姓变大写，名变小写，然后拼接
		```
		SELECT CONCAT(UPPER(last_name),LOWER(first_name)) FROM employees;
		```
		.
4. substr、substring
	==注意索引从1开始==
	一共有四个重载函数
	案例：李莫愁爱上了陆展元
	1. 输出陆展元
		```
		SELECT SUBSTR('李莫愁爱上了陆展元',7) out_put;
		```
		7指的是第一个字符所在的位置
		**截取从指定索引处及后面的所有字符**
	2. 输出李莫愁
		```
		SELECT SUBSTR('李莫愁爱上了陆展元',1,3) out_put;
		```
		3指的是长度
		**截取从指定索引处指定字符长度的字符**，==注意不是字节长度==
	3. 姓名中首字符大写，其它字符小写，然后用_拼接，显示出来
		```
		SELECT CONCAT(UPPER(SUBSTR(last_name,1,1)),'_',LOWER(SUBSTRING(last_name,2)))
		FROM employees;
		```
		.
5. instr 返回字串第一次出现的索引，如果找不到返回0
	案例：
	1. 
		```
		SELECT INSTR('杨不悔爱上了殷六侠','殷六侠') AS out_put;
		```
		结果是7
		如果加上from employees的话会出来107个7
	2. 
		```
		SELECT INSTR('杨不悔殷六侠爱上了殷六侠','殷六侠') AS out_put;
		```
		结果是4
	3. 
		```
		SELECT INSTR('杨不悔殷六侠爱上了殷六侠','殷八侠') AS out_put;
		```
		结果是0
6. trim 去除字符串首尾的某种字符
	案例：
	1. 
		```
		SELECT LENGTH(TRIM('       张翠山         ')) AS out_put;
		```
		结果是9
	2. 
		```
		SELECT TRIM('a' FROM 'aaaaaaaaaaa张翠山aaaaaaaaaaa') AS out_put;
		```
		结果是张翠山
	3. 
		```
		SELECT TRIM('aa' FROM 'aaaaaaaaaaa张aaaaaaaaa翠山aaaaaaaaaaa') AS out_put;
		```
		结果是a张aaaaaaaaa翠山a
7. lpad 用指定的字符实现左填充指定长度
	案例：
	1. 
		```
		SELECT LPAD('殷素素',10,'*') AS out_put;
		```
		结果是\*\*\*\*\*\*\*殷素素
	2. 
		```
		SELECT LPAD('殷素素',2,'*') AS out_put;
		```
		结果是殷素，因为长度不足会自动截断
8. rpad 用指定的字符实现右填充指定长度
	案例：
	1. 
		```
		SELECT RPAD('殷素素',2,'ab') AS out_put;
		```
		结果是殷素
	2. 
		```
		SELECT RPAD('殷素素',12,'ab') AS out_put;
		```
		结果是殷素素ababababa，总长度是12
9. replace 替换
	案例：
	```
	SELECT REPLACE('周芷若周芷若周芷若周芷若张无忌爱上了周芷若','周芷若','赵敏') AS out_put;
	```
	结果是赵敏赵敏赵敏赵敏张无忌爱上了赵敏
##### 5.4.5.1.2 数学函数
1. round 四舍五入
	它有两个重载函数
	案例：
	1. 
		```
		SELECT ROUND(1.45);
		```
		结果是1
	2.	
		```
		SELECT ROUND(-1.45);
		```
		结果是-1
	3. 
		```
		SELECT ROUND(1.567,2);
		```
		结果是1.57。2指的是在小数点之后保留两位
2. ceil 向上取整，返回>=该参数的最小整数
	案例：
	1. 
		```
		SELECT CEIL(1.002);
		```
		结果是2
	2. 
		```
		SELECT CEIL(1.000);
		```
		结果是1
3. floor 向下取整，返回<=该参数的最大整数
	案例：
	1. 
		```
		SELECT FLOOR(-1.02);
		```
		结果是-2
	2. 
		```
		SELECT FLOOR(9.99);
		```
		结果是9
4. truncate 截断
	案例：
	```
	SELECT truncate(1.65,1);
	```
	结果是1.5
5. mod 取余
	案例：
	```
	SELECT mod(5,3);
	```
	和
	```
	SELECT 5%3;
	```
	功能是一样的
	mod(a,b)其实相当于==**a-a/b\*b**==
	使用以下例子进行区分：
	1. 
		```
		SELECT mod(10,3);
		```
		结果是1
	2. 
		```
		SELECT mod(-10,3);
		```
		结果是-1
	3. 
		```
		SELECT mod(10,-3);
		```
		结果是1
	4. 
		```
		SELECT mod(-10,-3);
		```
		结果是-1
##### 5.4.5.1.3 日期函数
1. now 返回当前系统日期+时间
	```
	SELECT now();
	```
	结果：2022-01-20 11:40:50
2. curdate 返回当前系统日期，不返回时间
	```
	SELECT curdate();
	```
	结果：2022-01-20
3. curtime 返回当前时间，不包含日期
	```
	SELECT curtime();
	```
	结果：11:43:57
4. 可以获取指定的部分，年、月、日、小时、分钟、秒
	案例：
	1. 
		```
		SELECT year(now()) 年;
		```
		结果：年 2022
	2. 
		```
		SELECT year('1999-1-1') 年;
		```
		结果：年 1999
	3. 
		```
		SELECT  distinct year(hiredate) 年
		FROM employees;
		```
		结果：
		![[Pasted image 20220120115759.png|Pasted image 20220120115759.png]]
	4. 
		```
		SELECT month(now()) 月;
		```
		结果：月 1
	5. 
		```
		SELECT monthname(now()) 月;
		```
		结果：月 January
5. str_to_date 将日期格式的字符转换为指定格式的日期
	案例：
	1. 
		```
		SELECT str_to_date('9-13-1999','%m-%d-%Y');
		```
		结果：1999-09-13 。日期内部储存的默认格式月份是有两位
	2. 查询入职日期为1992年4月3日的员工信息
		```
		SELECT *
		FROM employees
		WHERE hiredate='1992-4-3';
		```
		结果：
		![[Pasted image 20220121093010.png|Pasted image 20220121093010.png]]
		但是实际情况下用户输入的年份和月份可能并不完全是按照这样的格式输入的，所以需要使用该函数。
		```
		SELECT * FROM employees WHERE hiredate=str_to_date('4-3 1992','%c-%d %Y');
		```
		.
6. date_format 将日期转换成字符
	案例：
	1. 
		```
		SELECT date_format('2018/6/6', '%Y年%m月%d日');
		```
		.
	2. 
		```
		SELECT date_format(now(),'%Y年%m月%d日') AS out_put;
		```
		结果是2022年01月21日
	3. 查询有奖金的员工名和入职日期（xx月/xx日 xx年）
		```
		SELECT last_name
		 ,date_format(hiredate,'%m年/%d日 %y年') 入职日期
		FROM employees
		WHERE commission_pct IS NOT NULL;
		```
		.
7. 常用的格式符
	
	| 格式符 | 功能 |
	|------|--------|
	| %Y | 四位的年份 |
	| %y | 两位的年份 |
	| %m | 月份（01，02，03……） |
	| %c | 月份（1，2，3……） |
	| %d | 日（01，02，03……） |
	| %H | 小时（24小时制）|
	| %h | 小时（12小时制） |
	| %i | 分钟（00，01……59） |
	| %s | 秒（00，01……59） |
##### 5.4.5.1.4 其它函数
```
	SELECT version();
	SELECT database();
	SELECT user();
```

##### 5.4.5.1.5 流程控制函数
1. if 函数，三目运算符的效果
	案例：
	1. 
		```
		SELECT if(10>5,'大','小');
		```
		结果：大
	2. 
		```
		SELECT last_name
			 ,commission_pct
			 ,IF(commission_pct is NULL,'没奖金，呵呵','有奖金，嘻嘻') 备注
		FROM employees;
		```
		.
2. case 函数
	1. 使用一：类似于switch，适合用于处理等值判断
		- 语法：
			case 要判断的字段或表达式
			when 常量1 then 要显示的值1或语句1;（*如果是语句加;，值不用加*）
			when 常量2 then 要显示的值2或语句2;
			else 要显示的值n或语句n;（代表默认情况）
			end
			**注意如果then后面是值得话放分号默认就结束了**
		- 案例：
			查询员工的工资，要求：
			部门号=30，显示的工资为1.1倍
			部门号=40，显示的工资为1.2倍
			部门号=50，显示的工资为1.3倍
			其它部门，显示的工资为原工资
			```
			SELECT salary 原始工资
			 ,department_id
			 ,CASE department_id
			 WHEN 30 THEN salary*1.1
			 WHEN 40 THEN salary*1.2
			 WHEN 50 THEN salary*1.3
			 else salary
			 END AS 新工资
			FROM employees;
			```
			**注意case……end相当于查询的一个对象，如果后面还要加新对象记得加逗号**
	2. 使用二：相当于多重if，多用于处理区间
		- 语法：
			case 
			when 条件1 then 要显示的值1或语句1;（*如果是语句加;，值不用加*）
			when 条件2 then 要显示的值2或语句2;
			……
			else 要显示的值n或语句n;
			end
		- 案例：
			查询员工的工资情况
			如果工资>20000，显示A级别
			如果工资>15000，显示B级别
			如果工资>10000，显示C级别
			否则，显示D级别
			```
			SELECT salary
			 ,CASE WHEN salary>20000 THEN 'A'
			 WHEN salary>15000 THEN 'B'
			 WHEN salary>10000 THEN 'C' ELSE 'D' END AS 工资级别
			FROM employees;
			```
			.
#### 5.4.5.2 分组函数
1. 功能：做统计使用，又称为统计函数、聚合函数、组函数
2. 分类：
	1. sum 求和
	2. avg 平均值
	3. max 最大值
	4. min 最小值
	5. count 计算个数
3. 特点：
	1. sum、avg一般用于处理数值型
		max、min、count可以处理任何类型
		[[MySQL笔记#^192a06|案例]]
	2. 是否忽略null值
		以上分组函数都忽略null值
		[[MySQL笔记#^9371da|案例]]
	3. 可以和DISTINCT搭配实现去重的运算
		[[MySQL笔记#^95cb2e|案例]]
	4. count函数的单独介绍
		一般使用count(\*)用于统计行数
		[[MySQL笔记#^c4b21d|案例]]
	5. 和分组函数一同查询的字段要求是group by后的字段
		[[MySQL笔记#^6fbc0c|案例]]
4. 案例：
	1. 简单的使用：
		1. 
			```
			SELECT SUM(salary) FROM employees;
			SELECT AVG(salary) FROM employees;
			SELECT MIN(salary) FROM employees;
			SELECT MAX(salary) FROM employees;
			SELECT COUNT(salary) FROM employees;
			```
			.
		2. 
			```
			SELECT SUM(salary) 和
			 ,round(AVG(salary),2) 平均
			 ,MAX(salary) 最高
			 ,MIN(salary) 最低
			 ,COUNT(salary) 个数
			FROM employees;
			```
			结果：
			![[Pasted image 20220121142828.png|Pasted image 20220121142828.png]]
	2. 参数支持哪些类型：
		 1. 
			```
			SELECT SUM(last_name),AVG(last_name) FROM employees;
			```
			结果：
			![[Pasted image 20220122142859.png|Pasted image 20220122142859.png]]
			没有逻辑意义
		2. 
			```
			SELECT SUM(hiredate),AVG(hiredate) FROM employees;
			```
			结果：
			![[Pasted image 20220122143025.png|Pasted image 20220122143025.png]]
			也是没有逻辑意义
		3. 
			```
			SELECT MAX(last_name), MIN(last_name) FROM employees;
			```
			结果：
			![[Pasted image 20220122143146.png|Pasted image 20220122143146.png]]
			是有逻辑意义的。因为既然能排序就有可比较性，就有最大值和最小值
		4. 
			```
			SELECT MAX(hiredate),MIN(hiredate) FROM employees;
			```
			结果：
			![[Pasted image 20220122143341.png|Pasted image 20220122143341.png]]
		5. 
			```
			SELECT COUNT(commission_pct) FROM employees;
			```
			结果：
			![[Pasted image 20220122143536.png|Pasted image 20220122143536.png]]
			注意count只计数非空的值
	^192a06
	3. 是否忽略null：
		1. sum
			```
			SELECT SUM(commission_pct) FROM employees;
			```
			结果：
			![[Pasted image 20220122145733.png|Pasted image 20220122145733.png]]
			忽略null值，因为null无论加上任何数都是null
		2. avg
			```
			SELECT AVG(commission_pct)
			 ,SUM(commission_pct)/35
			 ,SUM(commission_pct)/107
			FROM employees;
			```
			结果：
			![[Pasted image 20220122150127.png|Pasted image 20220122150127.png]]
			忽略null值，因为除以的是35不是107
		3. 	max,min
			```
			SELECT MAX(commission_pct),MIN(commission_pct) FROM employees;
			```
			结果：
			![[Pasted image 20220122150640.png|Pasted image 20220122150640.png]]
			忽略null值，否则其中有一个显示的就是null了
		4. count
			```
			SELECT COUNT(commission_pct) FROM employees;
			```
			结果：
			![[Pasted image 20220122150851.png|Pasted image 20220122150851.png]]
			忽略null值。这个函数本身的意义就是计算整个结果中非空元素  
	^9371da
	4. 和distinct搭配，进行去重：
		1. 
			```
			SELECT SUM( DISTINCT salary)
			 ,SUM(salary)
			FROM employees;
			```
			结果：
			![[Pasted image 20220122162849.png|Pasted image 20220122162849.png]]
		2. 
			```
			SELECT COUNT( DISTINCT salary)
			 ,COUNT( salary)
			FROM employees;
			```
			结果：
			![[Pasted image 20220122163215.png|Pasted image 20220122163215.png]] 
	^95cb2e
	5. count函数的详细介绍 
		1. 
			```
			SELECT COUNT(*) FROM employees;
			```
			意思是统计一共有多少非空行。只要有一个不是空，就可以被统计上。结果是107。
		2. 
			```
			SELECT COUNT(1) FROM employees;
			```
			意思是新增了一列，每一行都是1，统计一共有多少个1。结果是107。不论括号里面的常量是什么结果都是107。
		3. 效率
			- MYISAM引擎下，因为自己本身就带了一个计数器，所以count(\*)效率高
			- INNODB引擎下，count(1)和count(\*)的效率差不多，但是比count(字段)要高一些，因为count(字段)需要对是否为空进行判断
			因此我们较多使用count(\*)
	^c4b21d
	6. 和分组函数一同查询的字段有限制
		```
		SELECT AVG(salary),employee_id FROM employees;
		```
		结果：
		![[Pasted image 20220122172337.png|Pasted image 20220122172337.png]]
		右边那个100没有任何意义
		 ^6fbc0c
5. 补充：datediff()函数
	用于计算两个日期之间的相差天数。例如：
	```
	SELECT
	 DATEDIFF('2017-10-1', '2017-9-29');
	```
	结果是2
	查询员工表中的最大入职时间和最小入职时间的相差天数
	```
	SELECT
	 datediff(MAX(hiredate), MIN(hiredate)) difference
	FROM
	 employees;
	```
	结果：
	![[Pasted image 20220124105035.png|Pasted image 20220124105035.png]]
## 5.5 分组查询
- 引入：查询每个部门的平均工资
可以使用group by 子句将表中的数据分成若干组
- 语法：
	SELECT column,group_function(column)
	FROM table
	\[WHERE condition\]
	\[GROUP BY group_by_expression\]
	\[ORDER BY column\];
- 分组查询是搭配分组函数一起使用的，查询列表必须特殊，要求是分组函数和group by后出现的字段
- 特点：
	1. 分组筛选分为两类：
		
		| |数据源|位置|关键字|案例|
		|--|--|--|--|--|
		|分组前筛选|原始表|group by子句的前面|where| [[MySQL笔记#^39d4a2\|案例]]|
		|分组后筛选|分组后的结果集|group by子句的后面|having|[[MySQL笔记#^6127e8\|案例]]|
		1. 分组函数作条件肯定是放在having子句中
		2. 能用分组前筛选的，就优先考虑分组前筛选（有的条件既可以放在having那里又可以放在where那里
- 案例：
	1. 简单的分组查询 
		1. 查询每个工种的最高工资
			```
			SELECT MAX(salary),job_id FROM employees GROUP BY job_id;
			```
			结果：
			![[Pasted image 20220124112204.png|Pasted image 20220124112204.png]]
		2. 查询每个位置上的部门个数
			```
			SELECT COUNT(*),location_id FROM departments GROUP BY location_id;
			```
			结果：
			![[Pasted image 20220124113059.png|Pasted image 20220124113059.png]]
	2. 添加分组前的筛选条件 ^39d4a2
		1. 查询邮箱中包含a字符的，每个部门的平均工资
			```
			SELECT AVG(salary),department_id
			FROM employees
			WHERE email LIKE '%a%'
			GROUP BY department_id;
			```
			结果：
			![[Pasted image 20220124113609.png|Pasted image 20220124113609.png]]
		2. 查询每个领导手下有奖金的员工的最高工资
			```
			SELECT MAX(salary),manager_id
			FROM employees
			WHERE commission_pct IS NOT NULL
			GROUP BY manager_id;
			```
			结果：
			![[Pasted image 20220124114447.png|Pasted image 20220124114447.png]]			
	3. 添加分组后的筛选条件 ^6127e8
		1. 查询哪个部门的员工个数>2
			步骤：
			1. 查询每个部门的员工个数
				```
				SELECT COUNT(*),department_id
				FROM employees
				GROUP BY manager_id;
				```
				结果：
				![[Pasted image 20220124115114.png|Pasted image 20220124115114.png]]
			2. 根据第一步的结果进行筛选，查询哪个部门的员工个数>2
				```
				SELECT
				 COUNT(*),
				 department_id
				FROM
				 employees
				GROUP BY
				 manager_id
				HAVING
				 COUNT(*) > 2;
				```
				结果：
				![[Pasted image 20220124115324.png|Pasted image 20220124115324.png]]
				注意追加的要求不能使用where，不能放在group by前面，因为是对已有的结果进行一个筛选。
		2. 查询每个工种有奖金的员工的最高工资>12000的公众编号和最高工资
			步骤：
			1. 查询每个工种有奖金的员工的最高工资
				```
				SELECT MAX(salary),job_id
				FROM employees
				WHERE commission_pct IS NOT NULL
				GROUP BY job_id;
				```
				结果：
				![[Pasted image 20220124162147.png|Pasted image 20220124162147.png]]
			2. 根据第1步的结果筛选最高工资是否大于12000
				```
				SELECT MAX(salary),job_id
				FROM employees
				WHERE commission_pct IS NOT NULL
				GROUP BY job_id
				HAVING MAX(salary)>12000;
				```
				结果：
				![[Pasted image 20220124162501.png|Pasted image 20220124162501.png]]
		3. 查询领导编号>102的每个领导手下的最低工资>5000的领导编号以及其手下的最低工资
			步骤：
			1. 查询每个领导手下员工的最低工资
				```
				SELECT MIN(salary),manager_id
				FROM employees
				GROUP BY manager_id;
				```
				.
			2. 添加筛选条件：领导编号>102
				```
				SELECT MIN(salary),manager_id
				FROM employees
				WHERE manager_id>102
				GROUP BY manager_id;
				```
				.
			3. 添加筛选条件：最低工资>5000
				```
				SELECT MIN(salary),manager_id
				FROM employees
				WHERE manager_id>102
				GROUP BY manager_id
				HAVING MIN(salary)>5000;
				```
				结果：
				![[Pasted image 20220124165219.png|200]]
	4. 按表达式或者函数分组
		按员工姓名的长度分组，查询每一组的员工个数，筛选员工个数>5的有哪些
		步骤：
		1. 查询每个长度的员工个数
			```
			SELECT COUNT(*),LENGTH(last_name)
			FROM employees
			GROUP BY LENGTH(last_name);
			```
			.
		2. 添加筛选条件
			```
			SELECT COUNT(*),LENGTH(last_name)
			FROM employees
			GROUP BY LENGTH(last_name)
			HAVING COUNT(*)>5;
			```
			结果：
			![[Pasted image 20220124202529.png|200]]
		3. 这也是支持别名的：
			```
			SELECT COUNT(*) c,LENGTH(last_name) len_name
			FROM employees
			GROUP BY len_name
			HAVING c>5;
			```
			结果：
			![[Pasted image 20220124202731.png|200]]
# 6. DML语言的学习
Data Manipulation Language 数据操纵语言
主要进行增删改操作。可以将数据查询语言和数据操纵语言合称数据操纵语言
# 7. DDL语言的学习
Data Definition Language 数据定义语言
# 8. TCL语言的学习
Transaction Control Language 事务控制语言
# 9.