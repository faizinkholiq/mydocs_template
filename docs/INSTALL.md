# Installation Guide

This document provides instructions for installing and setting up the project. Follow the steps carefully to ensure a proper installation.

## Table of Contents

- [Installation Guide](#installation-guide)
  - [Table of Contents](#table-of-contents)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
    - [Step 1: Clone the Repository](#step-1-clone-the-repository)
    - [Step 2: Install Dependencies](#step-2-install-dependencies)
    - [Step 3: Configure Environment Variables](#step-3-configure-environment-variables)
    - [Step 4: Run Database Migrations](#step-4-run-database-migrations)
    - [Step 5: Start the Application](#step-5-start-the-application)
  - [Post-Installation](#post-installation)
  - [Troubleshooting](#troubleshooting)
  - [Uninstall](#uninstall)

---

## Prerequisites

Before installing the project, ensure that you have the following software installed on your system:

- **Operating System**: Linux, macOS, or Windows
- **Go**: Version 1.16 or later
- **PostgreSQL**: Version 12 or later
- **Git**: Version control system
- **Node.js and npm**: Required for building frontend assets
- **Docker** (optional): For containerized deployment

## Installation

### Step 1: Clone the Repository

Clone the project repository from GitHub to your local machine:

```bash
git clone https://github.com/yourusername/yourproject.git
cd yourproject
```

### Step 2: Install Dependencies

Ensure all required dependencies are installed:

For Go:
```bash
go mod tidy
```

For Node.js (if applicable):
```bash
npm install
```

### Step 3: Configure Environment Variables

Copy the .env.example file to .env and update the environment variables with your configuration:

```bash
cp .env.example .env
```

Edit the .env file and set the appropriate values:

  - DB_HOST: Database host (e.g., localhost)
  - DB_USER: Database user
  - DB_PASSWORD: Database password
  - APP_PORT: Port on which the app will run

### Step 4: Run Database Migrations

Run the database migrations to set up the required tables:

```bash
go run scripts/migrate.go
```

Or using a migration tool:

```bash
migrate -path ./migrations -database "postgres://user:password@localhost:5432/dbname?sslmode=disable" up
```

### Step 5: Start the Application

Start the application using the following command:

```bash
go run main.go
```

Or, if you're using Docker:

```bash
docker-compose up --build
```

Visit http://localhost:8080 in your browser to see the application running.

## Post-Installation

- Run Tests: Ensure everything is working correctly by running the tests.
    ``bash
    go test ./...
    ```

- Build Frontend Assets (if applicable):
    ```bash
    npm run build
    ```

## Troubleshooting

- Common Issues:
  - If you encounter a connection refused error, check if the database is running and accessible.
  - If dependencies fail to install, ensure that you have the correct versions of Go, Node.js, and other dependencies.

- Logs:
  - Check application logs for more details: `logs/app.log`
  - Check Docker logs (if using Docker): `docker logs <container_id>`

## Uninstall

To uninstall the project, follow these steps:

  1. Stop the Application:
    
    ```bash
    docker-compose down
    ```

    or, if running directly:

    ```bash
    kill $(lsof -t -i:8080)
    ```

  2. Remove the Database:

    ```bash
    dropdb your_database_name
    ```

  3. Delete the Project Directory:

    ```bash
    rm -rf yourproject
    ```