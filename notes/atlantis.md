---
tags: [iac]
title: atlantis
created: '2022-04-19T08:16:22.864Z'
modified: '2023-03-22T10:33:37.859Z'
---

# atlantis

> terraform pull request automation 

## usage

```sh
atlantis server \
  --atlantis-url="$URL" \
  --gh-user="$USERNAME" \
  --gh-token="$TOKEN" \
  --gh-webhook-secret="$SECRET" \
  --repo-allowlist="$REPO_ALLOWLIST"
```

## see also

- [[terraform]]
- [github.com/runatlantis/atlantis](https://github.com/runatlantis/atlantis)
