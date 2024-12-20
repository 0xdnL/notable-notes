---
tags: [linux, network]
title: telnet
created: '2019-07-30T06:19:49.252Z'
modified: '2024-10-09T10:10:20.595Z'
---

# telnet

> is a protocol and stands for "Teletype Network"

> user interface to the TELNET protocol
> a protocol of `internet protocol suite`/[[tcp-ip]]
> used to provide a bidirectional interactive text-oriented communication facility using a virtual terminal connection

## usage

```sh
## test email
telnet smtp.mydomain.com 25
    helo your_domain.com
    mail from:<test@your_domain.com>
    rcpt to:<to_email@your_domain.com>
    data
    From: test@your_domain.com
    Subject: test mail from command line

    this is test number 1
    sent from linux box
    .
```

```sh
telnet github.com 80

Trying 192.30.253.113...
Connected to github.com.
Escape character is '^]'.
GET / HTTP/1.1
Host: github.com
Connection: close

HTTP/1.1 301 Moved Permanently
Content-length: 0
Location: https://github.com/
Connection: close

Connection closed by foreign host.
```

## see also

- [[socat]], [[websocat]]
- [[nc]]
- [[curl]]
- [[tcp-ip]]
- [stackoverflow.com/check-if-smtp-is-working-from-commandline](https://stackoverflow.com/a/11988455)
