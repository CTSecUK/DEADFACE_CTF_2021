# Address Book
![Category](http://img.shields.io/badge/Category-SQL-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-30-brightgreen?style=for-the-badge)

## Details

>It looks like DEADFACE is targeting one of De Monne's customers. Check out this thread in Ghost Town and submit the customer's name as the flag: `flag{Jane Doe}`.
>
> Use the MySQL database dump from Body Count.
>
> [Ghost Town thread](https://ghosttown.deadface.io/t/why-do-people-fall-for-this/62)
---

Looking at this thread we see;

![image](https://user-images.githubusercontent.com/73170900/137784427-54e86b4f-251c-4675-bb14-2d67df2e22b0.png)

We can use this information to query the database for the likely victim. 

Looking at the `customers` table using the command `describe customer;` we can see we have the following information available to us;

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
```

Looking for customers who live in `Vienna` using the query `SELECT * from customers WHERE city = 'Vienna'` we see the following;

```
MariaDB [demonne]> SELECT * from customers WHERE city = 'Vienna';
+---------+-----------+------------+---------------------------+------------------------------+--------+-------+---------+--------+--------+------------+
| cust_id | last_name | first_name | email                     | street                       | city   | state | country | postal | gender | dob        |
+---------+-----------+------------+---------------------------+------------------------------+--------+-------+---------+--------+--------+------------+
|    1516 | Gronav    | Rogers     | rgronav163@opensource.org | 0303 Lakewood Gardens Avenue | Vienna | VA    | US      | 22184  | M      | 04/05/2003 |
|    2042 | Gummer    | Kyle       | kgummer1kp@ow.ly          | 170 Del Sol Terrace          | Vienna | VA    | US      | 22184  | M      | 12/14/1963 |
|    2574 | Allsopp   | Collen     | callsopp1zh@sbwire.com    | 90360 Red Cloud Crossing     | Vienna | VA    | US      | 22184  | F      | 10/25/1973 |
|    3960 | Loade     | Courtney   | cloade31z@prnewswire.com  | 47 Moose Parkway             | Vienna | VA    | US      | 22184  | M      | 04/14/1951 |
|    5685 | Brasier   | Berke      | bbrasier4dw@google.cn     | 94145 Brown Parkway          | Vienna | VA    | US      | 22184  | M      | 11/17/1968 |
|    8030 | Laguerre  | Kimble     | klaguerre671@php.net      | 5229 Utah Place              | Vienna | VA    | US      | 22184  | M      | 03/07/1970 |
+---------+-----------+------------+---------------------------+------------------------------+--------+-------+---------+--------+--------+------------+
6 rows in set (0.004 sec)
```

However the thread also mentioned;
> ***She*** lives near the Vienna branch of De Monne 

The only customer from the above list who is female is;
```
+---------+-----------+------------+---------------------------+------------------------------+--------+-------+---------+--------+--------+------------+
| cust_id | last_name | first_name | email                     | street                       | city   | state | country | postal | gender | dob        |
+---------+-----------+------------+---------------------------+------------------------------+--------+-------+---------+--------+--------+------------+
|    2574 | Allsopp   | Collen     | callsopp1zh@sbwire.com    | 90360 Red Cloud Crossing     | Vienna | VA    | US      | 22184  | F      | 10/25/1973 |
+---------+-----------+------------+---------------------------+------------------------------+--------+-------+---------+--------+--------+------------+
```

So the flag is;

## flag{Collen Allsopp}
