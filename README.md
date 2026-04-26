# wordpress-docker

## Table of Contents
- Description
- Features
- Quickstart
- Installation
- Usage

---

## Description

This project provides a minimal Docker Compose setup for running WordPress with a MariaDB database.  
The configuration follows best practices regarding security, environment variables, and persistence.

---

## Features

- WordPress and MariaDB run in separate containers
- Persistent database storage using Docker volumes
- Configuration via environment variables
- No sensitive data stored in the repository
- Simple and reproducible setup

---

## Quickstart

```bash
cp .env.example .env
docker compose up -d
```

Open in browser:

```
http://localhost:8080
```

---

## Installation

### Requirements

- Docker
- Docker Compose

### Setup

Clone the repository and navigate into the project directory.

Create a local `.env` file based on the template:

```bash
cp .env.example .env
```

Edit the `.env` file and provide your own values:

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

### Start services

```bash
docker compose up -d
```

### Check status

```bash
docker compose ps
```

### Access WordPress

```
http://localhost:8080
```

### Login

```
http://localhost:8080/wp-login.php
```

If no administrator user exists, create one using:

```bash
docker compose exec wordpress bash -c "wp user create admin admin@example.com --role=administrator --user_pass='your_password' --path=/opt/bitnami/wordpress"
```

### Stop services

```bash
docker compose down
```

---

## Notes

- The `.env` file is not committed to the repository
- All sensitive configuration is handled via environment variables
- Database data is stored persistently in a Docker volume