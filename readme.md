# Knot Docker

> **IMPORTANT**  
> This is a community maintained repository, support is not guaranteed.

Docker container and compose setup to run a [Tangled](https://tangled.sh) knot
and host your own repository data.

## Building The Image

By default the `Dockerfile` will build the latest tag, but you can change it
with the `TAG` build argument.

```sh
docker build -t knot:latest --build-arg TAG=master .
```

The command above for example will build the latest commit on the `master`
branch.

<hr style="margin-bottom: 20px; margin-top: 10px" />

When using compose, it can be specified as a build argument which will be
passed to the builder.

```yaml
build:
  context: .
  args: { TAG: master }
```

This will for example tell docker to build it using the `master` branch like
the command.

## Setting Up The Image

The simplest way to set up your own knot is to use the provided compose file
and run the following:

```sh
export KNOT_SERVER_HOSTNAME=example.com
export KNOT_SERVER_SECRET=KNOT_TOKEN_HERE
export KNOT_SERVER_PORT=443
docker compose up -d
```

This will setup everything for you including a reverse proxy.

