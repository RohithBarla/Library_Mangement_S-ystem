# Library Management System

## Overview
The **Library Management System** is a Python-based application that helps manage library operations such as adding books, issuing books, returning books, and maintaining user records. The system is designed to be user-friendly and efficient for librarians and users. It uses **SQL** for database management to store book and user details.

## Features
- **Book Management**: Add, delete, and update book records
- **User Management**: Register users and maintain user details
- **Issue & Return Books**: Track borrowed and returned books
- **Search Functionality**: Search books by title, author, or category
- **Reports & Logs**: Generate reports on issued books and due dates
- **SQL Database Integration**: Uses **MySQL/PostgreSQL/SQLite** for data storage

## Tech Stack
- **Python**
- **MySQL/PostgreSQL/SQLite** (Database for storing records)
- **Tkinter** (GUI for desktop application) / **Flask** (if web-based)
- **Pandas** (for data manipulation)

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/library-management-system.git
   cd library-management-system
   ```
2. Set up a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Set up the database:
   - Create a new database in MySQL/PostgreSQL
   - Run the SQL script provided in `schema.sql` to create tables
   - Update `config.py` with your database credentials

5. Run the application:
   ```bash
   python main.py
   ```

## Database Schema
```sql
CREATE TABLE books (
    id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL,
    author VARCHAR(255) NOT NULL,
    genre VARCHAR(100),
    isbn VARCHAR(50) UNIQUE NOT NULL
);

CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    contact_info VARCHAR(255)
);

CREATE TABLE issued_books (
    id INT PRIMARY KEY AUTO_INCREMENT,
    book_id INT,
    user_id INT,
    issue_date DATE,
    return_date DATE,
    FOREIGN KEY (book_id) REFERENCES books(id),
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

## Usage
- **Add Books**: Input book details (title, author, genre, ISBN)
- **Register Users**: Add user details (name, ID, contact info)
- **Issue a Book**: Assign a book to a user with an issue date
- **Return a Book**: Mark books as returned and update records
- **Search Books**: Look for books using filters

## Example Code Snippet
```python
import mysql.connector

def create_database():
    conn = mysql.connector.connect(host='localhost', user='root', password='password')
    cursor = conn.cursor()
    cursor.execute("CREATE DATABASE IF NOT EXISTS library")
    conn.close()

def connect_db():
    return mysql.connector.connect(host='localhost', user='root', password='password', database='library')

# Initialize database
create_database()
```

## Future Enhancements
- Implement **Barcode Scanner** for book tracking
- Add **Email Notifications** for due dates
- Create a **Web-Based Interface** with Flask/Django



## License
This project is licensed under the **MIT License**.

---
Feel free to modify and enhance it as per your project requirements! 🚀
