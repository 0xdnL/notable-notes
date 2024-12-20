---
tags: [container, rust, wasm]
title: spin
created: '2024-11-16T05:21:53.668Z'
modified: '2024-11-16T05:25:11.231Z'
---

# spin

> framework for building, deploying, and running fast, secure, and composable cloud microservices with [[wasm]]

## install

bundled with [[rdctl]]

## option

```sh
-h, --help       # Print help information
-V, --version    # Print version information
```

## usage

```sh
spin add          # Scaffold a new component into an existing application
spin build        # Build the Spin application
spin cloud *      # Commands for publishing applications to the Fermyon Cloud.
spin deploy       # Package and upload an application to the Fermyon Cloud.
spin doctor       # Detect and fix problems with Spin applications
spin help         # Print this message or the help of the given subcommand(s)
spin login        # Log into the Fermyon Cloud.
spin new          # Scaffold a new application based on a template
spin plugins      # Install/uninstall Spin plugins
spin registry     # Commands for working with OCI registries to distribute applications
spin templates    # Commands for working with WebAssembly component templates
spin up           # Start the Spin application
spin watch        # Build and run the Spin application, rebuilding and restarting it when files change
```

## see also

- [[wasm]]
- [[kubectl]]
