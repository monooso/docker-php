# PHP for Docker #
My standard Dockerfile for PHP development. Primarily concerned with [Laravel][laravel] projects, but seems to work just fine for other modern frameworks and CMSs (such as [Craft CMS][craft]).

[craft]: https://craftcms.com/
[laravel]: https://laravel.com/

Designed to be used in conjunction with [my Nginx Dockerfile][nginx].

[nginx]: https://github.com/monooso/docker-nginx

## Configuration ##

### Volumes ###
The image defines two volumes:

1. `/var/code`, which should contain your application code.
2. `/var/log`, which is where the container will write its log files.

Example usage:

```bash
docker run \
    -d \
    -v ~/code/myapp/code:/var/code \
    -v ~/code/myapp/logs:/var/log \
    monooso/docker-php:latest
```

## Docker for Mac ##
### xdebug ###
When running in Docker for Mac, xdebug cannot automatically determine the `remote_host` correctly. The solution is to pass a `XDEBUG_CONFIG` environment variable to the container, as follows:

```bash
docker run \
    -e XDEBUG_CONFIG="remote_host=docker.for.mac.localhost" \
    monooso/docker-php:latest
```

## Building and tagging ##
The Dockerfiles reference files from the `config` directory. This means you need to build the Docker images from the repository root. For example:

```bash
docker build -t monooso/docker-php:7.1 -f 7.1/Dockerfile .
```
