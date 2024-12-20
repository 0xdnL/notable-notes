---
title: ab
created: '2024-10-09T16:53:36.162Z'
modified: '2024-11-26T08:15:14.612Z'
---

# ab

> apache benachmark - [[http]] server benchmarking tool

## usage

```sh
# perform 1000 requests, 10 at a time (which approximately simulates 10 concurrent users getting 100 pages each 
ab -n 1000 -c 10 -k -H "Accept-Encoding: gzip, deflate" http://www.example.com/
```

## see also

- [[curl]]
- [[apache2]], [[apachectl]]
