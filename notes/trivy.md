---
title: trivy
created: '2024-12-04T14:30:58.799Z'
modified: '2024-12-04T14:35:04.470Z'
---

# trivy

> scanner for vulnerabilities in container images, file systems, and Git repositories, as well as for configuration issues and hard-coded secrets

## option

```sh
    --cache-dir string          # cache directory (default "/root/.cache/trivy")
-c, --config string             # config path (default "trivy.yaml")
-d, --debug                     # debug mode
-f, --format string             # version format (json)
    --generate-default-config   # write the default config to trivy-default.yaml
-h, --help                      # help for trivy
    --insecure                  # allow insecure server connections
-q, --quiet                     # suppress progress bar and log output
    --timeout duration          # timeout (default 5m0s)
-v, --version                   # show version
```

## env

```sh

```

## usage

```sh
trivy image python:3.4-alpine     # Scan a container image
trivy image --input ruby-3.1.tar  # Scan a container image from a tar archive
trivy fs .                        # Scan local filesystem
trivy server                      # Run in server mode
```

## Scanning Commands

```sh
trivy config        # Scan config files for misconfigurations
trivy filesystem    # Scan local filesystem
trivy image         # Scan a container image
trivy kubernetes    # [EXPERIMENTAL] Scan kubernetes cluster
trivy repository    # Scan a repository
trivy rootfs        # Scan rootfs
trivy sbom          # Scan SBOM for vulnerabilities and licenses
trivy vm            # [EXPERIMENTAL] Scan a virtual machine image
```

## Management Commands

```sh
trivy module      # Manage modules
trivy plugin      # Manage plugins
trivy vex         # [EXPERIMENTAL] VEX utilities
```

## Utility Commands

```sh
tivy clean        # Remove cached files
tivy completion   # Generate the autocompletion script for the specified shell
tivy convert      # Convert Trivy JSON report into a different format
tivy help         # Help about any command
tivy registry     # Manage registry authentication
tivy server       # Server mode
tivy version      # Print the version
```

## see also

- [[kubectl]]
- [[docker]]
- [[glab]]
