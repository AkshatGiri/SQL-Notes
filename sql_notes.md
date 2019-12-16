# SQL NOTES 

1. Sql Stands for `Structured Query Language`
2. It's the `query language` used for interacting with `RDBMS` ( Relational database management systems).
3. Relational databases use SQL and store data in tables with rows and columns.


## Tables and Keys

1. Tables are made of rows and columns
2. A column ( vertical ) indicates a single attribtue. 
3. A row ( horizontal ) indicates a full entry. 
4. When we are creating a table we want a column for the `primary key`.
5. `primary key` can be used to uniquely identify the subject for eg. `student_id`. 
6. A `primary key` that has a usage in the real world for eg. SSN. It can be called the `natural key`.
7. A `key` that has no usage in the real work is called the `surrogate key`. 
8. A `foreign key` is a column  that stores the `primary key` of another table.
9. A table can have more than 1 `foreign key` column. 
10. We can have two or more rows combined to have a `primary key`, in this case we call it `composite key`. 
11. supposedly `composite keys` are pretty commonly used. 


## SQL basics

1. `SQL` used to interact with `RDBMS` for eg. Mysql, posgress etc. 
2. `SQL` is a hybrid language, 4 types of languages in one. 
    1. `Data Query Language ( DQL )`
    2. `Data Definition Language ( DDL )`
    3. `Data Control Language ( DCL )`
    4. `Data Manipulation Language ( DML )`

To start mysql 
* `mysql -u root -p`
* enter password `password` ( that's my local password for mysql )


### SQL Datatypes

* `INT`                 - whole numbers
* `DECIMAL`             - decimal numbers - exact value 
* `VARCHAR(100)`        - String of text of length
* `BLOB`                - Binary large object, stores large data
* `DATE`                - 'YYYY-MM-DD'
* `TIMESTAMP`           - used for recording exact times 

## SQL Commands

#### ___To create a database___  
```
CREATE DATABASE $database_name
```

#### ___To create a table___
```
CREATE TABLE $table_name (
    $column_name $datatype,
     /* to make this attribute the primary key */
    $column_name $datatype PRIMARY KEY,

    /* Or the primary key can be defined down below like this */
    PRIMARY KEY($column_name),

    /* Adding an attribute that cannot be null */
    $column_name $datatype NOT NULL,

    /* Adding an attribute that should be unique */
    $column_name $datatype UNIQUE,

    /* Providing the default value for an attribute*/
    $column_name $datatype DEFAULT $default_value,

    /* Increment int automatically */
    $column_name INT AUTO_INCREMENT,

    /* to add foreign key */
    FOREIGN KEY($column_name) REFERENCES $table_name($column_name) ON DELETE SET NULL

);
```

#### ___To get details about schema of table___
```
DESCRIBE $table_name;
```

#### ___To delete a table___
```
DROP TABLE $table_name;
```

#### ___To add column to table___
```
 ALTER TABLE $table_name ADD $column_name $datatype;
```

#### ___To delete column from table___
```
 ALTER TABLE $table_name DROP $column_name;
```

#### ___To change column data type to foreign key___
```
ALTER TABLE $table_name
ADD FOREIGN KEY($column_name)
REFERENCES $table_name2($column_name)
ON DELETE SET NULL;

```

#### ___To Add data to table___
```
INSERT INTO $table_name VALUES($values_needed);

/* We can also specify the attributes we want to add like so  */ 

INSERT INTO $table_name($attributes) VALUES($values_in_attributes_order);
```


#### ___To update data in table___
```
/* To apply change to every single row */
UPDATE $table_name 
SET $attribute = $new_value;

/* To apply change using a condition */
UPDATE $table_name 
SET $attribute = $new_value, $attribute2 = $new_value
WHERE $condition;
```

#### ___To delete data in table___
```
/* To delete all data in table */
DELETE FROM $table_name;

/* To apply change using a condition */
DELETE FROM $table_name 
WHERE $condition;
```

#### ___To get data from table___
```
/* To get all the columns and rows from table */
SELECT * FROM $table_name; /* '*' in this case means all the columns */

/* To select which columns to return we can specifiy */
SELECT $column_name1, $table_name.$coulmn_name2 FROM $table_name;

/* We can order the data we are getting. BY default order is ascending */
SELECT * from $table_name 
ORDER BY $column_name;

/* To make the order descending */
SELECT * from $table_name 
ORDER BY $column_name DESC;

/* Limit the amount of data we get back */
SELECT * from $table_name 
LIMIT $number;

/* To filter data */
SELECT * FROM $table_name
WHERE $condition; 

/* to get non duplicate values in database */
SELECT DISTINCT $column_name FROM $table_name;

```

#### ___SQL Functions___
```
SELECT COUNT($coulmn_name) FROM $table_name;

SELECT SUM($coulmn_name) FROM $table_name; 
```

// Todo: Add notes for these topics
### ___SQL Union___

### ___SQL Join___

### ___SQL Triggers___

### ___SQL Nested Queries___

### ___ER Diagrams and relationships___