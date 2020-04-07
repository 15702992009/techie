# MYSQL WHERE

---

### 1) Using MySQL `WHERE` clause with equal operator example

```sql
SELECT 
    lastname, 
    firstname, 
    jobtitle
FROM
    employees
WHERE
    jobtitle = 'Sales Rep';
```

---

### 2) Using MySQL `WHERE` clause with `AND` operator

In this example, the expression in the `WHERE` clause uses the `AND` operator to combine two conditions:

```sql
SELECT 
    lastname, 
    firstname, 
    jobtitle,
    officeCode
FROM
    employees
WHERE
    jobtitle = 'Sales Rep' AND 
    officeCode = 1;
```

---

### 3) Using MySQL `WHERE` clause with `OR` operator

This query finds employees whose job title is `Sales Rep` or employees who locate the office with office

```sql
SELECT 
    lastName, 
    firstName, 
    jobTitle, 
    officeCode
FROM
    employees
WHERE
    jobtitle = 'Sales Rep' OR 
    officeCode = 1
ORDER BY 
    officeCode , 
    jobTitle;
```

---

### 4) Using MySQL `WHERE` with `BETWEEN` operator example

The `BETWEEN` operator returns `TRUE` if a value is in a range of values:

```sql
SELECT 
    firstName, 
    lastName, 
    officeCode
FROM
    employees
WHERE
    officeCode BETWEEN 1 AND 3
ORDER BY officeCode;
```

---

### 5) Using MySQL `WHERE` with the `LIKE` operator example

The `LIKE` operator evaluates to `TRUE` if a value matches a specified pattern. To form a pattern, you use `%` and `_` wildcards. The `%` wildcard matches any string of zero or more characters while the `_` wildcard matches any single character.

```sql
SELECT 
    firstName, 
    lastName
FROM
    employees
WHERE
    lastName LIKE '%son'
ORDER BY firstName;
```

---

### 6) Using MySQL `WHERE` clause with the `IN` operator example

The `IN` operator returns `TRUE` if a value matches any value in a list.

```sql
value IN (value1, value2,...)
```

The following example uses the `WHERE` clause with the `IN` operator to find employees who locate in the office with office code 1

```sql
SELECT 
    firstName, 
    lastName, 
    officeCode
FROM
    employees
WHERE
    officeCode IN (1 , 2, 3)
ORDER BY 
    officeCode;
```

---

### 7) Using MySQL `WHERE` clause with the `IS NULL` operator

To check if a value is `NULL` or not, you use the `IS NULL` operator, not the equal operator (`=`). The `IS NULL` operator returns `TRUE` if a value is `NULL`



This statement uses the `WHERE` clause with the `IS NULL` operator to get the row whose value in the `reportsTo` column is `NULL`:

```sql
SELECT 
    lastName, 
    firstName, 
    reportsTo
FROM
    employees
WHERE
    reportsTo IS NULL;
```

### 8) Using MySQL `WHERE` clause with comparison operators

The following table shows the comparison operators that you can use to form the expression in the `WHERE` clause.

| **Operator** | **Description**                                              |
| ------------ | ------------------------------------------------------------ |
| =            | Equal to. You can use it with almost any data types.         |
| <> or !=     | Not equal to                                                 |
| <            | Less than. You typically use it with numeric and date/time data types. |
| >            | Greater than.                                                |
| <=           | Less than or equal to                                        |
| >=           | Greater than or equal to                                     |

#  

# MySQL DISTINCT

**Summary**: in this tutorial, you will learn how to use the MySQL  **`DISTINCT`** clause in the `SELECT` statement to eliminate duplicate rows in a result set.

## MySQL `DISTINCT` and `NULL` values

If a column has `NULL` values and you use the `DISTINCT` clause for that column, MySQL keeps only one `NULL` value because `DISTINCT` treats all `NULL` values as the same value.

## MySQL `DISTINCT` with multiple columns

You can use the `DISTINCT` clause with more than one column. In this case, MySQL uses the combination of values in these columns to determine the uniqueness of the row in the result set.

For example, to get a unique combination of city and state from the `customers` table, you use the following query:

```sql
SELECT DISTINCT
    state, city
FROM
    customers
WHERE
    state IS NOT NULL
ORDER BY 
    state, 
    city;
```

