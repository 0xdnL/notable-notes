---
tags: [go]
title: go
created: '2019-07-30T06:19:49.075Z'
modified: '2025-11-10T14:58:54.115Z'
---

# go

> tool for managing `go` source code

## install

```sh
curl -O https://dl.google.com/go/go1.13.7.linux-amd64.tar.gz
tar xvzf go1.13.7.linux-amd64.tar.gz && mv go /usr/local/

curl -O https://go.dev/dl/go1.21.4.darwin-arm64.pkg
curl -O https://go.dev/dl/go1.24.10.darwin-amd64.pkg
installer -pkg ./go1.24.10.darwin-amd64.pkg -target /       # /usr/local/go/bin/go
```

[[installer]], [go.dev/dl/](https://go.dev/dl/)

## environment

```sh
GOROOT             # /usr/local/opt/go/libexec
GOTOOLDIR          # /usr/local/opt/go/libexec/pkg/tool/darwin_amd64
GOPATH             # go-workspace, places to look for code/packages; must be set to `go get`, `go build` and `go install`, `go env GOPATH`
GOBIN              # -
PKG_CONFIG         # pkg-config
GOCACHE            # /path/Caches/go-build
GOTMPDIR           # -
GOARCH             # amd64
GOOS               # darwin
GOHOSTARCH         # amd64
GOHOSTOS           # darwin
GCCGO              # gccgo
CC                 # clang
CXX                # clang++
CGO_ENABLED        # -
GOMOD              # -
GO11MODULE
```

## usage

```sh
go bug         # start a bug report

go clean       # remove object files and cached files
go doc         # show documentation for package or symbol

go fix         # update packages to use new APIs
go fmt         # gofmt (reformat) package sources
go generate    # generate Go files by processing source

go work        # workspace maintenance
go run         # compile and run Go program
go test        # test packages
go tool        # run specified go tool
go version     # print Go version
go vet         # report likely mistakes in packages
```

## build

> compile packages and dependencies

```sh
go build "./..."  # build all packages and commands in the current directory and all its subdirectories (recursively)
```

## env

> print Go environment information

```sh
go help env                   # more information about a command
go env                        # show current env vars go uses
go env GOCACHE                # print specific value
go env -json                  # print in json format
go env -w GO111MODULE=auto    # ..
```

## install

> compile and install packages and dependencies

```sh
go install -v golang.org/x/tools/gopls@latest
```

## mod

> module maintenance

```sh
go mod init REPO/hello        # creates a new module, initializing the `go.mod` that describes it
                              # `go build`, `go test` and other package-building commands add new dependencies to `go.mod`

go mod edit -replace example.com/greetings=../greetings     # rewrite path for local development

go mod tidy                   # remove unused dependencies
```

## list

> list packages or modules

```sh
go list -m all                        # lists the current module and all its dependencies
go list -m -versions rsc.io/sampler   # list available tagged versions of module
go list -m rsc.io/...                 # list current versions

go doc -all rsc.io/quote/v3                # get documentation
go doc io.Copy                             # print doc to Copy method of io package
go doc github.com/gorilla/mux ServeHTTP    # print doc from dependency

go clean -cache -modcache -i -r   # clear cache


go run

go test -json           # Convert test output to JSON suitable for automated processing

go clean -i github.com/motemen/gore...    # remove installed package
```

## get

> add dependencies to current module and install them
> downloads the packages named by import paths, along with dependencies. Then installs named packages like `go install`
> ⚠️ has been deprecated for installing binaries since `1.17`

```sh
-d      # stop after downloading the packages; that is, to not install packages
-fix    # run fix tool on the downloaded packages before resolving dependencies or building the code
-t      # also download packages required to build the tests for the specified packages
-u      # use network to update named packages and dependencies
-f      # forces -u not to verify that each package has been checked out from the source control repository implied by its import path. useful if source is local fork
-v      # enables verbose progress and debug output
```

```sh
go get -v github.com/user/repo    # install specific package

go get rsc.io/sampler@v1.3.1      # install with specific version, defaults to `@latest`

go get ./...                      # install all dependencies of project recursively
```

## see also

- [[language go]]
- [[go-template]]
- [[go datastructures]]
- [[c]], [[gcc]], [[make]]
- [[java]], [[javac]], [[mvn]]
- [[python]]
- [[wasm]]
- [[rust]]
- [[fmt]]
- [go-install-vs-go-build/](https://pocketgophers.com/go-install-vs-go-build/)
- [Does go get command do cache?](https://stackoverflow.com/a/52813009/2087704)
- [lecstor.com/go-clear-cache](https://lecstor.com/go-clear-cache/)
