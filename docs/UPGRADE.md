# Upgrade Guide

This document provides instructions and important notes for upgrading from one version to another. Follow the steps carefully to ensure a smooth transition.

## Table of Contents

- [Version 2.x to 3.x](#version-2x-to-3x)
  - [Breaking Changes](#breaking-changes)
  - [New Features](#new-features)
  - [Upgrade Steps](#upgrade-steps)
  - [Important Notes](#important-notes)
- [Version 1.x to 2.x](#version-1x-to-2x)
  - [Breaking Changes](#breaking-changes-1)
  - [New Features](#new-features-1)
  - [Upgrade Steps](#upgrade-steps-1)
  - [Important Notes](#important-notes-1)
- [General Notes](#general-notes)

---

## Version 2.x to 3.x

### Breaking Changes

- **Database Schema Changes**: The `users` table has been modified. You need to run the migration script provided in `migrations/3.0/upgrade.sql`.
- **Removed Deprecated Functions**: The following deprecated functions have been removed:
  - `getUserOld()`
  - `fetchDataLegacy()`
  - Replace these with `getUser()` and `fetchData()` respectively.

### New Features

- **OAuth2 Support**: Added support for OAuth2 for user authentication.
- **Improved Logging**: The logging system has been overhauled to provide more detailed output. Make sure to update your logging configuration in `config/logging.json`.

### Upgrade Steps

1. **Backup Your Database**: Before making any changes, ensure that you have a complete backup of your database.
2. **Run Migrations**: Execute the migration script:
```bash
psql -U username -d database_name -f migrations/3.0/upgrade.sql
```

3. **Update Configuration Files**: Review and update the configuration files according to the new settings.
    - config/app.yaml
    - config/logging.json

4. **Replace Removed Functions**: If you are using any of the deprecated functions in your code, replace them with the new ones.

### Important Notes

After upgrading, clear your cache to avoid conflicts with old settings:

```bash
redis-cli FLUSHALL
```

## Version 1.x to 2.x

### Breaking Changes

- **Configuration File Format Changed**: The `config.json` file has been replaced with `config.yaml`. You will need to manually convert your configuration to the new format.
- **Authentication System Overhaul**: The authentication system has been rewritten. Review the new authentication documentation here.

### New Features

- **GraphQL Support**: Introduced a GraphQL API endpoint `/graphql` for advanced querying.
- **WebSocket Enhancements**: Improved WebSocket handling for real-time applications.

### Upgrade Steps

1. **Convert Configuration File**: Migrate your config.json to the new config.yaml format.

2. **Update Dependencies**: Run the following command to update project dependencies:
```bash
go mod tidy
```

3. **Migrate Authentication**: Update your authentication code according to the new system.

### Important Notes

- Make sure to read the Authentication Migration Guide for detailed steps.

## General Notes

- **Deprecations**: Stay updated with the deprecated features listed in each release. Deprecated features will be removed in subsequent major releases.
- **Backup**: Always create backups of your database and important files before starting an upgrade process.
- **Testing**: It is strongly recommended to test the upgrade process in a development or staging environment before applying it to production.