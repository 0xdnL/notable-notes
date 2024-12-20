---
tags: [container, linux]
title: unix socket
created: '2019-08-20T09:22:26.742Z'
modified: '2024-11-17T13:03:34.723Z'
---

# unix socket

> allows communication between two different processes [[ipc]]
> on either the same machine or different machines in client-server application frameworks

a socket consist of three things:

1. an ip address
2. a transport protocol
3. a port number

- every unix systems i/o action is executed by writing/reading the descriptor file
- descriptor file is an open file, which is associated with an integer
  - It can be a network connection, text file, terminal or something else
  - It looks and behaves much like a low-level file descriptor
  - happens because the commands like read () and write () works with the same way they do with the files and pipes

## socket

- combination of IP-Address and Port-Number
- 2 types:
  - stream - reliable two-way connected communication streams
  - datagram

## see also

- [[ss]]
- [[nc]], [[socat]]
- [[netstat]]
- [[docker api]]
- [linux.com/news/what-socket](https://www.linux.com/news/what-socket)
- [[tcp-ip model]]
- [stackoverflow.com/what-is-the-difference-between-a-port-and-a-socket](https://stackoverflow.com/questions/152457/what-is-the-difference-between-a-port-and-a-socket)
