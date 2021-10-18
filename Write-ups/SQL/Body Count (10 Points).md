# Body Count

![Category](http://img.shields.io/badge/Category-SQL-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-10-brightgreen?style=for-the-badge)

## Details

>One of our employees, Jimmie Castora, kept database backups on his computer. DEADFACE compromised his computer and leaked a portion of the database. Can you figure out how many customers are in the database? We want to get ahead of this and inform our customers of the breach.
>
> Submit the flag as `flag{#}`. For example, `flag{12345}`.
>
> [Download MySQL database dump](https://tinyurl.com/r2cxnfua)
> 
> .SHA1: 5867eeb1466b31eb8d361061fddd99700fc5d739
> 
> Password: `d34df4c3`
---

After downloading and unzipping the file we are given a mysql data dump. Lets start `mysqld`, create a blank databse ready to  import the data into it so we can search and manipulate it.

```
sudo systemctl start mysqld 

MariaDB [(none)]> CREATE DATABASE testdb;
Query OK, 1 row affected (0.000 sec)

MariaDB [(none)]> exit
```

We can try to import the data into it like so;

```
sudo mysql demonne < demonne.sql
ERROR 1273 (HY000) at line 25: Unknown collation: 'utf8mb4_0900_ai_ci'
```

To fix this we can replace the offending strings in the SQL dump using `sed` with a gerneric UFT8 encoding like so;

```
sed -i 's/utf8mb4_0900_ai_ci/utf8_general_ci/g' demonne.sql
sed -i 's/utf8mb4/utf8/g' demonne.sql
```

Now we can try to reimport the data again;

```
sudo mysql demonne < demonne.sql
```

This should be sucessful this time, so we can now enter mysql and begin to search and look for the data we need.

```
❯ sudo mysql
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 12
Server version: 10.6.4-MariaDB Arch Linux

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> use demonne;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
MariaDB [demonne]> 
```

Using the `show tables;` commaand we can see there is a customers table.

```
MariaDB [demonne]> show tables;
+-------------------+
| Tables_in_demonne |
+-------------------+
| credit_cards      |
| cust_passwd       |
| customers         |
| employee_passwd   |
| employees         |
| loan_types        |
| loans             |
| test              |
+-------------------+
8 rows in set (0.000 sec)
```

Next we need a field name in that table so we use `describe customers;`

```
MariaDB [demonne]> describe customers;
+------------+-------------+------+-----+---------+----------------+
| Field      | Type        | Null | Key | Default | Extra          |
+------------+-------------+------+-----+---------+----------------+
| cust_id    | smallint(6) | NO   | PRI | NULL    | auto_increment |
| last_name  | tinytext    | NO   |     | NULL    |                |
| first_name | tinytext    | NO   |     | NULL    |                |
| email      | tinytext    | NO   |     | NULL    |                |
| street     | tinytext    | NO   |     | NULL    |                |
| city       | tinytext    | NO   |     | NULL    |                |
| state      | tinytext    | NO   |     | NULL    |                |
| country    | tinytext    | NO   |     | NULL    |                |
| postal     | tinytext    | NO   |     | NULL    |                |
| gender     | tinytext    | NO   |     | NULL    |                |
| dob        | tinytext    | NO   |     | NULL    |                |
+------------+-------------+------+-----+---------+----------------+
11 rows in set (0.001 sec)
```

Now, to find the number of customers we can use the following query - `select count(cust_id) from customers;`

```
MariaDB [demonne]> select count(cust_id) from customers;
+----------------+
| count(cust_id) |
+----------------+
|          10000 |
+----------------+
1 row in set (0.002 sec)
```

With this information we can complete our flag which is;

## flag{10000}
