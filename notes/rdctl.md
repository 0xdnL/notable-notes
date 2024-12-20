---
tags: [container]
title: rdctl
created: '2023-11-08T14:10:55.947Z'
modified: '2024-11-16T05:27:28.971Z'
---

# rdctl

> rancher desktop ctl that provides container management and kubernetes 

uses [[lima]] on macos

## install

```sh
curl -LO https://github.com/rancher-sandbox/rancher-desktop/releases/download/v1.11.0/Rancher.Desktop-1.11.0.aarch64.dmg
curl -LO https://github.com/rancher-sandbox/rancher-desktop/releases/download/v1.16.0/Rancher.Desktop-1.16.0.aarch64.dmg

mkdir -p /tmp/rancher
hdiutil attach ~/Downloads/rancher.dmg -mountpoint /tmp/rancher
cp -rf /tmp/rancher/*.app /Applications
hdiutil detach  /tmp/rancher
rm -rf $HOME/Download/rancher.dmg
```

bundled with [[docker]], [[docker-buildx]], [[docker-compose]], [[helm]], [[kuberlr]], [[nerdctl]], [[spin]], [[trivy]]

[docs.rancherdesktop.io/references/bundled-utilities/](https://docs.rancherdesktop.io/references/bundled-utilities/)

## options

```sh
    --config-path string   # config file default: $HOME/Library/Application Support/rancher-desktop/rd-engine.json
-h, --help                 # help for rdctl
    --host string          # default is 127.0.0.1; most useful for WSL
    --password string      # overrides the password setting in the config file
    --port int             # overrides the port setting in the config file
    --user string          # overrides the user setting in the config file
    --verbose              # be verbose
```

## usage

```sh
rdctl completion     # Generate the autocompletion script for the specified shell
rdctl completion bash > $(brew --prefix)/etc/bash_completion.d/rdctl

rdctl api            # run API endpoints directly
rdctl create-profile # Generate a deployment profile in either macOS plist or Windows registry format
rdctl extension      # Manage extensions
rdctl factory-reset  # Clear all the Rancher Desktop state and shut it down.
rdctl help           # Help about any command

rdctl list-settings  # Lists the current settings.
rdctl list-settings | plutil -convert xml1 - -o ~/Library/Preferences/io.rancherdesktop.profile.defaults.plist

rdctl set            # Update selected fields in the Rancher Desktop UI and restart the backend.
rdctl shell          # Run an interactive shell or a command in a Rancher Desktop-managed VM
rdctl shutdown       # Shuts down the running Rancher Desktop application
rdctl snapshot       # Manage Rancher Desktop snapshots
rdctl start          # Start up Rancher Desktop, or update its settings.
rdctl version        # Shows the CLI version.
```

## see also

- [[plutil]]
- [[minikube]], [[kind]], [[k3d]]
- [[docker-credential-helpers]], [[docker-credential-ecr-login]],
