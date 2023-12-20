---
tags: [shell/bash/keyword]
title: bash until
created: '2019-07-30T06:19:49.023Z'
modified: '2023-11-28T07:50:53.905Z'
---

# bash until

> execute commands as long as a test does not succeed

## usage

```sh
until condition; do
  statements
done
```

## wait examples

```sh
until nc -z -v -w30 "$DB_HOST" "$DB_PORT"; do
  echo "Waiting for database connection..."
  sleep 2;
done

# wait for hostname to be resolvable
until ping -c1 ${HOSTNAME_FQDN} >/dev/null 2>&1; do
  echo "waiting for ${HOSTNAME_FQDN} to resolve ..";
  sleep 1;
done

# wait for all containres to shut down
until [ $(docker info --format '{{.ContainersRunning}}') -eq 0 ]; do
  sleep 1;
done

until pg_isready -U postgres -h HOST -p 5432 -d postgres; do 
  sleep 1;
done
```

## see also

- [[bash break]]
- [[bash test]]
- [[sleep]]
- [[bash while]]
- [[pg_isready]], [[docker]], [[ping]], [[nc]]
