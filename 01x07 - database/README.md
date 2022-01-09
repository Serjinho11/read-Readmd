# Requirements

## 1) Database

In the Vending Machine application, add functionality to store the data (Products) in a database instead of the static list that was used until now.

### Database

Any database can be used (LiteDB, SQLite, SQL Server, etc), but please tell us your decision before starting.

The suggested databases are:

- LiteDB that is a NoSQL database.

- SQLite that is a SQL database.

### Repositories

New repository class must be added to encapsulate the details of accessing the database.

It is a good practice to store the connection string in the `app.config` file.

The existing repository (the in-memory repository) must be kept in the project. The `Bootstrapper` class must be the one that decides which concrete repository to be used in the whole application.

## 2) Dependency Inversion Principle

Separate the Business, Data Access and Presentation into different modules (dll files) and make the Business module independent of the other modules. 

Dependency inversion principle can help in this task. See the following article for details: 

- [How to apply DIP - Module Separation](how-to-apply-dip/README.md)
