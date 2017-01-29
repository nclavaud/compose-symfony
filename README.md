# compose-symfony

Run Symfony3 in seconds!

## Features

This Symfony boilerplate is orchestrated with `docker-compose` and features:
- Symfony 3.2
- nginx
- PHP-fpm 7.1
- PostgreSQL 9.6

## Quick start

```sh
# boot containers
docker-compose up -d

# browse website
xdg-open http://localhost

# run Symfony console
./console
```

### Map a different host port

By default, the web server will be mapped to host port `80`, but specifying another port is as easy as:

```
EXTERNAL_PORT=8000 docker-compose up -d
xdg-open http://localhost:8000
```
