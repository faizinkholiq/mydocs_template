# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- New feature: Added user authentication module.
- Documentation: Added a new section in the README on how to contribute.

### Changed
- Refactored the database layer to use a new ORM library.
- Updated the `INSTALL.md` file for better clarity.

### Deprecated
- The `old_auth` package is now deprecated and will be removed in future releases.

### Removed
- Removed support for Python 2.7.

### Fixed
- Fixed a bug where the app would crash on invalid input in the login form.
- Corrected typos in the error messages.

### Security
- Fixed a vulnerability in the user session management.

## [1.2.0] - 2024-09-10

### Added
- Implemented the new caching mechanism for faster response times.
- Added a new REST API endpoint `/api/v2/products`.

### Changed
- Changed the default timeout for database connections from 30s to 60s.

### Removed
- Removed the deprecated `/api/v1/orders` endpoint.

## [1.1.1] - 2024-08-15

### Fixed
- Fixed the issue where the server would not start on certain configurations.
- Fixed a minor UI bug in the settings page.

## [1.1.0] - 2024-07-25

### Added
- Added logging support with customizable log levels.
- Added support for PostgreSQL database.

### Changed
- Improved the performance of the data fetching logic.
- Modified the file structure for better modularity.

## [1.0.0] - 2024-06-01

### Added
- Initial release of the application.
- Basic user authentication and authorization.
- REST API endpoints for user management.