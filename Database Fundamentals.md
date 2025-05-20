# Database Fundamentals
SQL is Structured Query Language.

A Database is a shared collection of logically related data with description of these data, designed to meet the information needs of an organization.

- Data Storage: A database is used to store large amounts of structured data, making it easily accessible, searchable, and retrievable.
- Data Analysis: A database can be used to perform complex data analysis, generate reports, and provide insights into the data.
- Record Keeping: A database is often used to keep track of important records, such as financial transactions, customer information, and inventory levels.
- Web Applications: Databases are an essential component of many web applications, providing dynamic content and user management.

Properties of an ideal database
- Integrity
- Availability
- Security
- Independent of Application
- Concurrency

  ## Types Of Databases

  1. Relational Databases: Also known as SQL databases, these databases use a relational model to organize data into tables with rows and columns.
  2. Nosql Databases: These databases are designed to handle large amounts of unstructured or semi-structured data, such as documents, images, or videos.
  3. Column Databases: These databases store data in columns rather than rows, making them well-suited for data warehousing and analytical applications. (Amazon, Redshift, Google BigQuery)
  4. Graph Databases: These databases are used to store and query graph-structured data, such as social network connections or recommendation systems.
  5. Key-value Databases: These databases store data as a collection of keys and values, making them well-suited for caching and simple data storage needs (Redis and Amazon DynamoDB)

     ### Relational Databases
     Also known as SQL databases, these databases use a relational model to organize data into tables with rows and columns.Relation -> Table. Columns -> Attributes. Row -> Tuple. No. of rows -> Cardinatlity. No. of attribute -> Degree.

  ## Database Keys

  A key in a database is an attribute or a set of attributes that uniquely identifies a tuple in a table. Keys play a crucial role in ensuring the integrity and reliability of a database by enforcing unqiue constraints on the data and establishing relationships between tables.

  1. Super Key: A super key is a combination of columns that uniquely identifies any row within a relational database management system table.
  2. Candidate Key: A candidate key is a minimal Super key, meaning it has no redundant attributes. In other words, it's the smallest set of attributes that can be used to uniquely identify a tuple in the table.
  3. Primary Key: A primary key is a unique identifier for each tuple in a table. There can only be one primary key in a table, and it cannot contain null values.
  4. Alternate Key: An alternate key is a candidate key that is not used as the primary key.
  5. Composite Key: A composite key is a primary key that is made up of two or mroe attributes. They are used when a single attribute is not sufficient to uniquely identify a tuple in a table.
  6. Foreign Key: It is a primary key from one table that is used to establish a relationship with another table.
  7. 1:1 -> 1 Table required, 1:N -> 2 Tables required, N:N -> 3 Tables required
