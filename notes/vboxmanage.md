---
tags: [virtualization]
title: vboxmanage
created: '2019-07-30T06:19:49.257Z'
modified: '2024-10-26T09:22:48.042Z'
---

# vboxmanage

> oracle virtualbox cli management interface

## install

download platform package at [virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

## list

```sh
vboxmanage list vms
vboxmanage list runningvms
vboxmanage list bridgedifs        # get ip of bridged box
vboxmanage list hostonlyifs
vboxmanage list dhcpservers
```

## usage

```sh
vboxmanage createvm --name VM_NAME --register

vboxmanage modifyvm VM_NAME --ostype VM_OSTYPE --cpus VM_CPUS --memory VM_MEM 
  --rtcuseutc on --acpi on --ioapic on --hpet on --hwvirtex on --vtxvpid on \
  TXUX_SUPPORT --largepages on --nestedpaging on --firmware bios  --bioslogofadein off \
  --bioslogofadeout off --bioslogodisplaytime 0 --biosbootmenu disabled --boot1 dvd0

vboxmanage guestproperty get "web" "/VirtualBox/GuestInfo/Net/0/V4/IP"    # returns the first IP of NIC likely to be NAT 10.0.*.*

vboxmanage guestproperty enumerate "web" | grep -i ip                     # return full list of all available IPs

vboxmanage startvm ubuntu-16.04-server-amd64 --type headless              # start vbox headless

vboxmanage controlvm ubuntu-16.04-server-amd64 poweroff
```

## find vm ip

```sh
vboxmanage showvminfo VMNAME | grep -i mac    # get vm mac address
nmap -sP 192.168.1.1/24 >/dev/null            # update arp-table
arp -a | grep -i 08:00:27:09:33:C0
```

[[arp]], [[nmap]]

## snapshot

```sh
vboxmanage snapshot vm04-zca8 take snap1-before-upgrade
vboxmanage showvminfo vm04-zca8
vboxmanage snapshot vm04-zca8 restore snap1-before-upgrade
vboxmanage snapshot vm04-zca8 delete snap1-before-upgrade
```

## see also

- [[vagrant]]
- [[pvesh]]
- [[qemu]], [[qm]]
- [[docker-machine]]
- [Create VirtualBox VM from cli](https://www.perkin.org.uk/posts/create-virtualbox-vm-from-the-command-line.html)
- [Chapter8 VBoxManage](https://www.virtualbox.org/manual/ch08.html)
- [dotfiles/boot2docker magicmonty/dotfiles](https://github.com/magicmonty/dotfiles/blob/master/bin/boot2docker)
- [VirtualBox snapshots using the CLI – Dirk-Jan's blog](http://www.vleeuwen.net/2012/12/virtualbox-snapshots-using-the-cli)
