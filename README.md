# urban-waddle
> starter nginx server dockerized with SSL certificate 

## Installation

### Generate certificate :lock:
[https://www.sslforfree.com/](https://www.sslforfree.com/)

### Check server with file given by sslforfree

```bash
$ mkdir /home/urban-waddle/www/.well-known/pki-validation (if does not exist)
$ cp my-local/FXXXXXXX.txt /home/urban-waddle/www/.well-known/pki-validation/FXXXXXXX.txt
```

### Merge and add certificates to the project
```bash
$ cat certificate.crt ca_bundle.crt >> new-tmp-local-folder/certificate.crt
$ mkdir /home/urban-waddle/certs (if does not exist)
$ cp my-local/certificate.crt /home/urban-waddle/certs/certificate.crt
$ cp my-local/private.key /home/urban-waddle/certs/private.key
$ docker restart [container-id]
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

