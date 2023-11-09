---
title: rdctl
created: '2023-11-08T14:10:55.947Z'
modified: '2023-11-08T14:44:55.378Z'
---

# rdctl

> rancher desktop ctl that provides container management and kubernetes 

## install

```sh
curl -LO https://github.com/rancher-sandbox/rancher-desktop/releases/download/v1.11.0/Rancher.Desktop-1.11.0.aarch64.dmg # then use hdiutil and installer
```

package contains: [[helm]], [[kubectl]], [[nerdctl]], [[docker]]

## usage

```sh
rdctl list-settings 

rdctl list-settings | plutil -convert xml1 - -o ~/Library/Preferences/io.rancherdesktop.profile.defaults.plist
```

## see also

- [[k3d]]
- [[lima]]
- [[plutil]]
- [[minikube]]
