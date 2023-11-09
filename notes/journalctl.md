---
tags: [linux, systemd]
title: journalctl
created: '2019-08-19T09:11:28.583Z'
modified: '2023-10-14T09:28:48.586Z'
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
- [[systemctl]]
- [[syslog]]
- [Use journalctl to View Your System's Logs](https://www.linode.com/docs/quick-answers/linux/how-to-use-journalctl/)
- [systemd/man/journalctl](https://www.freedesktop.org/software/systemd/man/journalctl#-o)
