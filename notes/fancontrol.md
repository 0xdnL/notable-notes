---
title: fancontrol
created: '2025-12-23T10:39:46.779Z'
modified: '2025-12-23T10:43:05.553Z'
---

# fancontrol

helios64, systemd

```sh
cat /etc/fancontrol

INTERVAL=10
#FCTEMPS=/dev/fan-p6/pwm1=/dev/thermal-cpu/temp1_input /dev/fan-p7/pwm1=/dev/thermal-cpu/temp1_input

FCTEMPS=/sys/devices/platform/p6-fan/hwmon/hwmon5/pwm1=/sys/class/thermal/thermal_zone0/temp /sys/devices/platform/p7-fan/hwmon/hwmon4/pwm1=/sys/class/thermal/thermal_zone1/temp

MINTEMP=/sys/devices/platform/p6-fan/hwmon/hwmon5/pwm1=40 /sys/devices/platform/p7-fan/hwmon/hwmon4/pwm1=40
MAXTEMP=/sys/devices/platform/p6-fan/hwmon/hwmon5/pwm1=110 /sys/devices/platform/p7-fan/hwmon/hwmon4/pwm1=110
MINSTART=/sys/devices/platform/p6-fan/hwmon/hwmon5/pwm1=60 /sys/devices/platform/p7-fan/hwmon/hwmon4/pwm1=60
MINSTOP=/sys/devices/platform/p6-fan/hwmon/hwmon5/pwm1=40 /sys/devices/platform/p7-fan/hwmon/hwmon4/pwm1=40

MINPWM=20
```


```sh
ls /sys/devices/platform/*-fan
/sys/devices/platform/p6-fan:
driver  driver_override  hwmon  modalias  of_node  power  subsystem  supplier:platform:ff420010.pwm  uevent

/sys/devices/platform/p7-fan:
driver  driver_override  hwmon  modalias  of_node  power  subsystem  supplier:platform:ff420000.pwm  uevent
```
