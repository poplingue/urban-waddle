# urban-waddle
> starter nginx server dockerized with SSL certificate 

## Installation

### Generate certificate :lock:
[https://www.sslforfree.com/](https://www.sslforfree.com/)

### Auth File given by sslforfree on your server

```bash
$ mkdir /home/urban-waddle/www/.well-known/pki-validation (if does not exist)
$ scp my-local/FXXXXXXX.txt /home/urban-waddle/www/.well-known/pki-validation/FXXXXXXX.txt
```

### Merge and add certificates to the project
```bash
$ mkdir new-local-folder
$ cat my-local/certificate.crt ca_bundle.crt >> new-local-folder/certificate.crt
$ mkdir /home/urban-waddle/certs (if does not exist)
$ scp new-local-folder/certificate.crt user@server_name/home/urban-waddle/certs/certificate.crt
$ scp my-local/private.key user@server_name/home/urban-waddle/certs/private.key
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

