# MaterializeMySQL文档
https://clickhouse.com/docs/zh/engines/database-engines/materialize-mysql

### 使用条件
* The MaterializedMySQL engine requires binlog_format='ROW'
* The MaterializedMySQL engine requires default_authentication_plugin='mysql_native_password'

### MySQL配置
需要配置开启binlog并'ROW'格式启动，保证GTID_MODE=ON模式打开。用户密码加密方式需要使用mysql_native_password模式.
* MySQL: set GLOBAL ENFORCE_GTID_CONSISTENCY = ON;
* MySQL: set GLOBAL GTID_MODE = ON;

### 开启MaterializeMySQL
SET allow_experimental_database_materialized_mysql=1;

### 实例Clickhouse物化MySQL数据库(binlog同步mysql数据库进行实时数据同步)
```sql
SET allow_experimental_database_materialized_mysql=1;
CREATE DATABASE mysql ENGINE = MaterializeMySQL('mysql:3306', 'db', 'admin', '123456');
```