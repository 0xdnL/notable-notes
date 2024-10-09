---
tags: [linux]
title: raid
created: '2024-10-07T14:42:05.942Z'
modified: '2024-10-08T09:23:35.120Z'
---

# raid

> redundant array of inexpensive disks - linux software RAID

```
Level   | Name            | Min. Disks  | Redundancy  | Growable
Linear  | JBOD            | 2           | No          | No
0       | Stripe          | 2           | No          | No
1       | Mirror          | 2           | Yes         | Yes
5       | RAID5           | 3           | Yes         | Yes
6       | RAID6           | 4           | Yes         | Yes
10      | Stripped Mirror | 4           | Yes         | No
```

[docs.openmediavault.org/en/stable/administration/storage/raid](https://docs.openmediavault.org/en/stable/administration/storage/raid.html)


## see also

- [[mdadm]]
- [raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)
