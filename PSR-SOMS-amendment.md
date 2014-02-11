# PSR Amendment for SOMS

The following describes the naming conventions and coding standards used by the
SOMS group.

It is meant to be an amendment to [PSR-0][], [PSR-1][], and [PSR-2][].

[PSR-0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[PSR-1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[PSR-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md

## 1. Global Functions

Global functions MUST follow the standard convention by PHP for naming the
function and its arguments.

### 1.1 Example

```php
<?php

function execute_script($name, $second_name) {
  // body
}
```

## 2. Multi-Line Conditions

Conditional clauses covering multiple lines MAY increase indenting to prettify
the code.

### 2.1 Example

```php
if ($a == $b &&
    $c != $d) {
  // body
}
```

## 3. Inline SQL Queries

SQL queries can easily become very long and splitting them up on multiple lines
can be a way of extending the readability of them. When doing so, there are a
few rules that SHOULD be followed.

SQL statement keywords; SELECT, FROM, WHERE, ORDER BY, LIMIT, etc, SHOULD be
on their own line with no indenting, their clauses SHOULD each be on their own
line with indent.

The SQL statement keywords for joins SHOULD each be on their own line with
double indent since they are a sub of the FROM condition, and the entire JOIN
clause SHOULD be on a single line.

### 3.1 Example

A long query that should be broken up for code readability:

```sql
SELECT tbl1.*,tbl2.relation FROM longTableName tbl1 LEFT OUTER JOIN anotherLongTableName tbl2 ON tbl1.id = tbl2.relationID LEFT OUTER JOIN thirdTable tbl3 ON tbl3.rel2 = tbl2.rel3 WHERE tbl1.created > 123456789 AND tbl2.status = 'on' AND tbl3.foo = 'bar' ORDER BY tbl1.created DESC;
```

The above query can be written in the following way to improve readability:

```sql
SELECT
  tbl1.*,
  tbl2.relation
FROM
  longTableName tbl1
    LEFT OUTER JOIN anotherLongTableName tbl2 ON tbl1.id = tbl2.relationID
    LEFT OUTER JOIN thirdTable tbl3 ON tbl3.rel2 = tbl2.rel3
WHERE
  tbl1.created > 123456789 AND
  tbl2.status = 'on' AND
  tbl3.foo = 'bar'
ORDER BY
  tbl1.created DESC;
```

## 4. Database Tables and Columns

Camel case MUST be used for naming table names and its columns.

### 4.1 Example

```sql
CREATE TABLE lists (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `userID` INT UNSIGNED NOT NULL,
  `firstName` VARCHAR(32) NOT NULL,
  `lastName` VARCHAR(32) NOT NULL,
  PRIMARY KEY (`id`)
)
```
