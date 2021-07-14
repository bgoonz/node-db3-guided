# Objective 2 - query data from multiple tables: WEB43 - 4.2

> Now that we understand the basics of querying data from a single table, let's move on to selecting data from multiple tables using JOIN operations.

Now that we understand the basics of querying data from a single table, let's move on to selecting data from multiple tables using JOIN operations.

## Overview

We can use a `JOIN` to combine query data from multiple tables using a single `SELECT` statement.

There are different types of joins; some are listed below:

- inner joins.
- outer joins.
- left joins.
- right joins.
- cross joins.
- non-equality joins.
- self joins.

Using `joins` requires that the two tables of interest contain at least one field with shared information. For example, if a *departments* table has an *id* field, and an employee table has a *department_id* field, and the values that exist in the *id* column of the *departments* table live in the *department_id* field of the employee table, we can use those fields to join both tables like so:

    select * from employees
    join departments on employees.department_id = departments.id

This query will return the data from both tables for every instance where the `ON` condition is true. If there are employees with no value for department*id or where the value stored in the field does not correspond to an existing id in the* departments _table, then that record will NOT be returned. In a similar fashion, any records from the_ departments _table that don't have an employee associated with them will also be omitted from the results. Basically, if the_ id\* does not show as the value of department_id for an employee, it won't be able to join.

We can shorten the condition by giving the table names an alias. This is a common practice. Below is the same example using aliases, picking which fields to return and sorting the results:

    select d.id, d.name, e.id, e.first_name, e.last_name, e.salary
    from employees as e
    join departments as d
      on e.department_id = d.id
    order by d.name, e.last_name

Notice that we can take advantage of white space and indentation to make queries more readable.

There are several ways of writing joins, but the one shown here should work on all database management systems and avoid some pitfalls, so we recommend it.

The syntax for performing a similar join using Knex is as follows:

    db('employees as e')
      .join('departments as d', 'e.department_id', 'd.id')
      .select('d.id', 'd.name', 'e.first_name', 'e.last_name', 'e.salary')

## Follow Along

A good explanation of how the different types of joins can be seen [in this article from w3resource.com (Links to an external site.)](https://www.w3resource.com/sql/joins/sql-joins.php).

## Challenge

Use [this online tool (Links to an external site.)](https://www.w3schools.com/Sql/tryit.asp?filename=trysql_select_top) to write the following queries:

- list the products, including their category name.
- list the products, including the supplier name.
- list the products, including both the category name and supplier name.

[Source](https://lambdaschool.instructure.com/courses/1314/pages/objective-2-query-data-from-multiple-tables?module_item_id=602072)
