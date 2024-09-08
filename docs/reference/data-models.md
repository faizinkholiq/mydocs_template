# Data Models Reference

This document provides a comprehensive overview of the data models used in the application. It covers the entities, their attributes, relationships, and any relevant constraints or validation rules.

## Table of Contents

1. [Introduction](#introduction)
2. [Entities](#entities)
   - [User](#user)
   - [Product](#product)
   - [Order](#order)
3. [Relationships](#relationships)
   - [User-Order Relationship](#user-order-relationship)
   - [Product-Order Relationship](#product-order-relationship)
4. [Validation Rules](#validation-rules)
5. [Data Integrity Constraints](#data-integrity-constraints)
6. [Example SQL Schema](#example-sql-schema)
7. [Best Practices](#best-practices)

## Introduction

This section introduces the data models and explains their importance. The data models define the structure and organization of the data in the system, ensuring consistency, integrity, and accessibility.

## Entities

### User

The `User` entity represents a person who uses the application.

- **Attributes**:
  - `id` (UUID): Unique identifier for the user.
  - `username` (String): Unique username for the user.
  - `email` (String): User's email address (must be unique).
  - `password_hash` (String): Hashed password for user authentication.
  - `created_at` (DateTime): The date and time when the user was created.
  - `updated_at` (DateTime): The date and time when the user was last updated.

- **Indexes**:
  - `username_index`: Index on the `username` field for faster lookup.
  - `email_index`: Index on the `email` field to enforce uniqueness.

### Product

The `Product` entity represents an item that can be purchased by a user.

- **Attributes**:
  - `id` (UUID): Unique identifier for the product.
  - `name` (String): Name of the product.
  - `description` (Text): Description of the product.
  - `price` (Decimal): Price of the product.
  - `created_at` (DateTime): The date and time when the product was created.
  - `updated_at` (DateTime): The date and time when the product was last updated.

- **Indexes**:
  - `product_name_index`: Index on the `name` field for faster search operations.

### Order

The `Order` entity represents a purchase made by a user.

- **Attributes**:
  - `id` (UUID): Unique identifier for the order.
  - `user_id` (UUID): Foreign key referencing the `User` entity.
  - `product_id` (UUID): Foreign key referencing the `Product` entity.
  - `quantity` (Integer): Number of products ordered.
  - `total_price` (Decimal): Total price for the order.
  - `created_at` (DateTime): The date and time when the order was created.

- **Indexes**:
  - `order_user_index`: Index on the `user_id` field for faster retrieval of user orders.

## Relationships

### User-Order Relationship

- **Type**: One-to-Many
- **Description**: A user can have multiple orders, but an order is associated with a single user.
- **Foreign Key**: `user_id` in the `Order` table references `id` in the `User` table.

### Product-Order Relationship

- **Type**: Many-to-Many
- **Description**: An order can contain multiple products, and a product can be in multiple orders.
- **Foreign Key**: `product_id` in the `Order` table references `id` in the `Product` table.

## Validation Rules

- **User Email**: Must be a valid email format and unique.
- **Product Price**: Must be a positive decimal number.
- **Order Quantity**: Must be a positive integer.

## Data Integrity Constraints

- **Foreign Key Constraints**: Ensure that `user_id` in `Order` references a valid `User` and `product_id` in `Order` references a valid `Product`.
- **Unique Constraints**: Ensure that `username` and `email` in `User` are unique.

## Example SQL Schema

```sql
CREATE TABLE users (
  id UUID PRIMARY KEY,
  username VARCHAR(50) UNIQUE NOT NULL,
  email VARCHAR(100) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE products (
  id UUID PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  description TEXT,
  price DECIMAL(10, 2) NOT NULL CHECK (price > 0),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE orders (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  product_id UUID REFERENCES products(id) ON DELETE CASCADE,
  quantity INTEGER NOT NULL CHECK (quantity > 0),
  total_price DECIMAL(10, 2) NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Best Practices

- Use appropriate data types and constraints to ensure data integrity.
- Regularly back up the database to prevent data loss.
- Optimize queries using indexing and denormalization when necessary.