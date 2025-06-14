---
tags: [container]
title: kubectl
created: '2019-07-30T06:19:49.145Z'
modified: '2025-05-21T13:33:56.707Z'
---

# kubectl

> kubectl controls the Kubernetes cluster manager

[[kuberlr]], [[kubie]]

## installation

```sh
brew install kubectl
kubectl completion bash >$(brew --prefix)/etc/bash_completion.d/kubectl`

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

[[install]]

## environment

```sh
KUBECONFIG                        # path to kube config, specify multiple files by separating them with a colon
KUBERNETES_MASTER                 # URL of api-server, alternative way to specify the cluster's API server URL if it's not set in the kubeconfig file
KUBE_EDITOR, EDITOR               # editor to be used e.g. for `kubectl edit`
KUBECTL_EXTERNAL_DIFF             # Specifies the diff command to use when comparing resources with `kubectl diff`. This allows you to use your preferred diff tool
HTTP_PROXY, HTTPS_PROXY, NO_PROXY # proxy settings `kubectl` should use when communicating with the Kubernetes API server
```

## option

```sh
-v
--v=0 	# generally useful for this to always be visible to a cluster operator
--v=1 	# reasonable default log level if you don't want verbosity
--v=2 	# useful steady state information about the service and important log messages, recommended default log level for most systems
--v=3 	# extended information about changes
--v=4 	# debug level verbosity
--v=5 	# trace level verbosity
--v=6 	# display requested resources
--v=7 	# display HTTP request headers
--v=8 	# display HTTP request contents
--v=9 	# display HTTP request contents without truncation of contents

-o=[json|yaml] 	                    # output [JSON|YAML] formatted API object
-o=name 	                          # print only the resource name
-o=wide 	                          # output plain-text format with any additional information
-o=custom-columns=SPEC 	            # output table using a comma separated list of custom columns
-o=custom-columns-file=FILE         # output table using the custom columns template in the FILE file
-o=jsonpath=TEMPLATE  	            # output fields defined in a jsonpath expression
-o=jsonpath-file=FILE 	            # output fields defined by the jsonpath expression in the FILE file

-A                                  # all namespaces
-n, --namespace NS                  # namespace scope for cli equest

--as=""                             # Username to impersonate for the operation. User could be a regular user or a service account in a namespace.
--as-group=[]                       # Group to impersonate for the operation, this flag can be repeated to specify multiple groups.
--as-uid=""                         # UID to impersonate for the operation.

--certificate-authority=""          # path to a cert file for the certificate authority
--client-certificate=""             # path to a client certificate file for TLS
--client-key=""                     # path to a client key file for TLS

    --cluster CLUSTER               # name of the kubeconfig cluster to use
    --context CONTEXT               # name of the kubeconfig context to use
    --kubeconfig CONFIG             # path to the kubeconfig file to use for CLI requests.
-s, --server SERVER                 # address and port of the Kubernetes API server
    --token TOKEN                   # bearer token for authentication to the API server
    --user USER                     # name of the kubeconfig user to use
    --username USER                 # Username for basic authentication to the API server
    --password PASS                 # password for basic authentication to the API server

--insecure-skip-tls-verify=false    # true: don't check server's certificate for validity, makes https connections insecure
--match-server-version=false        # Require server version to match client version

--profile="none"                    # name of profile to capture. One of (none|cpu|heap|goroutine|threadcreate|block|mutex)
--profile-output="profile.pprof"    # name of the file to write the profile to

--request-timeout="0"               # time to wait before giving up on a single request; time unit (1s, 2m, 3h); zero means don't timeout requests
--tls-server-name=""                # server name to use for server certificate validation. If it is not provided, the hostname used to contact the server is used
--warnings-as-errors=false          # treat warnings received from the server as errors and exit with a non-zero exit code
--version=false                     # print version information and quit
```


## declarative / imperative commands

```sh
# declarative         imperative
  kubectl create      kubectl diff
  kubectl replace     kubectl apply
  kubectl delete
  kubectl edit
  kubectl scale
```

## versions

