# urban-waddle
> basic nginx server dockerized with SSL certificate 

## Installation

### Generate certificate :lock:
[https://www.sslforfree.com/](https://www.sslforfree.com/)

### Check server with file given by sslforfree

```bash
$ mkdir www/.well-known/pki-validation
$ cp my-local/FXXXXXXX.txt www/.well-known/pki-validation/FXXXXXXX.txt
```

### Add certificate to the project
```bash
$ cat certificate.crt ca_bundle.crt certificate.crt > my-local/certificate.crt
$ mkdir certs
$ cp my-local/certificate.crt certs/certificate.crt
$ cp my-local/private.key certs/private.key
```

### Build docker image and launch server in daemon mode

```bash
$ docker-compose -f docker-compose.yml up --build -d
```

Your server is now accessible through [https://my-server](https://my-server) :rocket:

## Usage 

### To check everything is fine

#### Inside docker container
```bash
$ docker ps 
$ docker exec -it [container_id] /bin/bash
```

#### Docker logs
```bash
$ docker ps -a
$ docker logs [container_id]
```

