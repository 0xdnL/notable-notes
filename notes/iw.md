---
title: iw
created: '2025-12-19T12:36:24.945Z'
modified: '2025-12-19T12:50:37.555Z'
---

# iw

> show and manipulate wireless devices

[[iwconfig]], [[ethtool]]

## installation

```sh
apt-get install iw
apk add iw

docker run cmd.cat/iw iw
```

## usage

```sh
iw dev wlan0 link

iw dev wlp2s0 link

#    0 dBm = 1 mW, every +10 dB = 10× power; every −10 dB = 1/10 power
#    dBm values for Wi‑Fi are usually negative because received power is much less than 1 mW
# typical wifi approximate receive levels
#    −30 to −50 dBm — Excellent    (very strong, close to AP)
#    −50 to −60 dBm — Very good    (reliable, high throughput)
#    −60 to −70 dBm — Good to fair (usable, may see reduced speeds)
#    −70 to −80 dBm — Weak         (slow, higher error rates)
#         < −80 dBm — Very poor    (likely unusable or frequent disconnects)
```

```sh
# shows device capabilities:
# - supported bands
# - channel widths (20/40/80/160)
# - number of spatial streams (RX/TX chains)
# - HE/ VHT/HT support — which set the max theoretical PHY rate
iw phy phy0 info
iw list
```

## see also

- [[ifconfig]]
