---
title: wg
created: '2023-11-18T15:47:17.914Z'
modified: '2023-11-18T16:01:13.375Z'
---

# wg

> set and retrieve configuration of wireguard interfaces

WireGuard securely encapsulates IP packets over UDP mimicing the model of [[ssh]] and Mosh; 
both parties have each other's public keys, and then they're simply able to begin exchanging packets through the interface.

## install

```sh
brew install wireguard-tools
```

## usage

```sh
wg genkey > privat
wg pubkey < private

ip link add wg0 type wireguard
ip addr add 10.0.0.1/24 dev wg0
wg set wg0 private-key ./private
ip link set wg0 up

wg set wg0 peer PUBLICKEY allowed-ips 10.0.0.2/32 endpoint 192.168.1.2:51820
```

## see also


OpenVPN

- [[ip]]
- [[ifconfig]]
- [[mullvad]]
- [wireguard.com/quickstart/](https://www.wireguard.com/quickstart/)