```sh
kubectl version -o yaml | yq e                                        # get client and server version

kubectl cluster-info                                                  # get addresses of the control plane and services

kubectl api-versions                                                  # get all supported api version
```

## api-resources

> get all resource-names, alias and kinds

```sh
    --api-group=''      # Limit to resources in the specified API group
    --cached=false      # Use the cached list of resources if available
    --namespaced=true   # If false, non-namespaced resources will be returned, otherwise returning namespaced resources by default
    --no-headers=false  # When using the default or custom-column output format, don't print headers (default print headers)
-o, --output=''         # Output format wide|name
    --sort-by=''        # If non-empty, sort list of resources using specified field The field can be either 'name' or 'kind'
    --verbs=[]          # Limit to resources that support the specified verbs
```

```sh
kubectl api-resources                                                 # get all resource-names, alias and kinds
kubectl api-resources -o name                                         # all resources with simple output (only the resource name)
kubectl api-resources -o wide                                         # all resources with expanded (aka "wide") output
kubectl api-resources -o wide --sort-by=name                          # get all objects
kubectl api-resources | awk '{if ( $2 ~ /^[a-z]{2,7}$/) {print $0}}'  # get only aliased objects
kubectl api-resources --namespaced=true                               # all namespaced resources
kubectl api-resources --verbs=list,get                                # all resources that support the "list" and "get" request verbs
kubectl api-resources --verbs=list --namespaced -o name
kubectl api-resources --api-group=extensions                          # all resources in the "extensions" API group

kubectl api-resources --verbs=list --namespaced=true
```

## cluster-info

> display addresses of the control plane and services with label `kubernetes.io/cluster-service=true`

```sh
kubectl cluster-info    # Print the address of the control plane and cluster services

kubectl cluster-info dump --namespaces default,kube-sytem,csi --output-directory=$(pwd)/$(kubectl config current-context).cluster-dump
```

## copy

> if [[tar]] is not present in container it will fail

```sh
tar cf - /tmp/foo | kubectl exec -i -n NAMESPACE <some-pod> -- tar xf - -C /tmp/bar    # Copy /tmp/foo local file to /tmp/bar in a remote pod in namespace <some-namespace>

kubectl exec POD -- tar cf - /tmp/foo | tar xf - -C /tmp/bar    # copy /tmp/foo from a remote pod to /tmp/bar locally

kubectl cp /tmp/foo_dir POD:/tmp/bar_dir                        # copy /tmp/foo_dir local directory to /tmp/bar_dir in a remote pod in the default namespace

kubectl cp /tmp/foo POD:/tmp/bar -c CONTAINER                   # copy /tmp/foo local file to /tmp/bar in a remote pod in a specific container

kubectl cp /tmp/foo NAMESPACE/POD:/tmp/bar                      # copy /tmp/foo local file to /tmp/bar in a remote pod in namespace NAMESPACE

kubectl cp NAMESPACE/POD:/tmp/foo /tmp/bar                      # copy /tmp/foo from a remote pod to /tmp/bar locally

kubectl cp POD:/etc/nginx/nginx.conf nginx.conf                 # copy nginx.conf to local dir
```

## config

> view and edit kubectl config

```sh
kubectl config view --minify
kubectl config view --flatten
kubectl config view --raw
kubectl config view --minify --output 'jsonpath={..namespace}'

kubectl config current-context
kubectl config get-contexts
kubectl config get-clusters

kubectl config use-context CONTEXT

kubectl config set-context CONTEXT --user minikube --cluster minikube --namespace NAMESPACE
kubectl config set-context --current --namespace kube-node-lease    # sets namespace

# merge configs
KUBECONFIG="$HOME/.kube/config:file2:file3" kubectl config view --merge --flatten \
  > ~/.kube/merged_kubeconfig && mv ~/.kube/merged_kubeconfig ~/.kube/config

# remove cluster, context and user from .kube/config
kubectl config delete-cluster MY_CLUSTER
kubectl config delete-context MY_CLUSTER_CONTXT
kubectl config unset users.MY_CLUSTER_USER
```

## create

