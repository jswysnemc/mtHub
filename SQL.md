## SQL语句分类

### D<font color=Red>D</font>L(Definition)			数据库<font color=Red>定义</font>语言

### D<font color=Red>M</font>L(Manipulation)	 数据库<font color=Red>操作</font>语言

### D<font color=Red>Q</font>L(Query)					数据库<font color=Red>查询</font>语言

### D<font color=Red>C</font>L(Control)				  数据库<font color=Red>控制</font>语言



## DDL

### 查询

- #### 查询所有数据库

  ```sql
  show databases;
  ```

- #### 查询当前数据库

  ```sql
  select databases();
  ```

  

### 创建

- ```sql
  create database [if not exists] 数据库名 [default charset] 字符集 [collate 排序规则];
  ```

### 删除

- ```sql
  drop database [if exists] 数据库名;
  ```

### 使用

- ```
  USE 数据库名;
  ```

  

## DDL-表操作-查询

- #### 查询当前数据库所有表

- ```sql
  show tables;
  ```
  
- #### 查询表结构

  ``` sql
  desc 表名;
  ```

- ####　查询指定的建表语句

  ```sql
  show create table 表名;
  ```


- #### 复制数据表

    ```sql
    create table[if not exists] 新表名
    [like 参照表名]
    [as (select语句)];
    ```
- #### 删除数据表

    ```sql
    drop table[if exists] 表名1 [,表名2...];
    
    //删除表,并重新创建
    truncate table 表名;
    ```
- #### 修改数据表名

    ``` sql
    alter table rename 旧表名1 to 新表名1,[旧表名2 to 新表名2]...;
    ```

### 列操作

- #### 增加新的数据列

    - 添加字段

    - ```sql
        alter table 表名 add 字段名 类型(长度) [comment] [约束];
        ```

    ```sql
    alter [ignore] table 表名
    add 新增列名 数据类型(长度) [first|after参照列的列名];
    ```

- #### 删除的数据列

    ```sql
    alter [ignore] table 表名 drop [colum] 列名
    ```


- #### 重命名数据列

    ```sql
    alter [ignore]table 表名
    change [column]旧列名 新列名 字段类型(长度);
    ```

- #### 修改列的数据类型

    ```sql
    alter [ignore]table 表名
    modify [column]列名 新类型(长度)[firdt|after 列名];
    ```

### 数据约束

- #### 非空约束

    ```sql
    create table grade(		//创建表时设置非空约束
    	gradId int(4) not null comment '年纪编号',
        gradName varchar(50) not null comment '年级名称'
    );
    //对已经存在的列设置非空约束
    alter [ignore]table 表名
    modify 数据类型 not null;
    ```

- #### 唯一约束
    ```sql
    //创建表,列时,在列名类型的后面加上 unique 
    
    //在已经创建的表添加唯一约束
    alter table 表名
    add [constraint]约束名 unique key(列名);
    ```
- #### 主键约束

     ```sql
    //创建表列时,在类名类型的后面加上primary key
    
    //已经创建的表,添加主键约束
    alter table 表名
    add [constraint] 约束名 primary key(列名);
    ```
- #### 默认值约束

    ```sql
    //创建表列时,在类名类型的后面加上  set default 默认值
    
    //已经创建的表,添加默认值约束
    alter table 表名
    alter 列名 set default 默认值;
    ```

- #### 检查约束

    ```sql
    //创建表列时,在类名类型的后面加上 check(条件表达式)
    
    //已经创建的表,添加主键约束
    alter table 表名
    add [constraint] 约束名 check(条件表达式);
    ```


- #### 外键约束

    ```sql
    //创建表列时,
    create table 表名(
    	字段名 数据类型,
    	...
    	[constraint] [外键名称] foreign key(外键字段名) references 主表(主表列名)
    );
    //已经创建表列
    alter table 表名 add constraint 外键名称 foreign key(外键字段名) references 主表(主表列名);
    //删除外键
    alter table 表名 drop foreign key 外键名称;
    ```
    

- ### 总结

    - #### DDL-数据库操作

        ```sql
        show databases;
        create database 数据库名;
        use 数据库名;
        select database();
        drop database 数据库名;;
        ```

    - #### DDL-数据库表操作

        ``` sql
        show tables;
        create table 表名 (字段 字段类型 [约束] [注释]);
        desc 表名;
        show create table 表名;
        alter table 表名 add / modify / change / drop / rename to ;
        drop table 表名;
        ```

    - #### 约束类型

        ```sql
        not null
        unique
        primary
        set default
        check
        ```

        

    

    

    

    



