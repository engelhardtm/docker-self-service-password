# LDAP Tool Box Self Service Password with Docker

A lightweight Self Service Password Docker image built from source atop [Alpine Linux](https://store.docker.com/images/alpine).

Self Service Password is a PHP application that allows users to change their password in an LDAP directory. See http://ltb-project.org/wiki/documentation/self-service-password.

## How to use this image

The easiest way is to create your own configuration file and modify it according to your settings. Download the latest version of the `config.inc.php` file from https://github.com/ltb-project/self-service-password/tree/master/conf/config.inc.php.

```
$ docker run -d \
         -p 8080:80 \
         -v config.inc.php:/var/www/html/conf/config.inc.php \
         --name ltb \
         engelhardtm/docker-self-service-password:latest
```

For docker-compose use this snippet:
```
  ltb:
    image: engelhardtm/docker-self-service-password:latest
    container_name: ltb
    ports:
      - 8080:80
    volumes:
      - config.inc.php:/var/www/html/conf/config.inc.php
```


## Modify the image

You can build your own Image with your `config.inc.php` settings:

```
FROM engelhardtm/docker-self-service-password
COPY config.inc.php:/var/www/html/conf/config.inc.php
```

## Building the image yourself

```
git clone https://github.com/engelhardtm/docker-self-service-password.git
cd docker-self-service-password
docker build -t docker-self-service-password .
```

Don't forget to edit the configuration file `assets/config.inc.php`

## Documentation for LTB Self-Service-Password

Documentation is available on http://ltb-project.org/wiki/documentation/self-service-password