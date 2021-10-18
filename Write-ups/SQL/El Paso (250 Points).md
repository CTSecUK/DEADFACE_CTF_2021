# El Paso

![Category](http://img.shields.io/badge/Category-SQL-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-250-brightgreen?style=for-the-badge)

## Details

>The regional manager for the El Paso branch of De Monne Financial is afraid his customers might be targeted for further attacks. He would like you to find out the dollar value of all outstanding loan balances issued by employees who live in El Paso. Submit the flag as `flag{$#,###.##}`.
>
> Use the MySQL database dump from Body Count.
---

For this challenge we need to use an SQL JOIN to gather data from two tables, using the below query;

```
SELECT SUM(balance) FROM loans INNER JOIN customers on customers.cust_id = loans.cust_id INNER JOIN employees on employees.employee_id = loans.employee_id
WHERE employees.city = "El Paso";
```

The result of which is;

```
------+
| SUM(balance) |
+--------------+
|    877401.00 |
+--------------+
1 row in set (0.002 sec)
```

So our flag is;

## flag{$877,401.00}