```sh
kubectl create configmap go-websocket-cm \
  --from-file=index.html \
  --from-file=main.go \
  --from-file=go.sum \
  --from-file=go.mod \
  --dry-run=client \
  -o yaml > configmap.yaml 
```

## certificate

> cert, certs from `cert-manager.io/v1`

```sh
kubectl get certificate --all-namespaces -ojsonpath="{range .items[*]}{.metadata.name} not before: {.status.notBefore} not after: {.status.notAfter}{'\n'}{end}"
```

## explain

> explain resources

```sh
kubectl explain po
kubectl explain --help
kubectl explain --api-version=apps/v1 replicaset
kubectl explain deployment.metadata
kubectl explain deployment.spec
kubectl explain deployment.spec.template.spec.containers --recursive    # 🤩 recursive: get a hierarchical view of the various fields.
```

[[kubectl krew]] `kubectl explore RESOURCE`

## events

```sh
kubectl events --for postgresql/postgres-cluster

kubectl get events --sort-by='.lastTimestamp'

kubectl get events --sort-by=.metadata.creationTimestamp

kubectl get events --sort-by='.metadata.creationTimestamp' \
  -o 'go-template={{range .items}}{{.involvedObject.name}}{{"\t"}}{{.involvedObject.kind}}{{"\t"}}{{.message}}{{"\t"}}{{.reason}}{{"\t"}}{{.type}}{{"\t"}}{{.firstTimestamp}}{{"\n"}}{{end}}'
```

[[go-template]]


## node

```sh
kubectl label node --all 'vpc.amazonaws.com/has-trunk-attached'-                # remove all labels 'vpc.ama..'


kubectl get node NODE_NAME -o yaml | yq -C e '.metadata.finalizers' -           # check for finalizers
kubectl patch NODE_NAME -p '{"metadata":{"finalizers":[]}}' --type=merge        # remove finalizers

kubectl drain NODE_NAME --force --ignore-daemonsets  --delete-local-data
kubectl cordon NODE_NAME
kubectl delete node NODE_NAME


kubectl get nodes -o go-template='{{printf "%-50s %-12s\n" "Node" "Taint"}}{{- range .items}}{{- if $taint := (index .spec "taints") }}{{- .metadata.name }}{{ "\t" }}{{- range $taint }}{{- .key }}={{ .value }}:{{ .effect }}{{ "\t" }}{{- end }}{{- "\n" }}{{- end}}{{- end}}'
```

## daemonset

```sh
kubectl rollout restart daemonset/DAEMONSET

kubectl -n kube-system patch daemonset aws-node \
  -p '{"spec": {"template": {"spec": {"nodeSelector": {"non-existing": "true"}}}}}'               # "scale down" daemonset
kubectl -n kube-system patch daemonset aws-node \
  --type json -p='[{"op": "remove", "path": "/spec/template/spec/nodeSelector/non-existing"}]'    # "scale up" daemonset
```

## exec

```sh
kubectl exec -it POD -- curl -s http://10.1.0.3  # double dash `--` signals end of command options, if not set -s would be interpreted as kubectl flag

kubectl exec -it POD -- cat /data/out.txt | tail -n 3
```

## get

> display one or many resources

```sh
kubectl get RESOURCE    # kubectl api-resources -o name
kubectl get all         # get alle resoruce of current namespace


kubectl get apiservices

kubectl get crd volumesnapshotcontent -o yaml

kubectl get deployments.v1.apps -o json   # List deployments in JSON output format, in the "v1" version of the "apps" API group

kubectl get replicationcontroller web     # List a single replication controller with specified NAME in ps output format
kubectl get rc,services                                   # List all replication controllers and services together in ps output format
kubectl get rc/web service/frontend pods/web-pod-13je7    # List one or more resources by their type and names

kubectl get svc SERVICE -o jsonpath="{.status.loadBalancer.ingress[*].hostname}"
```

```sh
kubectl get --raw /.well-known/openid-configuration

kubectl get --raw /apis/

kubectl get --raw /metrics

kubectl get --raw /apis/flowcontrol.apiserver.k8s.io/v1beta3/flowschemas/eks-workload-high | yq -P

kubectl get -k dir/                       # List resources from a directory with kustomization.yaml - e.g. dir/kustomization.yaml
kubectl get -f pod.yaml -o json           # List a pod identified by type and name specified in "pod.yaml" in JSON output format
```

