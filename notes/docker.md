---
tags: [container]
title: docker
created: '2019-07-30T06:19:49.045Z'
modified: '2025-12-19T09:37:27.091Z'
---

# docker

> self-sufficient runtime for containers

[[podman]], [[crictl]], [[nerdctl]] [[ctr]]

## install

```sh
brew install docker docker-compose

# when using the .dmg
brew install bash-completion  # prerquesite
ln -s /Applications/Docker.app/Contents/Resources/etc/docker.bash-completion $(brew --prefix)/etc/bash_completion.d/docker
ln -s /Applications/Docker.app/Contents/Resources/etc/docker-compose.bash-completion $(brew --prefix)/etc/bash_completion.d/docker-compose

curl -LO https://desktop.docker.com/mac/main/{arm64,amd64}/Docker.dmg
hdiutil attach Docker.dmg
/Volumes/Docker/Docker.app/Contents/MacOS/install
hdiutil detach /Volumes/Docker


colima start --network-address
docker context use colime
```

[[colima]]

## env

```sh
DOCKER_API_VERSION                # API version to use
DOCKER_BUILDKIT                   # enable or disable buildkit e.g. "failed to solve with frontend dockerfile.v0: failed to create LLB definition:.."
DOCKER_CONFIG                     # location of your client configuration
DOCKER_CERT_PATH                  # location of your authentication keys
DOCKER_CLI_EXPERIMENTAL           # enable experimental features for the cli (e.g. enabled or disabled)
DOCKER_DRIVER                     # graph driver to use
DOCKER_HOST                       # daemon socket to connect to
DOCKER_NOWARN_KERNEL_VERSION      # prevent warnings that your Linux kernel is unsuitable for Docker
DOCKER_RAMDISK                    # if set will disable ‘pivot_root’
DOCKER_STACK_ORCHESTRATOR         # Configure the default orchestrator to use when using docker stack management commands
DOCKER_TLS                        # when set docker uses TLS
DOCKER_TLS_VERIFY                 # when set docker uses TLS and verifies the remote
DOCKER_CONTENT_TRUST              # when set docker uses notary to sign and verify images. equates to --disable-content-trust=false for build, create, pull, push, run
DOCKER_CONTENT_TRUST_SERVER       # url of notary server to use. defaults to same URL as the registry
DOCKER_HIDE_LEGACY_COMMANDS       # when set docker hides legacy top-level commands (`docker rm`, `docker pull`, ..)
DOCKER_TMPDIR                     # location for temporary Docker files

# connect to docker host
export DOCKER_API_VERSION=1.38 DOCKER_TLS_VERIFY=1 DOCKER_CERT_PATH=/path/to/certs DOCKER_HOST=tcp://10.32.23.187:2376
```

## option

```sh
    --config string      # location of client config files (default "~/.docker")
-c, --context string     # name of context to use to connect to the daemon
-D, --debug              # enable debug mode
-H, --host list          # daemon socket to connect to
-l, --log-level string   # set logging level ("debug", "info", "warn", "error", "fatal") (default "info")
    --tls                # use TLS; implied by --tlsverify
    --tlscacert string   # trust certs signed only by this CA (default "~/.docker/ca.pem")
    --tlscert string     # path to TLS certificate file       (default "~/.docker/cert.pem")
    --tlskey string      # path to TLS key file               (default "~/.docker/key.pem")
    --tlsverify          # use TLS and verify the remote
-v, --version            # print version information and quit
```

## Common Commands

```sh
docker run         # Create and run a new container from an image
docker run --rm -ti ubuntu bash
docker run --rm -v $(pwd):$(pwd) -w $(pwd) IMAGE CMD                              # run CMD and place result in working dir
docker run --rm httpd:2.4-alpine htpasswd -nbB admin PASSWORD | cut -d ":" -f 2   # generate password and exit
docker run --rm -v $(pwd):/app -w /app -it --entrypoint="" node:25-alpine ash     # override entryponit
docker run -it
  -v /var/run/docker.sock:/var/run/docker.sock ubuntu:latest \       `# run docker from inside container`
  sh -c "apt-get update ; apt-get install docker.io -y ; bash"

