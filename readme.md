# Knot Docker

> **IMPORTANT**  
> This is a community maintained repository, support is not guaranteed.

Docker container and compose setup to run a [Tangled](https://tangled.sh) knot and host your own data.

## Simple Setup

If you want an easy way to spin up a knot, you can simply run the following
with docker installed:

```console
$ docker compose up -d
```

This will setup the knot server, as well as caddy to expose the front-end.

## Bring Your Own Setup

If you have your own compose setup already, you will just need point your web
server to the knot's HTTP port (namely `5555`), you can do this with docker by
setting another container to `depends_on` it and then pointing it to the name
of the container with the port. For example, with a very basic caddy webserver
container:

```
caddy reverse-proxy --from ${KNOT_SERVER_HOSTNAME} --to knot:5555
```

This will for example point caddy to the port on the knot container.

