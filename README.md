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
