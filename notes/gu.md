---
tags: [java]
title: gu
created: '2023-03-15T09:15:23.659Z'
modified: '2023-05-11T10:44:16.310Z'
---

# gu

> graalvm updater

## install

```sh
sdk install java 22.3.r19-grl
sdk use     java 22.3.r19-grl
```

## env

```sh
GRAALVM_HOME=$HOME/Development/graalvm/Contents/Home/
```

## option

```sh
-A, --auto-yes               # respond YES or ACCEPT to all questions
-c, --catalog                # treat parameters as component IDs from a catalog of GraalVM components. This is the default
-C, --custom-catalog <url>   # use user-supplied catalog at URL
-e, --debug                  # debugging. Prints stacktraces, ..
-E, --no-catalog-errors      # do not stop if at least one catalog is working
-h, --help                   # print help
-L, --local-file, --file     # treat parameters as local filenames of packaged components
-N, --non-interactive        # noninteractive mode. Fail when input is required
    --show-version           # print version information and continue
-u, --url                    # interpret parameters as URLs of packaged components
-v, --verbose                # be verbose. Print versions and dependency information
    --version                # print version
```

## usage

```sh
gu install native-image

gu install nodejs             # supports running Node.js applications

gu install llvm-toolchain

gu install wasm

native-image -cp bcprov-jdk15on-164.jar:. -H:ReflectionConfigurationFiles=reflection-config.json test
```

## see also

- [[sdk]]
- [[java]]
- [[mvn]]
- [[quarkus]]
- [[native-image]]
- [[graalvm]]
- [graalvm.org/22.0/docs/getting-started/](https://www.graalvm.org/22.0/docs/getting-started/)
