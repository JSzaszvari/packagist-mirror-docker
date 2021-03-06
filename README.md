[![Build Status](https://goo.gl/u9wbBD)](https://hub.docker.com/r/webysther/packagist-mirror/)

# Docker for Packagist Mirror

This project allows you to easily create and update a mirror of the packagist having as dependency only the docker.
It is possible to completely [customize the mirror](https://github.com/Webysther/packagist-mirror/blob/master/.env.example) only by using environment variable and thereby create an institutional mirror or for a particular country without any problem.

## Usage

Schedule in case of restart or another problem, the first execution create a mirror:

```bash
* * * * * root docker run --name mirror --rm -v /var/www/html:/public -e MAINTAINER_REPO='mymirror.com' webysther/packagist-mirror
```

You can add more mirrors with additional URL's separated by comma:

```bash
-e DATA_MIRROR='https://packagist.jp,https://packagist.com.br'
```

Main mirror is used to get providers and fallback in case of error on data mirror, you can also change them:

```bash
-e MAIN_MIRROR='https://packagist.com.br'
```

You also can change parallel connections for every mirror:

```bash
-e MAX_CONNECTIONS=10
```

All enviroment options stay on `.env` file.
