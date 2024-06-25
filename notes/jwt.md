---
tags: [crypto]
title: jwt
created: '2020-01-27T08:04:24.079Z'
modified: '2024-06-20T09:17:56.706Z'
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

## see also

- [[jq]]
- [[openssl]]
- [jwt.io/introduction](https://jwt.io/introduction/)
- [github.com/emcrisostomo/jwt-cli](https://github.com/emcrisostomo/jwt-cli)
- [willhaley.com/blog/generate-jwt-with-bash](https://willhaley.com/blog/generate-jwt-with-bash/)
- [jvt.me/posts/2019/06/13/pretty-printing-jwt-openssl](https://www.jvt.me/posts/2019/06/13/pretty-printing-jwt-openssl/)
- [gist.github.com/rolandyoung/176dd310a6948e094be6](https://gist.github.com/rolandyoung/176dd310a6948e094be6)
- [github.com/Moodstocks/moodstocks-api-clients/blob/master/bash/base64url.sh](https://github.com/Moodstocks/moodstocks-api-clients/blob/master/bash/base64url.sh)
