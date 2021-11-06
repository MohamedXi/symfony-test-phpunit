KNP Taste
==============

This is the test of the KNP Taste application (Symfony 5.3)

# Installation

First, clone this repository:

```bash
$ git clone git@github.com:KnpLabs/knp-taste-ismael.git
```

Next, add `knptaste.local` in your `/etc/hosts` file.

Then, run:

```bash
$ docker-compose up -d --build
```

You are done, you can visit your Symfony application on the following URL: `http://knptaste.local` (and access Adminer on `http://knptaste.local:8090`)

# How it works?

Here are the `docker-compose` built images:

* `db`: This is the MySQL database container (can be changed to postgresql or whatever in `docker-compose.yml` file),
* `php`: This is the PHP-FPM container including the application volume mounted on,
* `nginx`: This is the Nginx webserver container in which php volumes are mounted too,
* `adminer`: This is the database management interface

This results in the following running containers:

```bash
> $ docker-compose ps
      Name                     Command               State                          Ports                       
----------------------------------------------------------------------------------------------------------------
knp_taste-adminer   entrypoint.sh docker-php-e ...   Up      0.0.0.0:8090->8080/tcp,:::8090->8080/tcp           
knp_taste-mysql     docker-entrypoint.sh --def ...   Up      0.0.0.0:3306->3306/tcp,:::3306->3306/tcp, 33060/tcp
knp_taste-nginx     /docker-entrypoint.sh nginx      Up      443/tcp, 0.0.0.0:80->80/tcp,:::80->80/tcp          
php-fpm             php-fpm8 -F                      Up      0.0.0.0:9000->9001/tcp,:::9000->9001/tcp 
```

# Environment Customizations

You can customize the exposed ports and other parameters changing the docker-compose .env file.

# Read logs

You can access Nginx and Symfony application logs in the following directories on your host machine:

* `logs/nginx`
* `logs/symfony`
