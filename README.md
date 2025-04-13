# Module-5-OPAC-Cat

## Introduction
An **OPAC (Online Public Access Catalog)** is a digital interface that allows users to search and retrieve bibliographic records from a library database. It serves as the front-end for users to find books, articles, and other materials available in a library system. The **cataloging module** is responsible for adding, editing, and managing these bibliographic records, ensuring accurate and organized data.

## Relational Database Structure
The OPAC and cataloging module rely on a **relational database** to store and manage bibliographic records. This database follows a structured format with tables such as:

- **Books** (book_id, title, author, ISBN, publication_year, subject)
- **Authors** (author_id, name, birth_year, nationality)
- **Users** (user_id, name, email, membership_type)
- **Transactions** (transaction_id, user_id, book_id, checkout_date, due_date)

The **OPAC** retrieves records from these tables through SQL queries, while the **cataloging module** enables the addition and modification of these records.

## Step-by-Step Setup

### 1. Establishing Database Connection
In order to understand the relationship bewtween everything I needed to create a visual. 

<img width="341" alt="Screen Shot 2025-04-12 at 8 19 43 PM" src="https://github.com/user-attachments/assets/2e152f45-28ec-4c72-8ddb-dcf930ca1f08" />

SQL supports the OPACDB database by helping store, manage, and access book information. The Books table contains details like author, title, publisher, and publication year. SQL lets users search and filter this data using specific criteria. This makes the OPAC system fast and easy to use. Overall, SQL helps deliver accurate and useful search results.


### 2. Cataloging Module: Adding Records
The cataloging module allows librarians to add new books to the database:

```python
def add_book(title, author, isbn, publication_year, subject):
    query = "INSERT INTO Books (title, author, ISBN, publication_year, subject) VALUES (%s, %s, %s, %s, %s)"
    cursor.execute(query, (title, author, isbn, publication_year, subject))
    conn.commit()
    print("Book added successfully.")

add_book("The Great Gatsby", "F. Scott Fitzgerald", "9780743273565", 1925, "Fiction")
```

### 3. OPAC Search and Retrieval
A basic function for searching books based on title:

```
python
def search_books(title):
    query = "SELECT * FROM Books WHERE title LIKE %s"
    cursor.execute(query, ("%" + title + "%",))
    results = cursor.fetchall()
    for row in results:
        print(row)

search_books("Gatsby")
```

### 4. Enhancing OPAC and Cataloging for Real-World Use
To make the OPAC and cataloging module more realistic, consider:
- **User Authentication**: Implementing login/logout functionality.
- **Advanced Search Filters**: Enabling search by author, subject, or year.
- **Book Availability Tracking**: Showing whether a book is checked out or available.
- **User-Friendly Interface**: Creating a web-based or GUI application for interaction.

### 5. Configuration Steps

- Set up searchable book database using SQL
  
```
CREATE DATABASE opacdb;
USE opacdb;

mysql> create table books (
        id int unsigned not null auto_increment,
        author varchar(150) not null,
        title varchar(150) not null,
        copyright year(4) not null,
        primary key (ID)
);
```
In order to confirm a table has been created use 
```

mysql> show tables;
mysql> describe books;
```
To add new titles to the books table

```
mysql> insert into books (author, title, copyright) values
('Jennifer Egan', 'The Candy House', '2022');

```





## Key Details
- **Primary Keys**: Ensure `book_id` and `author_id` use `AUTO_INCREMENT`.
- **Indexes**: Use indexes on frequently searched fields (e.g., title, author).
- **Foreign Keys**: Maintain referential integrity between tables (e.g., linking books to authors).

## Using Documentation
To build this module, documentation from the following sources was referenced:
- **MySQL Documentation** for database setup and queries.
- **Python MySQL Connector Docs** for database interaction.
- **Flask/Python Web Development Resources** for enhancing OPAC.

### Challenges

## Links to Site
•	Your OPAC page on your Ubuntu server.

http://34.29.1.232/mylibrary.html

•	Your cataloging module on your Ubuntu server.

http://34.29.1.232/index.html
