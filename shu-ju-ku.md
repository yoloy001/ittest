# 数据库

安装

**登录**

```
mysql -u root -p 
```

### 操作库

**创建库**

```
mysql> create DATABASE RUNOOB;
```

**删除库**

```
DROP DATABASE <database_name>; 
```

**选择库**

```
USE database_name;
```

### **操作表**

**创建表**

<pre class="language-sql" data-overflow="wrap"><code class="lang-sql">CREATE TABLE users ( 
<strong>    id INT AUTO_INCREMENT PRIMARY KEY, 
</strong>    username VARCHAR(50) NOT NULL, 
    email VARCHAR(100) NOT NULL, 
    birthdate DATE, 
    is_active BOOLEAN DEFAULT TRUE 
);
</code></pre>

**删除表**

```
DROP TABLE table_name ;
```

**增**

```
INSERT INTO users (username, email, birthdate, is_active)
VALUES ('test', 'test@runoob.com', '1990-01-01', true);
```

**查**

```
-- 选择所有列的所有行 
SELECT * FROM users;
-- 选择特定列的所有行 
SELECT username, email FROM users;
```

**删**

```
DELETE FROM students
WHERE graduation_year = 2021;
```

**改**

```
UPDATE orders
SET status = 'Shipped', ship_date = '2023-03-01'
WHERE order_id = 1001;
```

**备份**

**导出**

```
mysqldump -u root -p mydatabase > mydatabase_backup.sql
```

**导入**

```
mysql -uroot -p123456 < runoob.sql
```
