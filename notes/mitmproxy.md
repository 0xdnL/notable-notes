---
title: mitmproxy
created: '2024-11-10T18:23:48.347Z'
modified: '2024-11-10T19:01:10.467Z'
---

# mitmproxy

>  set of tools that provide interactive, SSL/TLS-capable intercepting proxy for [[http⧸1]], [[http⧸2]], [[http⧸3]] and [[websockets]]

## install

```sh
brew install mitmproxy
```

## usage

```sh
mitmproxy   # start proxy on default port :8080

curl --proxy http://127.0.0.1:8080 "http://wttr.in/Dunedin?0"  # make req via proxy


# set web proxy in os to 127.0.0.1:8080 then visit http://mitm.it/
# download mitmproxy-ca-cert.pem and install in store
```

## HTTP/3

```sh
mitmproxy --mode reverse:https://http3.is

curl localhost:8080
```

[mitmproxy.org/posts/releases/mitmproxy-11/](https://mitmproxy.org/posts/releases/mitmproxy-11/)

## see also

- [[tcpdump]]
- [[wireshark]]
- [[curl]]
