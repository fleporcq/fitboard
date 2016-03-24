# fitboard

## Docker

### Requirements

 - Install docker https://docs.docker.com/engine/installation/
 - Install docker-compose https://docs.docker.com/compose/install/

To launch the development server :

 - Copy `docker-compose.yml.dist` to `docker-compose.yml`
 - Run this commands from project directory :

```bash
# build images
docker-compose build
# launch containers
docker-composer up
```
Two containers are created `php-apache` and `mysql`.

Composer is installed in `php-apache` container.

To enter in bash mode in `php-apache` container.

```bash
docker exec -i -t [project_name]_php-apache_1 bash
```
