---
tags: [crypto]
title: jwt
created: '2020-01-27T08:04:24.079Z'
modified: '2026-01-27T21:55:15.076Z'
---

# jwt

> `json web tokens` - standard `RFC 7519` method for representing claims securely between two parties

## token

`jwt`'s consist of three parts separated by dots: `HEADER.PAYLOAD.SIGNATURE`

```
┌───────────────────────────────┬──────────────────────────────────────┐
│ HEADER:ALGORITHM & TOKEN TYPE │ {                                    │
│                               │   "alg": "HS256",                    │
│                               │   "typ": "JWT"                       │
│                               │ }                                    │
├───────────────────────────────┼──────────────────────────────────────┤
│ PAYLOAD:DATA                  │ {                                    │
│                               │  "iss": "https://foo.bar",           │
│                               │  "sub": "clxmzwm3f00002232wftzku2t", │
│                               │  "aud": [                            │
│                               │    "https://foo.bar"                 │
│                               │  ],                                  │
│                               │  "iat": 1718873804,                  │
│                               │  "exp": 1718960204                   │
│                               │ }                                    │
├───────────────────────────────┼──────────────────────────────────────┤
│ VERIFY SIGNATURE              │ HMACSHA256(                          │
│                               │   base64UrlEncode(header) + "." +    │
│                               │   base64UrlEncode(payload),          │
│                               │ ) secret base64 encoded              │
└───────────────────────────────┴──────────────────────────────────────┘
```

## usage

```sh
jq -R 'split(".") | .[1] | @base64d | fromjson' <<< "$TOKEN"    # decode to json

echo $JWT | jq -R 'split(".") | .[0:2] | map(@base64d) | map(fromjson)
[
  # HEADER:ALGORITHM & TOKEN TYPE
  {
    "alg": "HS256",
    "typ": "JWT"
  },
  # PAYLOAD:DATA
  {
    "iss": "https://admin.foo.bar",
    "sub": "clxmzwm3f00002232wftzku2t",
    "aud": [
      "https://admin.foo.bar"
    ],
    "iat": 1718873804,
    "exp": 1718960204
  }
  # VERIFY SIGNATURE ??
]
```

```sh
cat /var/run/secrets/kubernetes.io/serviceaccount/token | jq -R 'split(".") | .[0:2] | map(@base64d | fromjson)'
[
  {
    "alg": "RS256",
    "kid": "LPlu7Vmh6r7wA2Ie811IjjboQGrFOZP_K0VizyNJZ00"
  },
  {
    "aud": [
      "https://kubernetes.default.svc.cluster.local",
      "k3s"
    ],
    "exp": 1801086288,
    "iat": 1769550288,
    "iss": "https://kubernetes.default.svc.cluster.local",
    "jti": "af045bdc-bc07-4088-8651-7f97f3b43645",
    "kubernetes.io": {
      "namespace": "default",
      "node": {
        "name": "node-01",
        "uid": "5a1b3d58-8d00-424b-afcf-ad5a186244f9"
      },
      "pod": {
        "name": "attacker",
        "uid": "3cf56272-c608-4295-bc91-0746085606b9"
      },
      "serviceaccount": {
        "name": "attacker",
        "uid": "15cd50bb-b0f4-4707-917c-c2379127901b"
      },
      "warnafter": 1769553895
    },
    "nbf": 1769550288,
    "sub": "system:serviceaccount:default:attacker"
  }
]
```

## see also

- [[jq]]
- [[openssl]]
- [jwt.io/introduction](https://jwt.io/introduction/)
- [github.com/emcrisostomo/jwt-cli](https://github.com/emcrisostomo/jwt-cli)
- [willhaley.com/blog/generate-jwt-with-bash](https://willhaley.com/blog/generate-jwt-with-bash/)
- [jvt.me/posts/2019/06/13/pretty-printing-jwt-openssl](https://www.jvt.me/posts/2019/06/13/pretty-printing-jwt-openssl/)
- [gist.github.com/rolandyoung/176dd310a6948e094be6](https://gist.github.com/rolandyoung/176dd310a6948e094be6)
- [github.com/Moodstocks/moodstocks-api-clients/blob/master/bash/base64url.sh](https://github.com/Moodstocks/moodstocks-api-clients/blob/master/bash/base64url.sh)
