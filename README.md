# WordPress Deployment with Docker Compose

This project provides a simple containerized setup for running WordPress with a MariaDB database using Docker Compose. It demonstrates how to configure services, environment variables, and persistent storage in a secure and reproducible way.

## Table of Contents

- Features
- Quickstart
- Installation
- Usage

## Features

- Two-container setup with WordPress and MariaDB
- Persistent database storage using Docker volumes
- Environment-based configuration
- No sensitive data stored in the repository
- Easy setup and execution with Docker Compose

## Quickstart

1. Clone the repository and navigate into the project directory.

2. Create a `.env` file from the default [`example.env`](./example.env):

```bash
cp example.env .env
```

3. Create and start the WordPress site:

```bash
docker compose up -d
```

4. Open WordPress site in browser:

```text
http://localhost:8080
```

## Installation

### Requirements

- Docker
- Docker Compose

### Environment Variables

Edit the `.env` file and set your values. Use [`example.env`](./example.env) as reference.

## Usage

### Check Status

```bash
docker compose ps
```

### Login

```text
http://localhost:8080/wp-login.php
```

### Create Admin User if Needed

```bash
docker compose exec wordpress bash -c "wp user create admin admin@example.com --role=administrator --user_pass='your_password' --path=/opt/bitnami/wordpress"
```

### Stop

```bash
docker compose down
```

## Notes

- `.env` is not committed to the repository
- Sensitive data is managed via environment variables
- Database data is stored in a Docker volume named `db_data`