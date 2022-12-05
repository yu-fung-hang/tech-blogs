# JPA Annotations

## @GeneratedValue

* **IDENTITY**: Indicates that the persistence provider must assign primary keys for the entity using a database identity column.
* **SEQUENCE**: Indicates that the persistence provider must assign primary keys for the entity using a database sequence.
* **TABLE**: Indicates that the persistence provider must assign primary keys for the entity using an underlying database table to ensure uniqueness.
* **AUTO**: Indicates that the persistence provider should pick an appropriate strategy for the particular database. The AUTO generation strategy may expect a database resource to exist, or it may attempt to create one. A vendor may provide documentation on how to create such resources in the event that it does not support schema generation or cannot create the schema resource at runtime.

&emsp;&ensp;&nbsp; Reference: 
https://docs.oracle.com/javaee/6/api/javax/persistence/GenerationType.html

## @Column

* String **table**: The name of the table that contains the column. If absent the column is assumed to be in the primary table.
* int **precision** & int **scale**: Precision is the number of digits in a number. Scale is the number of digits to the right of the decimal point in a number. For example, the number 123.45 has a precision of 5 and a scale of 2.