![MySQL DISTINCT multiple columns example](https://sp.mysqltutorial.org/wp-content/uploads/2011/02/MySQL-DISTINCT-multiple-columns-example.png)

Without the `DISTINCT` clause, you will get the duplicate combination of state and city as follows:

![MySQL without DISTINCT clause on multiple columns](https://sp.mysqltutorial.org/wp-content/uploads/2011/02/MySQL-without-DISTINCT-clause-on-multiple-columns.png)

## `DISTINCT` clause vs. `GROUP BY` clause



```sql
/* 
If you use the `GROUP BY` clause in the `SELECT` statement `without using` `aggregate functions`, the `GROUP BY` clause behaves `like` the `DISTINCT` clause
*/
SELECT 
    state
FROM
    customers
GROUP BY state;

-- GROUP BY (without using aggregate functions) syntax is same as DISTINCT

SELECT DISTINCT
	state
FROM
	customers;


```

## MySQL `DISTINCT` and aggregate functions

You can use the `DISTINCT` clause with an [aggregate function](https://www.mysqltutorial.org/mysql-aggregate-functions.aspx) e.g., [SUM](https://www.mysqltutorial.org/mysql-sum/), [AVG](https://www.mysqltutorial.org/mysql-avg/), and [COUNT](https://www.mysqltutorial.org/mysql-count/), to remove duplicate rows before the aggregate functions are applied to the result set.

For example, to count the unique states of customers in the U.S., you use the following query:

```sql
SELECT 
    COUNT(DISTINCT state)
FROM
    customers
WHERE
    country = 'USA';
```



## MySQL `DISTINCT` with `LIMIT` clause

In case you use the `DISTINCT` clause with the `LIMIT` clause, MySQL immediately stops searching when it finds the number of unique rows specified in the `LIMIT` clause.

The following query selects the first five non-null unique states in the `customers` table.

```sql
SELECT DISTINCT
	state
FROM
	customers
WHERE
	state IS NOT NULL
LIMIT 5;	
```

# MySQL AND Operator

**Summary**: in this tutorial, you will learn how to the MySQL `AND` operator to combine multiple Boolean expressions to filter data.

## Introduction to MySQL `AND` operator

The `AND` operator is a logical operator that combines two or more [Boolean](https://www.mysqltutorial.org/mysql-boolean/) expressions and returns true only if both expressions evaluate to true. The `AND` operator returns false if one of the two expressions evaluate to false.

Here is the syntax of the `AND` operator:

```sql
boolean_expression_1 AND boolean_expression_2
```

The following table illustrates the results of the `AND` operator when combining true, false, and null.

|           | TRUE  | FALSE | NULL  |
| --------- | ----- | ----- | ----- |
| **TRUE**  | TRUE  | FALSE | NULL  |
| **FALSE** | FALSE | FALSE | FALSE |
| **NULL**  | NULL  | FALSE | NULL  |

When evaluating an expression that has the `AND` operator, MySQL stops evaluating the remaining parts of the expression whenever it can determine the result. This function is called short-circuit evaluation

# MySQL OR Operator



**Summary**: in this tutorial, you will learn how to use the MySQL `OR` operator to combine Boolean expressions for filtering data.

## Introduction to the MySQL `OR` operator

The MySQL `OR` operator combines two Boolean expressions and returns true when either condition is true.

The following illustrates the syntax of the `OR` operator.

```sql
SELECT true OR false AND false;
--result
1
```

How it works

1. First, MySQL evaluates the `AND` operator, therefore the expression `false AND false` returns false
2. second, MySQL evaluates the `OR` operator hence the expression `true OR false` returns true

**To change the order of evaluation, you use the parentheses, for example:**

```sql
SELECT (true OR false) AND false;
--result
0
```

How it works

1. First, MySQL evaluates the expression in the parenthesis `(true OR false)` returns true
2. Second, MySQL evaluates the remaining part of the statement, `true AND false` returns false.

```sql
SELECT   
    customername, 
    country, 
    creditLimit
FROM   
    customers
WHERE(country = 'USA'
        OR country = 'France')
      AND creditlimit > 100000;
---------------different below-------------
/*
Notice that if you do not use the parentheses, the query will return the customers who locate in the USA or the customers who locate in France with the credit limit greater than 10,000.
*/

SELECT    
    customername, 
    country, 
    creditLimit
FROM    
    customers
WHERE country = 'USA'
        OR country = 'France'
        AND creditlimit > 10000;
      
```

`with` parentheses

![MySQL OR AND example](https://sp.mysqltutorial.org/wp-content/uploads/2016/05/MySQL-OR-AND-example.png)

`without` parentheses

![MySQL operator precedence example](https://sp.mysqltutorial.org/wp-content/uploads/2016/05/MySQL-operator-precedence-example.png)



