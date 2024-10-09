---
tags: [json]
title: jsonpath
created: '2020-10-09T11:50:35.973Z'
modified: '2024-10-08T10:17:32.396Z'
---

# jsonpath

> defines expressions to traverse through a json

## usage

```sh
$ 	                # root object/element
@ 	                # current object/element
. or [] 	          # child operator
.. 	                # recursive descent (borrowed from E4X)
* 	                # wildcard all objects/elements regardless names
[] 	                # subscript operator
[,] 	              # union operator allows alternate names or array indices as a set
[start:end:step] 	  # array slice operator (borrowed from E4X)
?() 	              # applies a filter (script) expression.
() 	                # script expression, using the underlying script engine.

$.store.book[0].title             # expressions can use the dot–notation
$['store']['book'][0]['title']    # or the bracket–notation
```

## functions

```sh
min() 	    # (double)  provides min value of an array of numbers 	
max() 	    # (double)  provides max value of an array of numbers 	
avg() 	    # (double)  provides average value of an array of numbers 	
stddev() 	  # (double)  provides standard deviation value of an array of numbers 	
length() 	  # (integer) provides length of an array
sum() 	    # (double)  provides sum value of an array of numbers 	
```

## filters

```sh
== 	        # left is equal to right (note that 1 is not equal to '1')
!= 	        # left is not equal to right
< 	        # left is less than right
<= 	        # left is less or equal to right
> 	        # left is greater than right
>= 	        # left is greater than or equal to right
=~ 	        # left matches regular expression [?(@.name =~ /foo.*?/i)]
in 	        # left exists in right [?(@.size in ['S', 'M'])]
nin 	      # left does not exists in right
subsetof 	  # left is a subset of right [?(@.sizes subsetof ['S', 'M', 'L'])]
anyof 	    # left has an intersection with right [?(@.sizes anyof ['M', 'L'])]
noneof 	    # left has no intersection with right [?(@.sizes noneof ['M', 'L'])]
size 	      # size of left (array or string) should match right
empty 	    # left (array or string) should be empty
```

## kubectl

```sh
kubectl get deployments -o jsonpath='{range .items[*]}
{"---"}
{"name: "}{@.metadata.name}
{"env.secretKeyRef: "}
  {range @.spec.template.spec.containers[*].env[*]}{"- "}{@.valueFrom.secretKeyRef.name}
  {end}
{"envFrom.configMapRef: "}
  {range @.spec.template.spec.containers[*].envFrom[*]}{"- "}{@.configMapRef.name}
  {end}
{"envFrom.secretRef: "}
  {range @.spec.template.spec.containers[*].envFrom[*]}{"- "}{@.secretRef.name}
  {end}
{end}' | yq e -P 'del(.. | select(length == 0))' - | yq e -P 'del(.. | select(length == 0))'

kubectl get svc SERVICE          -o jsonpath='{.spec.clusterIP}'
                                              {.items[*].status.addresses[?(@.type=="ExternalIP")].address}

kubectl get nodes                -o jsonpath='{.items[*].status.addresses[?(@.type=="InternalDNS")].address}'
kubectl get nodes                -o jsonpath='{.items[*].spec.taints}{"\n"}' | jq
kubectl get nodes                -o jsonpath='{range .items[*].status.images[*]}{.names[0]}{"\n"}{end}'

kubectl get pods -l run=my-nginx -o jsonpath='{.items[0].metadata.name}'
kubectl get pods                 -o jsonpath='{range .items[*]}{@.metadata.name}{" "}{@.spec.containers[*].image}{"\n"}{end}'

kubectl get secret SECRET        -o jsonpath="{.data.name-password}" | base64 -d
```

## see also

- [[jq]], [[yq]]
- [[go-template]]
- [[kubectl]]
- [[xpath]]
- [goessner.net/articles/JsonPath/](https://goessner.net/articles/JsonPath/)
- [github.com/json-path/JsonPath](https://github.com/json-path/JsonPath)
- [cburgmer.github.io/json-path-comparison/](https://cburgmer.github.io/json-path-comparison/)
