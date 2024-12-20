---
title: ipc
created: '2024-11-17T12:47:02.548Z'
modified: '2024-11-17T12:55:27.465Z'
---

# ipc

> inter process communication

[[unix socket]]


two methods of processes communication with each other

## (1) memory sharing

```sh
    +----+
    |    |
p1  |    | <- process 1 memory/address space
    |    |
    +----+
    |////| <- share memory space
    +----+
    |    |
p2  |    |
    |    |
    +----+
```

## (2) message passing

```sh
  +----+              +----+
  | p1 |-- Message -->| p1 |
  +----+              +----+
```

- via pipes
- via [[unix socket]]
- [[rpc]] "remove procedure call" ..gRPC

