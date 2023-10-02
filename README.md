**docker_laravel_apache_postgres**

## A Docker template

This repository provides a simple Docker setup to run a Laravel project with a PostgreSQL database and Apache web server.
The repository already contains an empty laravel project to simplify the project start a little bit more.
Nonetheless, I would recommend you run an update command before starting your project right away.

## The structure

The folder structure is quite self-explanatory. Please, check the `docker-compose.yml` for detailed information.
In broad strokes:
- The `apache` folder contains the virtual host configuration. It is mentioned in the `php/Dockerfile`.
- The `php` folder contains the definition which PHP version to pull. It uses a variation of the official PHP Docker image that is bundled with the Apache webserver.
- The `postgres-data` folder is going to contain the related data such that it is not lost when the container is shutdown or has to restart.
- The `src` folder contains the Laravel project. It is linked as working directory within the Apache configuration.

# Configuration

If you want to use the setup for production, I would recommend to adjust the configuration.
In specific take a look a the following files:
- `docker-compose.yml`
- `php/Dockerfile`
- `apache/default.conf`
- `src/.env` if you change the database config in `docker-compose.yml`

## Start it

To start run (from root directory)

```
docker-compose up -d --build
```

## Stop it

To stop run (from root directory)

```
docker-compose down
```

## Access the terminal

If you want to access the terminal on the webserver, run (from root directory)

```
docker-compose exec php-apache /bin/bash
```
Where `php-apache` is the name of the service defined with in the `docker-compose.yml`.


## Update the Laravel project

1. First open a terminal session with the above-mentioned command
2. Then simply run `composer update`


## Additional note

This repository is somewhat part of my learning to handle, configure and work with the Docker eco-system. If you find it helpful, you're welcome - star it, clone it, fork it or do nothing at all, up to you.
Anyway, Laravel has its own application to handle Docker images called **Laravel Sail**. Find more info about it [here](https://laravel.com/docs/sail).


## License

See LICENSE.md