```sh
kubectl get pod
kubectl get pod -L app.kubernetes.io/component,app.kubernetes.io/part-of  # labels that are going to be presented as columns
kubectl get pods --show-labels | awk '{print $6}' | column -s, -t         # show all labels as the last column
kubectl get pods -A -o wide --field-selector spec.nodeName=NODE  # list all pods running on NODE

kubectl get pod POD -o [yaml|json]
kubectl get pod POD -o template --template={{.status.phase}}     # return only the phase value of the specified pod
kubectl get pod POD -o custom-columns=CONTAINER:.spec.containers[0].name,IMAGE:.spec.containers[0].image   # list resource information in custom columns
```

```sh
kubectl get nodes
kubectl get node NODE -o name
kubectl get node NODE -o json | jq -r '.status.capacity.memory' | numfmt --from=iec-i --to=iec     # get avail memory
kubectl get nodes --selector='!node-role.kubernetes.io/master' --no-headers -o custom-columns=":metadata.name"
kubectl get node -L $(kubectl get node NODE -o json | jq -r '.metadata.labels | keys | join(",")')
```


## run

> running adhoc pod without yaml-manifest / create and run a particular image in a pod

```sh
kubectl run     # same as `kubectl create deployment`

kubectl run NAME --image ubuntu --restart=Never --rm -i --tty -- /bin/bash

kubectl run NAME --image=tutum/dnsutils --command -- sleep infinity

kubectl run NAME --image=radial/busyboxplus:curl -i --tty   # then run: nslookup my-nginx

kubectl run NAME --image=gcr.io/google_containers/echoserver:1.4 --port=8080

kubectl run NAME --image=k8s.gcr.io/echoserver:1.4 --port=8080

kubectl run NAME --image=bitnami/postgresql --restart=Never --overrides='{"spec": {"securityContext": {"runAsUser": 0}}}' --command -- sleep infinity

kubectl run NAME --image=mongo:4.0 `# run pod on specific node `\
  --overrides='{"apiVersion": "v1", "spec": {
    "affinity": {
      "nodeAffinity": {
        "requiredDuringSchedulingIgnoredDuringExecution": {
          "nodeSelectorTerms": [{
              "matchFields": [{
                  "key": "metadata.name",
                  "operator": "In",
                  "values": ["NODE_NAME"]
                }]
            }]
        }}}}}' \ 
  --command -- sleep infinity
```

## service

> routes internal traffic

```sh
kubectl apply   # makes incremental changes to an existing object
STDOUT | kubectl apply -f -
kubectl apply -f https://HOST/DEPLOYMENT.yaml

kubectl create  # creates a whole new object (previously non-existing / deleted) 
kubectl create -f kubia-manual.yaml

kubectl create whatever --dry-run=true -o yaml | kubectl apply -f -     # applying (declarative pattern) output of imperative command

kubectl delete deployment DEPLOYMENT


kubectl scale --replicas=1 kubia
kubectl scale replicationcontroller kubia --replicas=1

kubectl patch svc SERVICE -p '{"spec": {"type": "LoadBalancer"}}'

# edit a resource from the default editor
KUBE_EDITOR="nano" kubectl edit svc/SERVICE                  # use alternative editor
kubectl edit svc/SERVICE                                     # edit the service named 'docker-registry'
kubectl edit job.v1.batch/myjob -o json                      # edit the job 'myjob' in JSON using the v1 API format
kubectl edit deployment/mydeployment -o yaml --save-config   # edit the deployment 'mydeployment' in YAML and save the modified config in its annotation
```

## taint

> update taints on one or more nodes

```sh
# Update node 'foo' with a taint with key 'dedicated' and value 'special-user' and effect 'NoSchedule'
# If a taint with that key and effect already exists, its value is replaced as specified
kubectl taint nodes foo dedicated=special-user:NoSchedule

