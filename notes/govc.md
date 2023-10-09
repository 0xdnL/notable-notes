---
tags: [go]
title: govc
created: '2019-07-30T06:19:49.075Z'
modified: '2023-10-09T15:33:34.362Z'
---

# govc

> vSphere cli built on govmomi, the vSphere Go SDK - a robust inventory browser command

## install

```sh
go install github.com/vmware/govmomi/govc@latest
```

## env

```sh
GOVC_URL                    # URL of ESXi or vCenter instance to connect to user:pass@host
GOVC_USERNAME               # USERNAME to use if not specified in GOVC_URL
GOVC_PASSWORD               # PASSWORD to use if not specified in GOVC_URL
GOVC_TLS_CA_CERTS           # Override system root certificate authorities
GOVC_TLS_KNOWN_HOSTS        # File(s) for thumbprint based certificate verification
GOVC_TLS_HANDSHAKE_TIMEOUT  # Limits the time spent performing the TLS handshake
GOVC_INSECURE               # Disable certificate verification.
GOVC_DATACENTER
GOVC_DATASTORE
GOVC_NETWORK
GOVC_RESOURCE_POOL
GOVC_HOST
GOVC_GUEST_LOGIN            # guest credentials for guest operations
GOVC_VIM_NAMESPACE          # vim namespace defaults to urn:vim25
GOVC_VIM_VERSION            # vim version defaults to 6.0
GOVC_VI_JSON                # uses JSON transport instead of SOAP
```

## option

```sh
-u        # ESXi or vCenter URL e.g. user:pass@host
-debug    # trace requests and responses to ~/.govmomi/debug
```

## ls - list

```sh
govc ls -h
govc ls -l '*'
govc ls -l '/path to/host/'
govc ls datastore
govc ls -l -i "/path to/network"           # managed object IDs
govc ls -i -l -L "Network:network-42742"      # reverse search, supply the -L switch

# list ResourcePool 
govc ls -l 'host/*' | grep ResourcePool | awk '{print $1}' # | xargs -n1 -t govc pool.info

govc pool.info "/path to/host/someCluster02/Resources"
```

## host

```sh
govc host.info

govc host.service.ls

govc host.storage.info
 
govc datacenter.info                              
```

## datastore

```sh
govc datastore.ls -ds=datastore2 -l

govc find vm -type m -datastore $(govc find -i datastore -name datastore3)

for i in $(govc find vm -type m | grep -i "node" | cut -d/ -f2); do
  DATASTORE="$(govc vm.info -json "$i" | jq -r '.VirtualMachines[].Config.Hardware.Device[] | select(.DeviceInfo.Label=="CD/DVD drive 1" ) | .Backing.FileName')";
  printf "%s: %s" "$i" "$DATASTORE";
done
```

## vm - virtualmachine

```sh
govc vm.info -json ./vm/foo | jq '.VirtualMachines[]' | grep -o -E '10\.32\.[0-9]{1,3}\.[0-9]{1,3}';
govc vm.info -json ./vm/foo | jq '.VirtualMachines[].Guest.Net[] | .IpConfig | .IpAddress'
govc vm.info -json ./vm/foo | jq '.VirtualMachines[].Guest.Net[] | .IpAddress[0]'   # find vm and its ip
govc vm.info -json ./vm/foo | jq '.VirtualMachines[].Config.Hardware.Device[] | select(.Key== 2000) | .CapacityInBytes';

govc vm.power -off=true -vm.uuid=$UUID \&\& govc vm.power -on=true -vm.uuid=$UUID;  # restart vm
```

## tags

```sh
govc tags.ls

govc tags.attached.ls -r vm/foo.node.dev.domain.net
govc tags.attached.ls backup_daily2230_noQuiese

govc object.collect -json VirtualMachine:vm-365
```

## tasks

```sh
govc tasks -n=20 -f     # show current vsphere tasks
```

## metrics

```sh
govc metric.ls     ./vm/mq-1.node.dev.domain.net
govc metric.sample ./vm/mq-1.node.dev.domain.net cpu.usage.average
```

## snapshot

```sh
govc snapshot.tree -vm ./vm/mq-1.node.dev.domain.net -D -i -d
govc snapshot.create -vm ./vm/gitlab.node.dev.domain.net pre-gitlab-v12-upgrade
```

## find

```sh
govc find --help

govc find -type TYPE
# -type 
#  a    VirtualApp
#  c    ClusterComputeResource
#  d    Datacenter
#  f    Folder
#  g    DistributedVirtualPortgroup
#  h    HostSystem
#  m    VirtualMachine
#  n    Network
#  o    OpaqueNetwork
#  p    ResourcePool
#  r    ComputeResource
#  s    Datastore
#  w    DistributedVirtualSwitch

govc find -type m -name "*packer*"                                                # find vms which contain packer

govc find . -type m -guest.ipAddress "10.32.22.8" -runtime.powerState poweredOn   # find host by IP

govc find -type n | gxargs -d '\n' -I% govc object.collect -s % name              # find all network and get object-names

govc find -i -type h -name vhost11.foo.bar          # get managed-object-reference: "HostSystem:host-29240"

govc find -type m -host $(govc find -i -type h -name vhost11.foo.bar)

# -host can be the HostSystem name or inventory path.   
govc find . -type h -datastore $(govc find -i ./datastore -name iso_images)         # find hosts that have the datastore mounted using

# find all vms running linux
govc find . -type m -runtime.powerState poweredOn -guest.guestFamily linuxGuest

govc find . -type m -runtime.powerState poweredOn -guest.guestId '*Linux*'

govc find . -type m -runtime.powerState poweredOn -guest.guestId '*[ubuntu][Linux]*'
```

- [find with -guest.ipAddress argument returns more than one result](https://github.com/vmware/govmomi/issues/1089)

## see also

- [[jq]]
- [velenux.wordpress.com/automate-your-vcenter-interactions-from-the-linux-commandline-with-govmomi-and-govc](https://velenux.wordpress.com/2016/09/19/automate-your-vcenter-interactions-from-the-linux-commandline-with-govmomi-and-govc/)
- [Network info · Issue #742 · vmware/govmomi · GitHub](https://github.com/vmware/govmomi/issues/742)
- [datastore.upload broken pipe · Issue #832 · vmware/govmomi · GitHub](https://github.com/vmware/govmomi/issues/832)
- [pool.info command appears broken · Issue #203 · vmware/govmomi · GitHub](https://github.com/vmware/govmomi/issues/203#issuecomment-70699130)
