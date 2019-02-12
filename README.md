# Supported tags and respective `Dockerfile` links

- [`latest` (*Dockerfile*)](https://github.com/ivankomolin/docker-cron/blob/master/Dockerfile)

# How to use this images
Distinctive feature this image is that allows you to run commands from other containers

Example /path/to/crontab
```
# 
*	*	*	*	*	docker exec php php -v

```

Without build
```console
$ docker run --volume /path/to/crontab:/etc/crontabs/root --network host ivankomolin/cron
```

With build
```console
FROM ivankomolin/cron

COPY /path/to/crontab /etc/crontabs/root
```

Using docker-compose
```
version: '3.4'

services:
  cron:
    restart: always
    image: ivankomolin/cron
    volumes:
      - /path/to/crontab:/etc/crontabs/root
    network_mode: host
```