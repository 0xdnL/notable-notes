---
title: apachectl
created: '2024-11-26T08:12:33.429Z'
modified: '2024-11-26T08:13:00.606Z'
---

# apachectl

> control to apache..


```sh
apachectl configtest                # test config

/usr/local/apache/bin/apachectl configtest

apache2ctl -M                     # list loaded modules

apachectl -t -D DUMP_MODULES      # list loaded modules

ls /etc/apache2/mods-enabled/		  # list enabled modules
ls /etc/apache2/mods-available/		# list available modules
```

## see also

- [[apache2]]
- [[systemctl]]
