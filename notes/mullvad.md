---
title: mullvad
created: '2023-11-18T15:29:06.914Z'
modified: '2023-11-18T15:47:14.163Z'
---

# mullvad

> manage mullvad vpn daemon via a convenient cli


## install

```sh
curl -L https://mullvad.net/de/download/app/pkg/latest -o mullvad.pkg
sudo installer -pkg MullvadVPN-2023.5.pkg -target /
```

## usage

```sh
mullvad account                           # control and display information about your Mullvad account
mullvad account login 1234123412341234
mullvad account get
mullvad account list-devices

mullvad auto-connect   # control the daemon auto-connect setting

mullvad beta-program   # receive notifications about beta updates

mullvad lockdown-mode  # control whether to block network access when disconnected from VPN

mullvad dns            # configure DNS servers to use when connected

mullvad lan            # control the allow local network sharing setting

mullvad connect        # connect to a VPN relay

mullvad disconnect     # disconnect from the VPN

mullvad reconnect      # reconnect to any matching VPN relay

mullvad bridge         # manage use of bridges, socks proxies and Shadowsocks for OpenVPN. Can make OpenVPN tunnels use Shadowsocks via one of the Mullvad bridge servers. Can also make OpenVPN connect through any custom SOCKS5 proxy. These 
settings also affect how the app reaches the API over Shadowsocks

mullvad relay          # manage relay and tunnel constraints
mullvad relay list
mullvad relay update
mullvad relay set location se mma   # connect to server in sweden (se) and city malmö (mma)
mullvad relay set location se mma se-mma-wg-001
mullvad relay set hostname se-mma-wg-001


mullvad obfuscation    # manage use of obfuscation protocols for WireGuard. Can make WireGuard traffic look like something else on the network. Helps circumvent censorship and to establish a tunnel when on restricted networks

mullvad status         # return the state of the VPN tunnel

mullvad tunnel         # manage tunnel options

mullvad version        # show information about the current Mullvad version and available versions

mullvad factory-reset  # reset settings, caches, and logs

mullvad help           # print this message or the help of the given subcommand(s)
```

## see also

- [[wg]]
- [[mullvad-exclude]]
- [mullvad.net/de/help/how-use-mullvad-cli](https://mullvad.net/de/help/how-use-mullvad-cli)
