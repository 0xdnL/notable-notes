---
title: ipv4
created: '2024-11-16T07:55:05.755Z'
modified: '2024-11-16T08:04:08.508Z'
---

# ipv4

> [RFC-791: INTERNET PROTOCOL](https://www.rfc-editor.org/rfc/rfc791.html)

[[ipv6]], [[cidr]]

## Relation to Other Protocols

```
+------+ +-----+ +-----+     +-----+
|Telnet| | FTP | | TFTP| ... | ... |
+------+ +-----+ +-----+     +-----+
      |   |         |           |
     +-----+     +-----+     +-----+
     | TCP |     | UDP | ... | ... |
     +-----+     +-----+     +-----+
        |           |           |
     +--------------------------+----+
     |    Internet Protocol & ICMP   |
     +--------------------------+----+
                    |
       +---------------------------+
       |   Local Network Protocol  |
       +---------------------------+
```

## see also

- [[ip]]
