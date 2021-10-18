# Keys

![Category](http://img.shields.io/badge/Category-SQL-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-20-brightgreen?style=for-the-badge)

## Details

>One of De Monne's database engineers is having issues rebuilding the production database. He wants to know the name of one of the foreign keys on the loans database table. Submit one foreign key name as the flag: `flag{foreign-key-name}` (can be ANY foreign key).
>
> Use the MySQL database dump from **Body Count**.
---

To find this information we need to look at the INFORMATION_SCHEMA database in mysql.

Using the following query (Note the loans table specified in the WHERE clause of this query as specified in the challenege details);

```
MariaDB [(none)]> SELECT
    ->   TABLE_NAME,
    ->   COLUMN_NAME,
    ->   CONSTRAINT_NAME,
    ->   REFERENCED_TABLE_NAME,
    ->   REFERENCED_COLUMN_NAME
    -> FROM INFORMATION_SCHEMA.KEY_COLUMN_USAGE
    -> WHERE
    ->   TABLE_NAME = 'loans';
```

This returns the following information;

```
+------------+--------------+-----------------------+-----------------------+------------------------+
| TABLE_NAME | COLUMN_NAME  | CONSTRAINT_NAME       | REFERENCED_TABLE_NAME | REFERENCED_COLUMN_NAME |
+------------+--------------+-----------------------+-----------------------+------------------------+
| loans      | loan_id      | PRIMARY               | NULL                  | NULL                   |
| loans      | cust_id      | fk_loans_cust_id      | customers             | cust_id                |
| loans      | employee_id  | fk_loans_employee_id  | employees             | employee_id            |
| loans      | loan_type_id | fk_loans_loan_type_id | loan_types            | loan_type_id           |
| loans      | loan_id      | PRIMARY               | NULL                  | NULL                   |
| loans      | cust_id      | fk_loans_cust_id      | customers             | cust_id                |
| loans      | employee_id  | fk_loans_employee_id  | employees             | employee_id            |
| loans      | loan_type_id | fk_loans_loan_type_id | loan_types            | loan_type_id           |
+------------+--------------+-----------------------+-----------------------+------------------------+
8 rows in set (0.000 sec)
```

The relevent informationhere is in the `CONSTRAINT_NAME` column.

Any one of the `Foreign Keys` can be submitted as the flag;


## flag{fk_loans_cust_id}
## flag{fk_loans_employee_id}
## flag{fk_loans_loan_type_id}
