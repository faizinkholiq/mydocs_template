# Dependencies

This document lists all the external dependencies used in this project, including libraries, frameworks, tools, and services. It is important to keep this document up-to-date to ensure that all dependencies are managed correctly and any potential security vulnerabilities are addressed promptly.

## Table of Contents

- [Core Dependencies](#core-dependencies)
- [Development Dependencies](#development-dependencies)
- [Testing Dependencies](#testing-dependencies)
- [Build Tools](#build-tools)
- [External Services](#external-services)
- [Managing Dependencies](#managing-dependencies)
- [License Information](#license-information)

## Core Dependencies

These are the primary dependencies required for the application to function.

| Dependency | Version | Description                           | License   |
|------------|---------|---------------------------------------|-----------|
| Fiber      | v2.20.0 | A web framework for Go                | MIT       |
| PostgreSQL | 12.0    | Relational database                   | PostgreSQL|
| Redis      | 6.0     | In-memory data structure store        | BSD       |
| Go-JWT     | v3.2.0  | Library for handling JWT tokens in Go | MIT       |

## Development Dependencies

These dependencies are only required for development purposes, such as code formatting, linting, and hot-reloading.

| Dependency      | Version | Description                        | License |
|-----------------|---------|------------------------------------|---------|
| Air             | v1.29.0 | Live reload for Go apps            | MIT     |
| Go Lint         | v1.5.1  | Linter for Go source code          | MIT     |
| Mockery         | v2.10.1 | Mocking framework for testing      | MIT     |

## Testing Dependencies

Dependencies required for running tests and ensuring code quality.

| Dependency      | Version | Description                        | License |
|-----------------|---------|------------------------------------|---------|
| Testify         | v1.7.0  | Assertions and mocks for testing   | MIT     |
| GoMock          | v1.4.4  | Mocking framework for Go           | Apache 2.0|

## Build Tools

Tools used for building, packaging, and distributing the application.

| Tool        | Version | Description                          | License |
|-------------|---------|--------------------------------------|---------|
| Docker      | 20.10.8 | Containerization platform            | Apache 2.0 |
| Make        | 4.3     | Build automation tool                | GPL-3.0  |

## External Services

External services integrated with the project.

| Service   | Purpose                      | Description                                     |
|-----------|------------------------------|-------------------------------------------------|
| AWS S3    | Storage                      | Used for storing static files                   |
| Stripe    | Payment Processing           | Handles payment transactions                    |
| Auth0     | Authentication               | Manages user authentication and authorization   |

## Managing Dependencies

Dependencies are managed using [Go Modules](https://blog.golang.org/using-go-modules). To add a new dependency, run:

```bash
go get github.com/some/dependency
```

To update a dependency, use:

```bash
go get -u github.com/some/dependency
```

Make sure to run go mod tidy to clean up any unused dependencies.

## License Information

Make sure to review the licenses for all dependencies to ensure they are compatible with your project's licensing. You can typically find license information in the repository of each dependency or in the go.mod file.