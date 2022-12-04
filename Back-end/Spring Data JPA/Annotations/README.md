# JPA Annotations

## @GeneratedValue

* **IDENTITY**: Indicates that the persistence provider must assign primary keys for the entity using a database identity column.
* **SEQUENCE**: Indicates that the persistence provider must assign primary keys for the entity using a database sequence.
* **TABLE**: Indicates that the persistence provider must assign primary keys for the entity using an underlying database table to ensure uniqueness.
* **AUTO**: Indicates that the persistence provider should pick an appropriate strategy for the particular database. The AUTO generation strategy may expect a database resource to exist, or it may attempt to create one. A vendor may provide documentation on how to create such resources in the event that it does not support schema generation or cannot create the schema resource at runtime.

&emsp;&ensp;&nbsp; Reference: 
https://docs.oracle.com/javaee/6/api/javax/persistence/GenerationType.html