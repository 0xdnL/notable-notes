---
tags: [container, linux]
title: unix socket
created: '2019-08-20T09:22:26.742Z'
modified: '2023-03-22T10:10:46.245Z'
---

# unix socket

> allows communication between two different processes `IPC`
> on either the same machine or different machines in client-server application frameworks

- Every UNIX systems Input/Output action is executed by writing or reading the descriptor file
- Descriptor file is an open file, which is associated with an integer
  - It can be a network connection, text file, terminal or something else. 
  - It looks and behaves much like a low-level file descriptor. 
  - This happens because the commands like read () and write () works with the same way they do with the files and pipes.

## socket

- combination of IP-Address and Port-Number
- 2 types:
  - stream - reliable two-way connected communication streams
  - datagram

## see also

- [[nc]]
- [[ss]]
- [[socat]]
- [[netstat]]
- [[docker api]]
- [linux.com/news/what-socket](https://www.linux.com/news/what-socket)
- [[tcp-ip model]]
