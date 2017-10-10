# Ghost Blogging Platform Docker Orchestration

## Install

    $ git clone https://github.com/avoinea/docker.deploy.ghost myblog.com
    $ cd myblog.com
    $ cp .env.example .env
    $ vim .env

## SSL certificates

* Obtain your SSL certificates from letsencrypt

      $ docker run --rm \
                   -p 80:80 \
                   -p 443:443 \
                   -v certs:/etc/letsencrypt \
               certbot/certbot certonly -d www.myblog.com --standalone -m my-email@myblog.com --agree-tos

* If you already have SSL certificates

      $ docker run -it --rm -v certs:/etc/letsencrypt -v /path/my/certs:/backup alpine sh
      $ mkdir -p /etc/letsencrypt/live/www.myblog.com/
      $ cd /backup
      $ cp cert.pem privkey.pem fullchain.pem /etc/letsencrypt/live/www.myblog.com/
      $ exit

## Run

    $ docker-compose pull
    $ docker-compose up -d

## Start blogging

* https://www.avoinea.com
