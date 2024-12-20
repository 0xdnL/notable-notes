---
tags: [json, linux]
title: jq
created: '2019-07-30T06:19:49.141Z'
modified: '2024-12-05T08:44:49.205Z'
---

# jq

> cli json processor - transforms json, by selecting, iterating, reducing and otherwise mangling json documents

## install

```sh
brew install jq
```

## option

```sh
-c, --compact-output    # compact to single line,1 no pretty print
-r, --raw-output        # output no quotes
-R, --raw-input         # don't parse the input as json. Instead, each line of text is passed to the filter as a string
--unbuffered            # if you're piping a slow data source into jq and piping jq's output elsewhere
-n, --null-input        # Don't read any input at all! useful when using jq as a simple calculator or to construct json data from scratch
-S, --sort-keys         # output fields of each object with the keys in sorted order
```

## usage

```sh
echo '[1, "foo", ["foo"]]' | jq '. | tostring'      # `tojson` `fromjson`

echo '[1, "foo", ["foo"]]' | jq '. | tojson'

echo '"[1,\"foo\",[\"foo\"]]"' | jq '. | fromjson'

diff <(jq -S . FILE_A.json) <(jq -S . FILE_A.json)    # diff by sorting first
```

## string interpolation

```sh
STDOUT | jq '.[]| "\(.id) \(.name)"'  # print in one line

jq -n -r '["abc","def"] | "\(.[0]) \(.[1])"'


STDOUT | jq -r '.auths | keys[]'   # get only keys from auths{} object
```

## select - get a object based on object's value

```sh
jq '.VirtualMachines[].Config.Hardware.Device[] | select(.Key== 2000) | .CapacityInBytes'

jq '.QueueUrls[] | select(endswith("STRING"))'              # get array-elemnts ending with "STRING"

jq '.fields | select(.some | tonumber > 0) | .some)'        # convert string from .some `tonumber` then get if greater zero
```

## filter values

```sh
STDOUT | jq --unbuffered 'map(del(.database, .id, .isDefault, .jsonData, .orgId, .password, .typeLogoUrl, .user))' # removes from .[], ..map for array 

STDOUT | jq --unbuffered 'map({access, basicAuth, name, type, url})'   # keeps whitelisted from .[]

STDOUT | jq 'map(.price) | add'         #  will take an array of JSON objects as input and return the sum of their "price" fields
```

## edit

```sh
echo '{"hello": "world"}' | jq --arg foo bar '. + {foo: $foo}'                # add field: {  "hello": "world", "foo": "bar"  }

echo '{"hello": "world"}' | jq --arg foo bar '. + {hello: $foo}'              # override field value: { "hello": "bar" }

echo '{"hello": "world"}' | jq --arg foo bar '. + {hello: ("not" + $foo)}'    # concat and add: { "hello": "world", "foo": "notbar" }



STDOUT | jq -r '.[] | [.Node.Node, .Service.Service] | @tsv'    # print in same line; input must be an array, and it is rendered as TSV (tab-separated values)

STDOUT | jq -r '.servers  | keys[] as $k | "\(.[$k] | .url)"'   # get value of dynamic object names

json | jq -r '.data | .MINIO_SECRET_KEY | @base64d '            # base64-decode string

jq -R 'split(".") | .[1] | @base64d | fromjson' <<< "$TOKEN"    # decode jwt-token

jq -n -c '[{"foo": 1, "bar": 2}, {"foo": 3, "quux": 4}] | map(select( .bar ))'  # get element containing bar-field
```

## strftime

```sh
curl -s 'http://127.0.0.1:8080/loki/api/v1/delete' |  jq '.[] | .start_time |= (strftime("%Y-%m-%d %H:%M:%S")) | .end_time |= (strftime("%Y-%m-%d %H:%M:%S")) | .created_at |= (strftime("%Y-%m-%d %H:%M:%S"))'
{
  "start_time": "2024-11-05 08:21:42",
  "end_time": "2024-12-05 08:21:42",
  "created_at": "2024-12-05 08:21:53"
}
```

[[date]]

## @uri - url encoding

```sh
echo '{"a": "text with / and spaces &"}' | jq '@uri "\(.a)"'
# "texte%20with%20%2F%20and%20spaces%20%26"

echo '{"search":"what is jq?"}' | jq '@uri "https://www.google.com/search?q=\(.search)"'
# "https://www.google.com/search?q=what%20is%20jq%3F"

printf %s "same text as above with / and spaces &"|jq -sRr @uri
# same%20text%20as%20above%20with%20%2F%20and%20spaces%20%26
```

[[url encoding]], [gitlab.in2p3.fr/-/snippets/609](https://gitlab.in2p3.fr/-/snippets/609)

## see also

- [[jless]], [[fx]], [[jsonpath]]
- [[json5]]
- [[jp]]
- [[yq]]
- [[jwt]]
- [[curl]]
- [[aws]], [[govc]], [[kubectl]]
- [remysharp.com/drafts/jq-recipes](https://remysharp.com/drafts/jq-recipes)
- [unix.stackexchange.com/jq-print-key-and-value-for-all-in-sub-object](https://unix.stackexchange.com/a/406425)
- [stackoverflow.com/printing-multiple-values-on-the-same-line](https://stackoverflow.com/a/46131963)
