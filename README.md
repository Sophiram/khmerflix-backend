# Movie App API

The backend for the movie application is built with Spring Boot and provides the REST API, authentication integration, media storage support, and admin services used by the frontend.

## Stack

- Java 25 toolchain
- Spring Boot 4.1.1
- Spring Web
- Spring Data JPA
- Spring Security
- Keycloak integration
- PostgreSQL
- MinIO
- Flyway
- SpringDoc OpenAPI / Swagger UI

## Prerequisites

- Java 25
- Gradle wrapper included in the project
- Docker Desktop or a local equivalent for PostgreSQL, MinIO, and Keycloak
- Database and service ports exposed as defined in the environment file

## Installation

From the backend directory:

```bash
./gradlew build
```

## Run with Docker services

The project includes Docker Compose for local infrastructure:

```bash
docker-compose up -d
```

This starts:

- PostgreSQL
- MinIO
- Keycloak

## Run the application

```bash
./gradlew bootRun
```

The API is served on:

- http://localhost:8081

## Environment variables

The backend expects configuration values such as:

```env
SERVER_PORT=8081
DB_PORT=5433
DB_NAME=movie_db
DB_USERNAME=postgres
DB_PASSWORD=123
KEYCLOAK_PORT=8080
KEYCLOAK_REALM=movie-app-realm
KEYCLOAK_CLIENT_ID=movie-app-client
KEYCLOAK_CLIENT_SECRET=your_client_secret
MINIO_URL=http://localhost:9000
MINIO_ACCESS_KEY=minioadmin
MINIO_SECRET_KEY=minioadmin
MAIL_HOST=smtp.gmail.com
MAIL_USERNAME=your_email
MAIL_PASSWORD=your_app_password
```

## API docs

Swagger UI is available at:

```text
http://localhost:8081/swagger-ui.html
```

OpenAPI JSON is available at:

```text
http://localhost:8081/v3/api-docs
```

## Project structure

- `src/main/java` — application source code
- `src/main/resources` — configuration files, YAML properties, static resources
- `src/test/java` — backend tests
- `docker-compose.yml` — local dependency services
- `build.gradle` — Gradle configuration and dependencies

## Notes

- Flyway is enabled for database migrations.
- JWT validation is configured against Keycloak.
- MinIO is used for media object storage.
- The app uses PostgreSQL as the primary relational database.
