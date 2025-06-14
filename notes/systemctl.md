---
tags: [initsystem, linux, systemd]
title: systemctl
created: '2019-07-30T06:19:49.250Z'
modified: '2025-04-28T05:52:50.459Z'
---

# systemctl

> query or send control commands to the [[systemd]] manager

## usage

```sh
systemctl --version
# systemd 219
# +PAM +AUDIT +SELINUX +IMA -APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 -SECCOMP +BLKID +ELFUTILS +KMOD +IDN

systemctl --failed            # list failed units

systemctl --type=service      # list current services

systemctl --state=running
```


```sh
systemctl list-units

systemctl list-units --all

systemctl list-units --all --state=inactive

systemctl list-units --type=service

systemctl list-unit-files --state=enabled

systemctl list-dependencies sshd.service


systemctl is-active application.service

systemctl is-enabled application.service

systemctl is-failed application.service
```

## Checking Unit Properties

```sh
systemctl show sshd.service             # get all properties

systemctl show unit.service --property=ActiveState

systemctl show -p FragmentPath k3s.service | cut -d'=' -f2      # get systemd service file


systemctl cat sshd.service              # cat unit-files fo service

systemctl edit --full sshd.service      # reload unit file after editing

systemctl daemon-reload


systemctl start unit.service

systemctl stop unit.service

systemctl restart unit.service

systemctl reboot


systemctl status unit.service

systemctl -l status service-name
    #   -l             # don't truncate entries with ellipses
    #   --no-pager     # can be added to avoid invoking a pager when the output is an interactive terminal. 

systemctl --output=json status docker-volume-netshare.service     
    # using output from `journalctl`
    # output: short, short-full, export, json, json-pretty, json-sse, json-seq, cat, with-unit
```

[[journalctl]]

## see also

- [[sudo]]
- [[sysctl]]
- [[apachectl]]
- [difference between service and systemctl? - serverfault.com](https://serverfault.com/questions/867322/what-is-the-difference-between-service-and-systemctl)
