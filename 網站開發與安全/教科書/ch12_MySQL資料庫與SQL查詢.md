# 第12章 MySQL資料庫與SQL查詢
```
12-1 認識資料庫
12-2 使用phpMyAdmin管理MySQL資料庫
12-3 SQL語法
```
# 12-1 認識資料庫
```

```
# 12-2 使用phpMyAdmin管理MySQL資料庫
```

```
# MySQL資料庫
```
MySQL Functions
https://www.w3schools.com/sql/sql_ref_mysql.asp
```
# 12-3 SQL語法
```
SQL語法
使用phpMyAdmin執行SQL查詢
```
## SQL語法
```
SQL == Structured Query Language == 結構查詢語言

不同資料庫管理系統有不同分類: 底下為微軟資料庫的分類
1.DDL – Data Definition Language
2.DML – Data Manipulation Language
3.DCL – Data Control Language
4.TCL – Transaction Control Language

https://www.geeksforgeeks.org/sql-ddl-dml-tcl-dcl/
```
```
https://www.w3schools.com/sql/
```
```
CRUD
C ==> CREATE 建立
R ==> Read   查詢
U ==> UPDATE 更新與修改
D ==> DELETE 刪除

https://en.wikipedia.org/wiki/Create,_read,_update_and_delete
```
## 1.DDL – Data Definition Language
```
https://en.wikipedia.org/wiki/Data_definition_language

CREATE
DROP ==> destroys an existing database, table, index, or view.
TRUNCATE ==>  delete all data from a table
ALTER ==>
```
## 2.DML – Data Manipulation Language
```
https://en.wikipedia.org/wiki/Data_manipulation_language

SELECT ... FROM ... WHERE ... (strictly speaking DQL) ==>查詢資料
SELECT ... INTO ...
INSERT INTO ... VALUES ... ==> 新增 資料
UPDATE ... SET ... WHERE ...==> 更新(修改) 資料
DELETE FROM ... WHERE ...==> 刪除 資料
```
## 3.DCL – Data Control Language
```
https://en.wikipedia.org/wiki/Data_control_language

GRANT ==> 賜予 權限 ==> to allow specified users to perform specified tasks.
REVOKE ==>收回 權限 ==>  to remove the user accessibility to database object.
```
## 4.TCL – Transaction Control Language
```
異動(Transaction)管理
COMMIT
ROLLBACK 
....
```
# SELECT
```
SQL關鍵字沒有英文字母大小寫之分，而且可以寫成多行或一行
SELECT   欄位名稱
FROM      資料表名稱
[WHERE  搜尋子句]
[ORDER BY  排序子句 {ASC|DESC}]
```
```
INSERT INTO 資料表名稱 (欄位1, 欄位2, 欄位3…) Values (資料1, 資料2, 資料3…)
```
```
DELETE  FROM 資料表名稱 WHERE 條件


```
