---
tags: [linux, virtualization]
title: qm
created: '2024-10-26T09:13:22.343Z'
modified: '2024-10-26T09:31:48.049Z'
---

# qm

> qm - [[qemu]]/[[kvm]] Virtual Machine Manager

## create a vm template for cloud-init

```sh
TEMPLATE_ID=5000

qm create ${TEMPLATE_ID} --memory 2048 --core 2 --name ubuntu-cloud --net0 virtio,bridge=vmbr0

qm importdisk ${TEMPLATE_ID} noble-server-cloudimg-amd64.img local-lvm

qm set ${TEMPLATE_ID} --scsihw virtio-scsi-pci --scsi0 local-lvm:vm-${TEMPLATE_ID}-disk-0

qm set ${TEMPLATE_ID} --ide2 local-lvm:cloudinit

qm set ${TEMPLATE_ID} --boot c --bootdisk scsi0

qm set ${TEMPLATE_ID} --serial0 socket --vga serial0

qm disk resize ${TEMPLATE_ID} scsi0 10G


qm clone ${TEMPLATE_ID} $(pvesh get /cluster/nextid)  --name "k3s-alpha"
qm start ${VM_ID}
```

## see also

- [[pvesh]]
- [[qemu]]
- [[vboxmanage]]
