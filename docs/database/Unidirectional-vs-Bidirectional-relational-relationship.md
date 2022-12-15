# Unidirectional vs Bidirectional relational relationship

This has to do with whether common usage (within the application domain) would attempt to access both sides of the relationship from the other side... Invoices to products would probably be unidirectional, as athough we often want to know what products are on an invoice, it is unlikely that you would want to know all the invoices that contain a given product.

Stores to products on the other hand is bi-directional, as we could easily want to access both all the products at a specific store, or find all the stores that sell a specific product.

Bi-Directional is not limited to where the relationship is a many-to-many relationship. An employee to supervisor relationship could easily be bi-directional, if, in our domain model, an employee object will need to be able to access the employee's supervisor object, and of course, the supervisors object contains a property that lists all his assigned employees.

**Example #1:**

**One to Many Bidirectional:** State and City, where State has collection property of Cities, and City has a State property

**Many to Many Unidirectional:** Bus and Rider, where Bus has collection property of Riders, but Rider does not have collection property listing all Buses Rider has ridden in (application does not care).

**Many to Many Bidirectional:** Person class, where each person has Friends Property, as Collection of other person objects this person is friends with;
or...
Artist and Album classes, where Artist has Albums collection, and Album has Artists Collection (where album is compilation of tracks from multiple artists)


**Example #2:**

We have two tables in database: Student Table, Subject Table
Many-To-Many Bidirectional

You need apply the navigation in the database from the following two directions:

    Navigation from Student to Subject

A student can enroll for many subjects in the semester.

    Navigation from Subject to Student

A Subject can have many different students enrolled for it.
Many-To-Many Unidirectional

You need apply the navigation in the database from the just one direction:

    Navigation from Student to Subject

A student can enroll for many subjects in the semester.



## Links