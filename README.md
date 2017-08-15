# compose-symfony

Run Symfony3 in seconds!

## Features

This Symfony starter-kit is bundled with:
- Symfony 3
- nginx
- PHP-fpm 7.1
- PostgreSQL 9.6
- composer
- MailCatcher

Each service runs in a dedicated container, and the whole thing is orchestrated with `docker-compose`.

## Requirements

You need [Docker Engine](https://docs.docker.com/engine/) and [Docker Compose](https://docs.docker.com/compose/) installed on your machine.

## Quick start

```sh
# boot containers
docker-compose up -d

# browse website
xdg-open http://localhost

# watch emails sent in MailCatcher
xdg-open http://localhost:81

# run Symfony console
./console

# connect to PostgreSQL
./psql
```

### Map a different host port

By default, the web server will be mapped to host port `80`, but specifying another port is as easy as:

```
EXTERNAL_PORT=8000 docker-compose up -d
xdg-open http://localhost:8000
```

### Map a different host port for MailCatcher

By default, MailCatcher web interface will be mapped to host port `81`. Change with:
```
EXTERNAL_MAILCATCHER_PORT=8001 docker-compose up -d
xdg-open http://localhost:8001
```
