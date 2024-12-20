---
tags: [container]
title: docker
created: '2019-07-30T06:19:49.045Z'
modified: '2024-12-07T12:34:15.961Z'
---

# docker

> self-sufficient runtime for containers

[[podman]]

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

## run

> Create and run a new container from an image

```sh
docker run
```

## exec

> Execute a command in a running container

```sh
docker exec
```

## ps

> List containers

```sh
docker ps --no-trunc     # wide view, full command
```

## build

> Build an image from a Dockerfile

```sh
docker build BUILD_CONTEXT

docker build -t spilo:local --target ubuntu-18 .       # in multistage-build only build unto a target and exit
```

build without a Dockerfile using 

```sh
docker build -t example.com/test:latest - <<EOF
FROM busybox:latest
CMD ["echo", "just a test"]
EOF
```

[[Dockerfile]], [[heredoc]]

## pull

> Download an image from a registry

```sh
docker pull
```

## push

> Upload an image to a registry

```sh
docker push
```

## images

> List images

```sh
docker images
```

## login

> Log in to a registry

```sh
docker login
```

## logout

> Log out from a registry

```sh
docker logout
```

## search

> Search docker-hub for images

```sh
docker search
```

## version

> Show the Docker version information

```sh
docker version
```

## info

> Display system-wide information

```sh
docker info
```

```                                          
Management Commands:                                                                                                                                                              
  builder     Manage builds                                                                                                                                                       
  buildx*     Docker Buildx                                                              
  compose*    Docker Compose                                                             
  container   Manage containers                                                                                                                                                   
  context     Manage contexts                                                            
  debug*      Get a shell into any image or container                                                                                                                             
  desktop*    Docker Desktop commands (Alpha)                                                                                                                                     
  dev*        Docker Dev Environments                                                                                                                                             
  extension*  Manages Docker extensions                                                  
  feedback*   Provide feedback, right in your terminal!                      
  image       Manage images         
  init*       Creates Docker-related starter files for your project              
  manifest    Manage Docker image manifests and manifest lists
  network     Manage networks                                                            
  plugin      Manage plugins              
  sbom*       View the packaged-based Software Bill Of Materials (SBOM) for an image
  scout*      Docker Scout                                                               
  system      Manage Docker                                                              
  trust       Manage trust on Docker images                                              
  volume      Manage volumes               
                                                                                         
Swarm Commands:                                                                          
  swarm       Manage Swarm      
                                                                                         
Commands:                                  
  attach      Attach local standard input, output, and error streams to a running container                                                                                                                                                       
  commit      Create a new image from a container's changes                           
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container                                                     
  diff        Inspect changes to files or directories on a container's filesystem
  events      Get real time events from the server                 
  export      Export a container's filesystem as a tar archive
  history     Show the history of an image                                               
  import      Import the contents from a tarball to create a filesystem image
  inspect     Return low-level information on Docker objects                      
  kill        Kill one or more running containers                                                                        
  load        Load an image from a tar archive or STDIN                                                                  
  logs        Fetch the logs of a container                                                                                                                                       
  pause       Pause all processes within one or more containers                                                                                                                   
  port        List port mappings or a specific mapping for the container
  rename      Rename a container                                                                         
  restart     Restart one or more containers                                                                                                                                                                       
  rm          Remove one or more containers                                                              
  rmi         Remove one or more images                                                                                                                                                                            
  save        Save one or more images to a tar archive (streamed to STDOUT by default)                                                                                                                             
  start       Start one or more stopped containers                                                       
  stats       Display a live stream of container(s) resource usage statistics                            
  stop        Stop one or more running containers                                                        
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE                                                      
  top         Display the running processes of a container                                               
  unpause     Unpause all processes within one or more containers                                                        
  update      Update configuration of one or more containers                                             
  wait        Block until one or more containers stop, then print their exit codes  
```

-------------------

## login

> log in to a registry, if no server is specified, the default is defined by daemon

```sh
-p, --password string   # password
    --password-stdin    # password from stdin
-u, --username string   # username
```

```sh
aws ecr get-login-password --region region | docker login --username AWS --password-stdin AWS_ACCOUNT_ID.dkr.ecr.region.amazonaws.com
```

[[aws]]

## usage

```sh
docke pull REGISTRY/IMAGE:TAG
docke pull REGISTRY/IMAGE@sha256:0afbf10990f3a9e4fbe8328740055ae86e531863b59307127ff2e531fa90b3bd

docker system prune --all --volumes --force

docker exec -it --env 'PS1=[CMD]\w \$ ' IMGAE CMD             # setting prompt for interactive use
docker exec -it --env 'PS1=['$ENV'] \s-\v\$ ' IMAGE CMD

docker run --rm -v $(pwd):$(pwd) -w $(pwd) IMAGE CMD                              # run CMD and place result in working dir

docker run --rm httpd:2.4-alpine htpasswd -nbB admin PASSWORD | cut -d ":" -f 2   # generate password and exit

docker run -it -v /var/run/docker.sock:/var/run/docker.sock ubuntu:latest \       `# run docker from inside container`
  sh -c "apt-get update ; apt-get install docker.io -y ; bash"


# filter
docker ps -a --no-trunc --filter name=^/foo$            # list container who's name is "/foo"

docker image ls --filter label=org.opencontainers.image.vendor="Elastic"


docker logs nginx 2>&1 | grep "127."    # debugging: grepping logs with 2>&1

docker events

docker swarm update --task-history-limit=1        # swarm task-history

docker node inspect $(docker node ls --format '{{.Hostname}}')| jq -r '.[].ManagerStatus.Addr'    # get node ip
```

## inspect

```sh
docker inspect 0                        # low level information about container

docker inspect CONTAINER_ID | jq '.[] | .Config .Image'

docker inspect --format '{{.State.Running}}' CONTAINER_ID    # container running

docker inspect --format '{{ index .Config.Labels "com.foo.bar" }}' foo   # index function: can lookup arbitrary strings in the map

docker inspect --format "{{.State.Status}}" CONTAINER_ID &>/dev/null
```

## stats

```sh
docker stats $(docker inspect -f '{{.Name}}' $(docker ps -q) | cut -c 2-)

docker stats $(docker ps --format={{.Names}})
```

## network / docker overlay network

- network namepsace
- XVLAN
- Netlink
- distributed KV-Store (consul)

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

docker exec container ip addr show    # debugging inside container
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

- [[podman]], [[crictl]], [[nerdctl]] [[ctr]]
- [[Dockerfile]]
- [[brew]]
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
