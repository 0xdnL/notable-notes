---
tags: [linux]
title: websocat
created: '2024-09-25T09:54:54.708Z'
modified: '2026-01-27T22:03:13.877Z'
---

# websocat

> [[nc]], [[curl]] and [[socat]] for [[websockets]]

## install

```sh
brew install websocat
```

## usage

```sh
websocat ws://HOST/ws

websocat -q -uU ws://HOST/ws    # check if connection works


websocat -s 1234
Listening on ws://127.0.0.1:1234/
ABC
123

websocat ws://127.0.0.1:1234/
ABC
123
```

## kubernetes

```sh
websocat --insecure \
  --header "Authorization: Bearer $TOKEN" \
  --protocol v4.channel.k8s.io \
  "wss://$NODE_IP:10250/exec/default/nginx/nginx?output=1&error=1&command=id"

websocat --insecure \
  --header "Authorization: Bearer $TOKEN" \
  --protocol v4.channel.k8s.io \
  "wss://$NODE_IP:10250/exec/default/nginx/nginx?output=1&error=1&command=cat&command=/etc/shadow"
```

## see also

- [[mitmproxy]]
- [[curl]]
- [[socat]]
- [[nghttp]]
- [github.com/vi/websocat](https://github.com/vi/websocat)
