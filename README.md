## Introduction
This is a Dockerfile to build a container image for [nginx](http://wiki.nginx.org/Main), [php-fpm](http://php-fpm.org/), [phalcon](https://phalconphp.com/en/), and [v8](https://code.google.com/p/v8/) (of all things). This Dockerfile uses the work of Richard Harvey in [https://github.com/ngineered/nginx-php-fpm](https://github.com/ngineered/nginx-php-fpm)

## Nginx Version
- Mainline Version (see [https://github.com/ngineered/nginx-php-fpm](https://github.com/ngineered/nginx-php-fpm))

## Phalcon Version
- **1.3.5**
- **latest**

## PHP Version
- **~5.5**

### Git repository
The source files for this project can be found here: [https://github.com/artburkart/nginx-php-fpm-phalcon-v8](https://github.com/artburkart/nginx-php-fpm-phalcon-v8)

If you have any improvements please submit a pull request.

### Docker hub repository
The Docker hub build can be found here: [https://registry.hub.docker.com/u/artburkart/nginx-php-fpm-phalcon-v8/](https://registry.hub.docker.com/u/artburkart/nginx-php-fpm-phalcon-v8/)

## Installation
Pull the image from the docker index rather than downloading the git repo. This prevents you having to build the image on every docker host.

```
docker pull artburkart/nginx-php-fpm-phalcon-v8
```

## Running
To run the container:

```
docker run --name v8_thing -p 8080:80 -d artburkart/nginx-php-fpm-phalcon-v8
```
You can then browse to http://\<docker_host\>:8080 to view the default install files.
### Volumes
If you want to link to your web site directory on the docker host to the container run:

```
docker run --name v8_thing -p 8080:80 -v /your_code_directory:/usr/share/nginx/html -d artburkart/nginx-php-fpm-phalcon-v8
```

## The folks at ngineered
built out a lot of cool features into the image I based this on. Check them out at [https://github.com/ngineered/nginx-php-fpm](https://github.com/ngineered/nginx-php-fpm).
