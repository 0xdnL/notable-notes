---
tags: [go]
title: yq
created: '2019-08-20T12:05:18.926Z'
modified: '2024-06-19T08:44:07.101Z'
---

# yq

> lightweight and portable command-line YAML processor

## install

```sh
brew install yq

GO111MODULE=on go get github.com/mikefarah/yq/v4        # from source

yq shell-completion bash > /etc/bash_completion.d/yq    # install bach_completion
```

## option

```sh
-C, --colors                  # force print with colors
-M, --no-colors               # force print with no colors
-e, --exit-status             # set exit status if there are no matches or null or false is returned
-f, --front-matter STRING     # first input as yaml front-matter: extract, process
                              #    extract: will pull out the yaml content
                              #    process: will run the expression against the yaml content, leaving the remaining data intact
    --header-preprocess       # slurp any header comments and separators before processing expression. 
                              #     workaround for go-yaml to persist header content. (default true)
-I, --indent INT              # sets indent level for output (default 2)
-i, --inplace                 # update the yaml file inplace of first yaml file given.
-N, --no-doc                  # don't print document separators `---`
-n, --null-input              # don't read input, simply evaluate the expression given. Useful for creating yaml docs from scratch.
-o, --output-format STRING    # output format (default "yaml"): yaml, y, json, j, props, p
-P, --prettyPrint             # pretty print, shorthand for '... style = ""'
    --unwrapScalar            # unwrap scalar, print the value with no quotes, colors or comments (default true)
-v, --verbose                 # verbose mode
```

## operators

> `yq` expressions are made up of operators and pipes

```sh
add

reduce      # powerful way to process a collection of data into a new form
            # EXPRESSION as $NAME ireduce (INIT; BLOCK)

.[] as $item ireduce (0; . + $item)


env
strenv          # inject the contents from an environment variable

sort_keys(.)    # sort keys of map
sort_keys(..)   # sort keys recursively
``` 

## usage

```sh
yq r file.yml services.application.image                # read file and print ..image

yq w -i -s ../update.yml file.yml                       # write/update file


eksctl utils schema | yq -P                             # convert json output to yaml

helm template CHART | yq eval-all                       # read multiple yaml documents

readarray actions < <(yq e '.coolActions[]' sample.yaml)    # create a bash array

LICENSE=$(cat LICENSE) yq eval -n '.a = strenv(LICENSE)' # strenv operator to inject the contents from an environment variable. 

# merge multiple documents into one
# to merge, use the reduce operator with the * (multiply) operator. 
# note: the use of ea/eval-all to load all files into memory so that they can be merged
yq ea '. as $item ireduce ({}; . * $item )' FILE1.yml FILE2.yml


yq eval '... comments=""' FILE.yaml                 # strip all comments, `...` ensure key nodes are included

diff -y -W $(tput cols) <(yq e -P FILE1.yaml) <(yq e -P FILE2.yaml)                      # using pretty print to normalise styling and running diff
diff -y -W $(tput cols) <(yq e 'sort_keys(..)' 1.yaml) <(yq e 'sort_keys(..)' 2.yaml)    # sort keys recursively, reducing diff noise

yq e '. | select(.kind == "Service") ' FILE.yaml    # print only document of kind: Service


# https://stackoverflow.com/a/68291270/14523221
yq -y 'del(.. | select(objects and length == 0))'   # Remove empty objects
yq -y 'del(.. | select(arrays and length == 0))'    # Remove empty arrays
yq -y 'del(.. | select(length == 0))'               # Remove empty objects, arrays and strings


# concat two strings
kubectl get node -o yaml | yq e '.items[].metadata.labels | ."kubernetes.io/role" + " " + ."node.kubernetes.io/instance-type" ' -

# select two values via `(.val, .foo)`
kubectl get node -o yaml | yq e '.items[].metadata.labels | (."kubernetes.io/role", ."node.kubernetes.io/instance-type") ' -

kubectl get secret SECRET -o yaml | yq '.data | map(@base64d)'    # base64 decode secret values
```

## base64d

```sh
kubectl get secret SECRET -o yaml | yq '.data |= with_entries(.value |= @base64d)|.data'    # decode each .data value
```

## see also

- [[yaml]]
- [[jq]]
- [[kubectl]], [[eksctl]], [[docker-compose]]
- [[bash readarray]]
- [mikefarah.gitbook.io/yq](https://mikefarah.gitbook.io/yq/)
