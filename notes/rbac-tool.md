---
title: rbac-tool
created: '2024-10-20T11:33:47.796Z'
modified: '2024-10-20T13:32:00.585Z'
---

# rbac-tool

## install

```sh
# standalone
curl https://raw.githubusercontent.com/alcideio/rbac-tool/master/download.sh | bash

kubectl krew install rbac-tool
```

## usage

```sh
kubectl rbac-tool analysis --cluster-context CONTEXT |yq '.Findings[].Finding.Message'

rbac-tool who-can delete pods


kubectl rbac-tool policy-rules -e 'SERVICEACCOUNT_NAME'
```

## see also

- [[kubectl]], [[k9s]]
- [[rbac-lookup]]
- [[dot]]
