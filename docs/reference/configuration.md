# Configuration Guide

This document provides detailed information on how to configure the application. It covers environment variables, configuration files, and best practices for managing settings in different environments.

## Table of Contents

1. [Overview](#overview)
2. [Environment Variables](#environment-variables)
   - [General Settings](#general-settings)
   - [Database Settings](#database-settings)
   - [Authentication Settings](#authentication-settings)
3. [Configuration File](#configuration-file)
   - [File Format](#file-format)
   - [Example Configuration](#example-configuration)
4. [Configuration Options](#configuration-options)
   - [Server Configuration](#server-configuration)
   - [Logging Configuration](#logging-configuration)
   - [Security Configuration](#security-configuration)
5. [Environment-Specific Configurations](#environment-specific-configurations)
6. [Best Practices](#best-practices)
7. [Common Issues](#common-issues)

## Overview

The application can be configured using environment variables and configuration files. This flexibility allows the application to be easily customized for different environments (development, staging, production) and deployment strategies.

## Environment Variables

The application uses environment variables to manage configuration settings. Below is a list of essential environment variables that must be set for the application to run correctly.

### General Settings

| Variable Name          | Description                               | Default Value  |
|------------------------|-------------------------------------------|----------------|
| `APP_ENV`              | The environment the app is running in     | `development`  |
| `APP_PORT`             | Port on which the server will run         | `3000`         |
| `APP_HOST`             | Host address for the server               | `localhost`    |

### Database Settings

| Variable Name          | Description                               | Default Value  |
|------------------------|-------------------------------------------|----------------|
| `DB_HOST`              | Database host address                     | `localhost`    |
| `DB_PORT`              | Port on which the database is running     | `5432`         |
| `DB_NAME`              | Name of the database                      | `app_db`       |
| `DB_USER`              | Database user                             | `user`         |
| `DB_PASSWORD`          | Database user password                    | `password`     |

### Authentication Settings

| Variable Name          | Description                               | Default Value  |
|------------------------|-------------------------------------------|----------------|
| `JWT_SECRET`           | Secret key for signing JWT tokens         | `your-secret`  |
| `TOKEN_EXPIRY`         | Expiry duration for authentication tokens | `3600` (seconds) |

## Configuration File

Apart from environment variables, the application can also be configured using a configuration file, typically in formats like YAML, JSON, or TOML.

### File Format

The configuration file should be placed in the root directory of the project and named `config.yml` (or another appropriate format). Below is an example of a configuration file in YAML format.

### Example Configuration

```yaml
server:
  host: "localhost"
  port: 3000

database:
  host: "localhost"
  port: 5432
  name: "app_db"
  user: "user"
  password: "password"

auth:
  jwt_secret: "your-secret"
  token_expiry: 3600
```

## Configuration Options

### Server Configuration

- `host`: The server's hostname or IP address.
- `port`: The port number the server listens to.

### Logging Configuration

- `log_level`: Defines the level of logging (e.g., `debug`, `info`, `warn`, `error`).
- `log_output`: The output destination for logs (e.g., stdout, file).

### Security Configuration

- `enable_https`: Boolean value to enable or disable HTTPS.
- `https_cert_file`: Path to the SSL certificate file.
- `https_key_file`: Path to the SSL key file.

## Environment-Specific Configurations

You can create different configuration files for different environments (e.g., `config.dev.yml`, `config.prod.yml`) and load the appropriate configuration based on the environment variable `APP_ENV`.

### Best Practices

- Keep sensitive data (e.g., database passwords, API keys) out of version control.
- Use environment variables to override settings in different environments.
- Validate configuration settings during application startup.

### Common Issues

- Missing Environment Variables: Ensure all required environment variables are set.
- Invalid Configuration File Format: Double-check the configuration file format for syntax errors.
- Port Conflicts: Ensure the port specified for the server is not already in use.