# vagrant-docker-graylog

Vagrant environment with Docker and Docker Compose installed running [Graylog](https://www.graylog.org/) containers.

## Starting the vagrant box:

```bash
vagrant up
```

You have to wait some time until the Graylog server is up and running. The dashboard is accessable at [http://localhost:9000](http://localhost:9000). You `admin/admin` to log in.

Configure an input with port `12201`. This port is forwarded in the default config.

## Watch running containers

Connect into the vagrant box with

```bash
vagrant ssh
```

After that navigate into `/vagrant`. Then issue the command

```bash
sudo docker ps
```

or

```bash
sudo docker-compose ps
```