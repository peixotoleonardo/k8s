# Tools

- kubectl: cli for manager kubernetes
- kind: for create a locally cluster


## Commands

### Kind

#### Create a cluster

```sh
$ kind create cluster --config=kind.yml --name=k8s
```

> creates a kind cluster with k8s name and using kind.yaml configuration file

### Docker

#### Create an image

```sh
$ docker build -f .docker/Dockerfile -t k8s/hello-api .
```

- -f: specify the docker file
- -t: specify the name and optionally a tag

#### Run a container

```sh
$ docker run --rm -d -p 8000:8000 k8s/hello-api:latest
```

- --rm: automatically remove the when it exits
- -d: run the container in background
- -p: publish a container's ports to the host