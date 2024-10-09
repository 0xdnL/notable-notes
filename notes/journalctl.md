---
tags: [linux, systemd]
title: journalctl
created: '2019-08-19T09:11:28.583Z'
modified: '2024-06-26T05:18:41.460Z'
---

# journalctl

## option

## usage

```sh
journalctl -f                   # follow

journalctl -u ssh               # Show Logs for a systemd ServicePermalink

journalctl -k                   # View Kernel MessagesPermalink

journalctl -o json-pretty       # Change the Log Output FormatPermalink

journalctl --vacuum-size=2G     # Manually Clean Up Archived LogsPermalink


journalctl -xefu SERVICE
```

## see also

- [[k3s]]
- [[systemd]], [[systemctl]]
- [[syslog]]
- [Use journalctl to View Your System's Logs](https://www.linode.com/docs/quick-answers/linux/how-to-use-journalctl/)
- [systemd/man/journalctl](https://www.freedesktop.org/software/systemd/man/journalctl#-o)
