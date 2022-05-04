## Задача 1

Найдите команду для выдачи статуса БД и приведите в ответе из ее вывода версию сервера БД.
```
mysql> \s

Server version:		8.0.29 MySQL Community Server - GPL
```

Приведите в ответе количество записей с price > 300.
```
mysql> select count(*) from orders where price > 300;
+----------+
| count(*) |
+----------+
|        1 |
+----------+
1 row in set (0.01 sec)
```

## Задача 2

Используя таблицу INFORMATION_SCHEMA.USER_ATTRIBUTES получите данные по пользователю test и приведите в ответе к задаче.
```
mysql> select * from INFORMATION_SCHEMA.USER_ATTRIBUTES WHERE user="test";
+------+------+---------------------------------------+
| USER | HOST | ATTRIBUTE                             |
+------+------+---------------------------------------+
| test | %    | {"fname": "James", "lname": "Pretty"} |
+------+------+---------------------------------------+
1 row in set (0.00 sec)
```

## Задача 3

Исследуйте, какой engine используется в таблице БД test_db и приведите в ответе.
```
mysql> SELECT TABLE_NAME, ENGINE FROM information_schema.TABLES WHERE TABLE_SCHEMA='test_db';
+------------+--------+
| TABLE_NAME | ENGINE |
+------------+--------+
| orders     | InnoDB |
+------------+--------+
1 row in set (0.00 sec)
```
Измените engine и приведите время выполнения и запрос на изменения из профайлера в ответе:
```
mysql> show profiles;
+----------+------------+---------------------------------------------------------------------------------------+
| Query_ID | Duration   | Query                                                                                 |
+----------+------------+---------------------------------------------------------------------------------------+
|        5 | 0.00024550 | show engines                                                                          |
|        6 | 0.00090925 | SELECT TABLE_NAME, ENGINE FROM information_schema.TABLES WHERE TABLE_SCHEMA='test_db' |
|        7 | 0.01112250 | ALTER TABLE orders ENGINE MyISAM                                                      |
|        8 | 0.01043175 | ALTER TABLE orders ENGINE InnoDB                                                      |
+----------+------------+---------------------------------------------------------------------------------------+
4 rows in set, 1 warning (0.00 sec)
```


