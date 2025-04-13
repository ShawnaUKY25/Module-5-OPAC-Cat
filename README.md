# Module-5-OPAC-Cat

## Introduction
An **OPAC (Online Public Access Catalog)** is a digital interface that allows users to search and retrieve bibliographic records from a library database. It serves as the front-end for users to find books, articles, and other materials available in a library system. The **cataloging module** is responsible for adding, editing, and managing these bibliographic records, ensuring accurate and organized data.

## Relational Database Structure
The OPAC and cataloging module rely on a **relational database** to store and manage bibliographic records.

## Step-by-Step Setup

### 1. Establishing Database Connection
In order to understand the relationship bewtween everything I needed to create a visual. 

<img width="341" alt="Screen Shot 2025-04-12 at 8 19 43 PM" src="https://github.com/user-attachments/assets/2e152f45-28ec-4c72-8ddb-dcf930ca1f08" />

SQL supports the OPACDB database file name that helps store, manage, and access book information. The Books table contains details like author, title, publisher, and publication year. SQL lets users search and filter this data using specific criteria. This makes the OPAC system fast and easy to use. Overall, SQL helps deliver accurate and useful search results.

### 2. Cataloging Module: Adding Records
The cataloging module allows librarians to add new books to the database:

```
def add_book(title, author, isbn, publication_year, subject):
   ('Julia Phillips', 'Disappearing Earth', '2019');
```

### 3. OPAC Search and Retrieval
A basic function for searching books based on title:

```
mysql> select author from books;
mysql> select copyright from books;
mysql> select author, title from books;
mysql> select author from books where author like '%millet%';
mysql> select title from books where author like '%mbue%';
mysql> select author, title from books where title not like '%e';
mysql> select * from books;

```

### 4. Enhancing OPAC and Cataloging for Real-World Use
To make the OPAC and cataloging module more realistic, consider:
- **User Authentication**: Implementing login/logout functionality.
- **Advanced Search Filters**: Enabling search by author, subject, or year.
- **Book Availability Tracking**: Showing whether a book is checked out or available.

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
Absolutely! Here’s a simple and memorable way to understand and **remember the command sequence preference** when working across **MySQL**, **Bash**, **PHP**, and **HTML** — especially if you're jumping between them in a web development context.

---

### 🔄 **Command Context Cheat Sheet: “Where Am I Talking?”**

Think of each environment like a *different person you're talking to* — each with its own "language" and command style.

---

### 1. 🐚 **Bash (Terminal)**  
> You're talking to the *server* directly.

- **Commands start like:** `cd`, `ls`, `nano`, `mysql`, `sudo`, etc.  
- **Usage:** Navigating files, starting services, editing files.  
- ✅ *Start here* to move into MySQL or to run PHP scripts manually.

**Tip to remember:** *Bash = the doorway* into everything.

---

### 2. 🛢️ **MySQL (Inside the database)**  
> Now you’re talking directly to the *database engine*.

- **Commands look like:**  
  ```sql
  USE OPACDB;
  SELECT * FROM Books WHERE author='Rowling';
  ```
- **Ends with `;`**  
- **Entered after typing `mysql -u root -p` from Bash.**

**Tip to remember:** *MySQL talks to tables.* Always end SQL commands with a semicolon.

---

### 3. 🐘 **PHP (Server-side scripting)**  
> You're scripting *how the web server will talk to the database*.

- **Looks like:**  
  ```php
  $query = "SELECT * FROM Books WHERE author='Rowling'";
  $result = mysqli_query($conn, $query);
  ```
- Embedded in `.php` files, executed when requested by a browser or via Bash (`php file.php`).

**Tip to remember:** *PHP is the translator* between the user and MySQL.

---

### 4. 🌐 **HTML (Front-end)**  
> Now you’re talking to the *user’s browser*.

- **Used for:** Displaying the results from PHP in readable format.
- Example:
  ```html
  <form method="POST" action="search.php">
    <input type="text" name="search">
    <input type="submit" value="Search">
  </form>
  ```
---


## Using Documentation
I had to use the reference guide above to remind myself that the comamand line langague requirments change, based on what I am trying to create or edit.

### Challenges
The biggest challenge with this module was setting up the cataloging permissions and passwords. 
I created a cataloging directory, however, when I attempted to access the directory, the system said it didn't exist.

<img width="1002" alt="Screen Shot 2025-04-12 at 4 14 42 PM" src="https://github.com/user-attachments/assets/b899a9d9-5b5a-4cb7-b924-aa4efd0eb5ee" />

I went ahead and went through the security steps for practice; with my fingers crossed that it might work, but it didn't. I'm not sure what I've done wrong or how to fix it. 

<img width="1057" alt="Screen Shot 2025-04-13 at 10 10 05 AM" src="https://github.com/user-attachments/assets/674b55f9-6cf8-420e-94a2-4b6cb4c812bf" />

I'm open to suggestions.


## Links to Site
•	Your OPAC page on your Ubuntu server.

http://34.29.1.232/mylibrary.html

•	Your cataloging module on your Ubuntu server.

http://34.29.1.232/index.html