kubectl taint nodes foo dedicated:NoSchedule-   # Remove from node 'foo' the taint with key 'dedicated' and effect 'NoSchedule' if one exists
kubectl taint nodes foo dedicated-              # Remove from node 'foo' all the taints with key 'dedicated'

kubectl taint node -l myLabel=X  dedicated=foo:PreferNoSchedule   # Add a taint with key 'dedicated' on nodes having label myLabel=X
kubectl taint nodes foo bar:NoSchedule                            # Add to node 'foo' a taint with key 'bar' and no value
```

## ingress

> manages external access to services, may provide load balancing, SSL termination and name-based virtual hosting

```sh
kubectl patch ingress INGRESS_NAME -p '{"metadata":{"finalizers":[]}}' --type=merge
```

## deployment/statefulset

```sh
kubectl expose deployment DEPLOYMENT --type=NodePort

kubectl rollout restart deployment/nginx

kubectl rollout status deployment aws-load-balancer-controller

kubectl autoscale deployment DEPLOYMENT \
  --cpu-percent=50    `# target average CPU utilization` \
  --min=1             `# lower limit for the number of pods that can be set by the autoscaler` \
  --max=10            `# upper limit for the number of pods that can be set by the autoscaler`

kubectl patch deployment NAME --type=json -p='[{"op": "add", "path": "/spec/template/metadata/labels/this", "value": "that"}]'
```

## job

```sh
kubectl create job --from cronjob/some-job some-job-trigger-1   # manually trigger a job
```

## label

```sh
kubectl label pods foo unhealthy=true                 # Update pod 'foo' with the label 'unhealthy' and the value 'true'
kubectl label --overwrite pods foo status=unhealthy   # Update pod 'foo' with the label 'status' and the value 'unhealthy', overwriting any existing value
kubectl label pods --all status=unhealthy             # Update all pods in the namespace
kubectl label -f pod.json status=unhealthy            # Update a pod identified by the type and name in "pod.json"
kubectl label pods foo status=unhealthy --resource-version=1    # Update pod 'foo' only if the resource is unchanged from version 1
kubectl label pods foo bar-   # Update pod 'foo' by removing a label named 'bar' if it exists; Does not require the --overwrite flag
```

## logs

```sh
kubectl logs POD

kubectl logs POD -c CONTAINER

kubectl logs INGRESS_CONTROLLER -c controller \
  | jq -r '. | select(.nginx.status != "200") | .nginx | "\(.status): \(.remote_addr) \(.request) \(.proxy_upstream_name)"'
```

## port-forward 

> forward one or more local ports to a pod (requires node to have [[socat]] installed)

> `kubectl port-forward [resource-type]/[resource-name] [local-port]:[resource-port]`

```sh
kubectl port-forward deployment/mongo             28015:27017
kubectl port-forward deployment/mongo                  :27017    # let's kubectl choose the local port
kubectl port-forward deployment/mydeployment      5000 6000      # listen on ports 5000 and 6000 locally, forwarding data to/from ports 5000 and 6000 in a pod selected by the deployment

kubectl port-forward replicaset/mongo-75f59d57f4  28015:27017

kubectl port-forward service/mongo                28015:27017
kubectl port-forward service/myservice            8443:https     # listen on port 8443 locally, forwarding to the targetPort of the service's port named "https" in a pod selected by the service

kubectl port-forward mongo-75f59d57f4-4nd6q       28015:27017
kubectl port-forward pods/mongo-75f59d57f4-4nd6q  28015:27017
kubectl port-forward                                 pod/mypod 5000 6000  # listen on ports 5000 and 6000 locally, forwarding data to/from ports 5000 and 6000 in the pod
kubectl port-forward                                 pod/mypod 8888:5000  # listen on port 8888 locally, forwarding to 5000 in the pod
kubectl port-forward                                 pod/mypod :5000      # listen on a random port locally, forwarding to 5000 in the pod
kubectl port-forward --address 0.0.0.0               pod/mypod 8888:5000  # listen on port 8888 on all addresses, forwarding to 5000 in the pod
kubectl port-forward --address localhost,10.19.21.23 pod/mypod 8888:5000  # listen on port 8888 on localhost and selected IP, forwarding to 5000 in the pod
```

## proxy

> creates a proxy server or application-level gateway between localhost and the Kubernetes API server

```sh
kubectl proxy --api-prefix=/                                              # proxy all of the Kubernetes API and nothing else

