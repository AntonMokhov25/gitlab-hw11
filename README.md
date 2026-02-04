# Домашнее задание к занятию "«Работа с данными (DDL/DML)»" - `Мохов Антон`
### Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

1.2. Создайте учётную запись sys_temp. 

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

1.4. Дайте все права для пользователя sys_temp. 

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос: 
```sql
ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.7. Восстановите дамп в базу данных.

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*
### Решение
<img width="1301" height="392" alt="image" src="https://github.com/user-attachments/assets/dc1ecacf-9d7b-49c9-9917-0bb036a8c3ae" />
<img width="1857" height="717" alt="image" src="https://github.com/user-attachments/assets/f199b053-addb-49c4-bf6c-ca685c011b2c" />
<img width="1763" height="696" alt="image" src="https://github.com/user-attachments/assets/b1c701be-773a-4500-9bfd-3153b22b2b07" />

```sql
-- 1.2. Создание пользователя
CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY 'password';

-- 1.3. Список пользователей (Скриншот 1)
SELECT user, host FROM mysql.user;

-- 1.4. Выдача прав
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;

-- 1.5. Просмотр прав (Скриншот 2)
SHOW GRANTS FOR 'sys_temp'@'localhost';

-- 1.6. Смена типа аутентификации (перед переподключением)
ALTER USER 'sys_temp'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

-- === ДАЛЕЕ ВЫПОЛНЯТЬ ПОСЛЕ ПЕРЕПОДКЛЮЧЕНИЯ ПОД sys_temp ===

-- 1.7. Восстановление дампа (пример через SOURCE, пути могут отличаться)
-- Сначала схема
SOURCE /path/to/file/sakila-schema.sql;
-- Затем данные
SOURCE /path/to/file/sakila-data.sql;

-- 1.8. Получение всех таблиц базы данных (Скриншот 3)
USE sakila;
SHOW FULL TABLES;
```
### Задание 2
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)
```
Название таблицы | Название первичного ключа
customer         | customer_id
```
### Решение
<img width="1663" height="486" alt="image" src="https://github.com/user-attachments/assets/65c7cb52-b108-4ea5-ab19-4560f920c27a" />


