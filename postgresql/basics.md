# PostgreSQL Basics

## Table of Contents
1. [Introduction](#introduction)
2. [Connecting to PostgreSQL](#connecting-to-postgresql)
3. [Basic SQL Commands](#basic-sql-commands)
4. [Data Types](#data-types)
5. [Indexes](#indexes)

## Introduction
PostgreSQL is an open-source, powerful relational database system. It is known for its stability, scalability, and advanced features.

## Connecting to PostgreSQL

### Connecting via Command Line
```bash
psql -h localhost -U username -d database_name
```
- -h: Hostname
- -U: Username
- -d: Database name

## Connecting via Java (JDBC)
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class PostgreSQLExample {
    public static void main(String[] args) {
        String url = "jdbc:postgresql://localhost:5432/mydb";
        String user = "username";
        String password = "password";

        try (Connection conn = DriverManager.getConnection(url, user, password)) {
            System.out.println("Connected to PostgreSQL database!");
        } catch (SQLException e) {
            System.out.println("Connection failed!");
            e.printStackTrace();
        }
    }
}
```
## Basic SQL Commands
### Creating a Database
```sql
CREATE DATABASE mydb;
```

### Creating a Table
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Inserting Data
```sql
INSERT INTO users (name, email) VALUES ('John Doe', 'john.doe@example.com');
```
### Querying Data
```sql
SELECT * FROM users;
```
### Updating Data
```sql
UPDATE users SET email = 'new.email@example.com' WHERE name = 'John Doe';
```
### Deleting Data
```sql
Copy code
DELETE FROM users WHERE id = 1;
```
## Data Types
- Character Types: CHAR, VARCHAR, TEXT
- Numeric Types: INTEGER, SERIAL, BIGINT, DECIMAL
- Date/Time Types: DATE, TIMESTAMP, TIME
- Boolean: BOOLEAN
- JSON: JSON, JSONB for structured data
- 
## Indexes
Creating indexes can significantly improve the performance of SELECT queries.

### Creating an Index
```sql
CREATE INDEX idx_users_email ON users (email);
```
#### Unique Index
```sql
CREATE UNIQUE INDEX idx_unique_email ON users (email);
```