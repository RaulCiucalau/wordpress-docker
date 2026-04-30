# WordPress Deployment with Docker Compose

## Table of Contents
- Description
- Features
- Quickstart
- Installation
- Usage

---

## Description

This project provides a simple containerized setup for running WordPress with a MariaDB database using Docker Compose.  
It demonstrates how to configure services, environment variables, and persistent storage in a secure and reproducible way.

---

## Features

- Two-container setup (WordPress + MariaDB)
- Persistent database storage using Docker volumes
- Environment-based configuration
- No sensitive data stored in the repository
- Easy setup and execution with Docker Compose

---

## Quickstart

```bash
cp .env.example .env
docker compose up -d
```

Open:

```
http://localhost:8080
```

---

## Installation

### Requirements

- Docker
- Docker Compose

### Setup

1. Clone the repository
2. Navigate into the project directory
3. Create a `.env` file:

```bash
cp .env.example .env
```

4. Edit `.env` and set your values:

```env
MARIADB_USER=your_user
MARIADB_PASSWORD=your_password
MARIADB_ROOT_PASSWORD=your_root_password
MARIADB_DATABASE=bitnami_wordpress

WORDPRESS_BLOG_NAME=My WordPress Site
WORDPRESS_PORT=8080
WORDPRESS_ENABLE_HTTPS=no
```

---

## Usage

### Start

```bash
docker compose up -d
```

### Status

```bash
docker compose ps
```

### Access

```
http://localhost:8080
```

### Login

```
http://localhost:8080/wp-login.php
```

### Create Admin User (if needed)

```bash
docker compose exec wordpress bash -c "wp user create admin admin@example.com --role=administrator --user_pass='your_password' --path=/opt/bitnami/wordpress"
```

### Stop

```bash
docker compose down
```

---

## Notes

- `.env` is not committed to the repository
- Sensitive data is managed via environment variables
- Database data is stored in a Docker volume (`db_data`)