docker run -d --shm-size=2gb IMAGE:TAG         # increase shared memory from 64M to 2G
docker run -d -v /dev/shm:/dev/shm IMAGE:TAG   # acces shared memory of host system
```

[[shm]], [[filsystem hierarchy standard]]

```sh
docker exec        # Execute a command in a running container
docker exec -it --env 'PS1=[CMD]\w \$ ' IMGAE CMD             # setting prompt for interactive use
docker exec -it --env 'PS1=['$ENV'] \s-\v\$ ' IMAGE CMD

docker ps          # List containers
docker ps --no-trunc     # wide view, full command
docker ps -a --no-trunc --filter name=^/foo$            # list container who's name is "/foo"

docker build       # Build an image from a Dockerfile
docker build BUILD_CONTEXT
docker build -t spilo:local --target ubuntu-18 .       # in multistage-build only build unto a target and exit

# build without a Dockerfile using
docker build -t example.com/test:latest - <<EOF
FROM busybox:latest
CMD ["echo", "just a test"]
EOF

docker bake        # Build from a file

docker pull        # Download an image from a registry
docke pull REGISTRY/IMAGE:TAG
docke pull REGISTRY/IMAGE@sha256:0afbf10990f3a9e4fbe8328740055ae86e531863b59307127ff2e531fa90b3bd

docker push        # Upload an image to a registry

docker images      # List images
docker images --format table

docker login       # Authenticate to a registry
docker login dhi.io     # docker hardened images
aws ecr get-login-password --region eu-central-1 | docker login --username AWS --password-stdin 123412341234.dkr.ecr.eu-central-1.amazonaws.com

docker logout      # Log out from a registry
docker search      # Search Docker Hub for images
docker version     # Show the Docker version information
docker info        # Display system-wide information
```

## Management Commands

```sh
docker ai*         # Docker AI Agent - Ask Gordon
docker builder     # Manage builds
docker buildx*     # Docker Buildx

docker compose*    # Docker Compose
docker compose -f compose.yaml up -d
docker compose --project-name this_dir ps
docker compose logs -f pgadmin
docker compose exec -it pgadmin bash
docker compose down -v --remove-orphans     # when seeing "Network db_default Resource is still in use"


docker container   # Manage containers
docker context     # Manage contexts
docker debug*      # Get a shell into any image or container
docker desktop*    # Docker Desktop commands
docker extension*  # Manages Docker extensions

docker image       # Manage images
docker image ls --filter label=org.opencontainers.image.vendor="Elastic"

docker init*       # Creates Docker-related starter files for your project
docker manifest    # Manage Docker image manifests and manifest lists
docker mcp*        # Docker MCP Plugin
docker network     # Manage networks
docker offload*    # Docker Offload
docker plugin      # Manage plugins
docker sandbox*    # Docker Sandbox
docker sbom*       # View the packaged-based Software Bill Of Materials (SBOM) for an image
docker scout*      # Docker Scout

docker system      # Manage Docker
docker system prune --all --volumes --force

docker volume      # Manage volumes
```

## Swarm Commands

```sh
docker swarm       # Manage Swarm
docker swarm update --task-history-limit=1        # swarm task-history

# (deprecated and/or docker machine ?)
docker node inspect $(docker node ls --format '{{.Hostname}}')| jq -r '.[].ManagerStatus.Addr'    # get node ip
```

## Commands

```sh
docker attach     # Attach local standard input, output, and error streams to a running container
docker commit     # Create a new image from a container's changes
docker cp         # Copy files/folders between a container and the local filesystem
docker create     # Create a new container
docker diff       # Inspect changes to files or directories on a container's filesystem
docker events     # Get real time events from the server
docker export     # Export a container's filesystem as a tar archive
docker history    # Show the history of an image
docker import     # Import the contents from a tarball to create a filesystem image