kubectl proxy --www=/my/files --www-prefix=/static/ --api-prefix=/api/    # proxy only part of the Kubernetes API and also some static files
curl localhost:8001/api/v1/pods

kubectl proxy --api-prefix=/custom/                                       # proxy the entire Kubernetes API at a different root
curl localhost:8001/custom/api/v1/pods

kubectl proxy --port=8011 --www=./local/www/        # run a proxy on port 8011, serving static content from ./local/www/

kubectl proxy --port=0                              # run a proxy on an arbitrary local port

kubectl proxy --api-prefix=/k8s-api                 # run a proxy and changing the API prefix to k8s-api
curl localhost:8001/k8s-api/v1/pods/

# force delete a namespace, when kubectl edit making the same change has no effect
kubectl proxy &
kubectl get namespace $NAMESPACE -o json |jq '.spec = {"finalizers":[]}' >temp.json
curl -k -H "Content-Type: application/json" -X PUT --data-binary @temp.json 127.0.0.1:8001/api/v1/namespaces/$NAMESPACE/finalize
```

## pv - persistant volume

```sh
kubectl get pv pvc-c7d68f31-4104-4827-b63d-0181ed25c50e -o jsonpath='{.spec.awsElasticBlockStore.volumeID}'  # get volumeId
```

## pvc - persistant volume claim

```sh
kubectl get pvc
```


## sc - storageclass

```sh
kubectl get storageclass
```

## secrets

```sh
kubectl get secrets --field-selector type=kubernetes.io/tls     # list only certificate secrets
kubectl get secrets --field-selector type=Opaque

kubectl get secrets SECRET -o json | jq -r '.data | to_entries[] | "\(.key): \(.value | @base64d)"';    # print secrets base64-decoded
```

## krew

> a kubectl plugin manager

```sh
# failed to retrieve plugin indexes: failed to list the remote URL for index default
unset GIT_CONFIG
```

```sh
kubectl krew help        # Help about any command
kubectl krew index       # Manage custom plugin indexes
kubectl krew info        # Show information about an available plugin
kubectl krew install     # Install kubectl plugins
kubectl krew list        # List installed kubectl plugins
kubectl krew search      # Discover kubectl plugins
kubectl krew uninstall   # Uninstall plugins
kubectl krew update      # Update the local copy of the plugin index
kubectl krew upgrade     # Upgrade installed plugins to newer versions
kubectl krew version     # Show krew version and diagnostics


kubectl krew  list
PLUGIN         VERSION
access-matrix  v0.5.0
cert-manager   v1.13.0
explore        v0.7.1
krew           v0.4.4
stern          v1.27.0

kubectl krew install oidc-login     # install plugin

kubectl access-matrix               # use plugin to see the level of access user has on namespaces

kubectl stern some-pod-             # prints logs of all pods starting with some-pod-
```

[[kubectl krew]], [krew.sigs.k8s.io/docs/user-guide/quickstart/](https://krew.sigs.k8s.io/docs/user-guide/quickstart/)

## see also

- [[kubernetes]], [[oc]]
- [[helm]], [[kustomize]]
- [[cmctl]], [[nerdctl]]
- [[bazel]]
- [[kubectx]], [[kubens]], [[kubeseal]], [[kubeval]], [[kubie]]
- [[rbac-lookup]]
- [[krr]]
- [[kim]], [[opa]]
- [[aws]], [[eksctl]], [[kops]]
- [[minikube]], [[k3s]], [[k3d]], [[k0s]], [[k9s]]
- [[yml]], [[jsonpath]], [[go-template]]
- [[socat]]
- [kubernetes.io/docs/reference/kubectl](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)
- [stackoverflow.com/questions/47369351/kubectl-apply-vs-kubectl-create](https://stackoverflow.com/questions/47369351/kubectl-apply-vs-kubectl-create)
