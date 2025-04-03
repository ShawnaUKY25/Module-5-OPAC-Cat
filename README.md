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
The following Python snippet demonstrates how to establish a connection to a MySQL database using `mysql-connector-python`:

```python
import mysql.connector

def connect_to_db():
    return mysql.connector.connect(
        host="localhost",
        user="root",
        password="yourpassword",
        database="library_db"
    )

conn = connect_to_db()
cursor = conn.cursor()
print("Database connection established.")
```

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

```python
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
- Install dependencies: `pip install mysql-connector-python`
- Set up the database schema:

```sql
CREATE DATABASE library_db;
USE library_db;

CREATE TABLE Books (
    book_id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    author VARCHAR(255) NOT NULL,
    ISBN VARCHAR(13) UNIQUE NOT NULL,
    publication_year INT,
    subject VARCHAR(255)
);
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

### Addressing Gaps
While setting up, some gaps in understanding included:
- Handling SQL injection risks → Solution: Use parameterized queries.
- Ensuring data consistency → Solution: Define constraints in the database schema.

## Links to Site
•	Your OPAC page on your Ubuntu server.

•	Your cataloging module on your Ubuntu server.