docker inspect    # Return low-level information on Docker objects
docker inspect 0                        # low level information about container
docker inspect CONTAINER_ID | jq '.[] | .Config .Image'
docker inspect --format '{{.State.Running}}' CONTAINER_ID    # container running
docker inspect --format '{{ index .Config.Labels "com.foo.bar" }}' foo   # index function: can lookup arbitrary strings in the map
docker inspect --format "{{.State.Status}}" CONTAINER_ID &>/dev/null

docker kill       # Kill one or more running containers
docker load       # Load an image from a tar archive or STDIN

docker logs       # Fetch the logs of a container
docker logs nginx 2>&1 | grep "127."    # debugging: grepping logs with 2>&1

docker pause      # Pause all processes within one or more containers
docker port       # List port mappings or a specific mapping for the container
docker rename     # Rename a container
docker restart    # Restart one or more containers
docker rm         # Remove one or more containers
docker rmi        # Remove one or more images
docker save       # Save one or more images to a tar archive (streamed to STDOUT by default)
docker start      # Start one or more stopped containers

docker stats      # Display a live stream of container(s) resource usage statistics
docker stats $(docker inspect -f '{{.Name}}' $(docker ps -q) | cut -c 2-)
docker stats $(docker ps --format={{.Names}})

docker stop       # Stop one or more running containers
docker tag        # Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
docker top        # Display the running processes of a container
docker unpause    # Unpause all processes within one or more containers
docker update     # Update configuration of one or more containers
docker wait       # Block until one or more containers stop, then print their exit codes
```

---

## network / docker overlay network

network namepsace / XVLAN / Netlink / distributed KV-Store ([[consul]])

```
┌─────────────┐              (VXLAN Tunnel Endpoint)
│ container ┌─┴────┐   ┌─────┐     ┌──────┐     ┌───────────────┐
└───────────┤ veth ├───┤ br0 ├─────┤ VTEP ├─────┤  vxlan tunnel │
            └──────┘   └─────┘     └──────┘     └───────────────┘
                   ┌───────────────────┘
VTEP encapsulates Frames by adding VXLAN-Header

  ┌────────────────┬──────────────┐
  │ Ethernet Frame │ VXLAN-Header │
  └────────────────┴──┬───────────┘
                      └─ VNID
```

`L3` segement routing IP (`network`), `L2` broadcast MAC (`Datalink`)

```sh
docker network inspect -f '{{range $container_id, $container_def := .Containers}} {{$container_id}}^{{index $container_def "Name"}} {{end}}'

docker network disconnect -f NETWORK CONTAINER

docker exec container ip addr show
docker exec container ip route

docker network create -d bridge --subnet 1.2.3.0/24 my_bridge   # create entwork and attach container
docker network create --driver bridge --subnet 192.168.100.0/24 --ip-range 192.168.100.0/24 my-bridge-network

docker run -itd --name c2 --net my_bridge busybox sh
docker run -itd --name c3 --net my_bridge --ip 20.10.0.254 busybox sh
docker run -itd --name c3 --net my_bridge --ip 10.23.6.33 busybox sh
docker run -d   --name c2 --net my_bridge -p 5000:80 nginx
docker run -itd --name c1 busyboy sh
docker run -itd --name c1-1 --network host busybox sh
```

[[ip]], [[brctl]], [[nat]], [[servicemesh]]

- [Docker Reference Architecture - success.docker.com](http://success.docker.com/article/networking)
- [Demystifying Docker overlay networking – nigelpoulton.com](http://blog.nigelpoulton.com/demystifying-docker-overlay-networking/)


## see also

- [[Dockerfile]]
- [[kubectl]]
- [[docker-compose]]
- [[minikube]]
- [[cosign]]
- [[hdiutil]], [[softwareupdate]]
- [[go-template]]
- [[12 factor app]]
- [stackoverflow.com/questions/42364695/how-to-clear-docker-task-history#](https://stackoverflow.com/questions/42364695/how-to-clear-docker-task-history#)
- [github.com/moby/moby/issues/31698#issuecomment-320294893](https://github.com/moby/moby/issues/31698#issuecomment-320294893)
- [docs.docker.com/engine/reference/commandline/cli/#environment-vairables](https://docs.docker.com/engine/reference/commandline/cli/#environment-vairables)
