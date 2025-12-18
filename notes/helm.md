---
tags: [container]
title: helm
created: '2021-06-04T08:40:48.010Z'
modified: '2025-12-08T13:20:12.295Z'
---

# helm

> package manager for `k8s`

[[kustomize]], [[helmfile]], [[oras]]

## install

```sh
brew install helm

curl -sSL https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
```

## environment vairables

```sh
HELM_CACHE_HOME                     # alt location for storing cached files
HELM_CONFIG_HOME                    # alt location for storing Helm configuration
HELM_DATA_HOME                      # alt location for storing Helm data
HELM_DEBUG                          # indicate whether or not Helm is running in Debug mode
HELM_DRIVER                         # backend storage driver: configmap, secret, memory, postgres                                                  
HELM_DRIVER_SQL_CONNECTION_STRING   # connection string the SQL storage driver should use
HELM_MAX_HISTORY                    # maximum number of helm release history
HELM_NAMESPACE                      # namespace used for the helm operations
HELM_NO_PLUGINS                     # ble plugins. Set HELM_NO_PLUGINS=1 to disable plugins
HELM_PLUGINS                        # path to plugins dir
HELM_REGISTRY_CONFIG                # path to registry config file
HELM_REPOSITORY_CACHE               # path to repository cache dir
HELM_REPOSITORY_CONFIG              # path to repositories file
KUBECONFIG                          # alt k8s config - default `.kube/config`
HELM_KUBEAPISERVER                  # k8s API Server Endpoint for auth
HELM_KUBECAFILE                     # k8s certificate authority file
HELM_KUBEASGROUPS                   # set groups to use for impersonation using a comma-separated list
HELM_KUBEASUSER                     # Username to impersonate for the operation
HELM_KUBECONTEXT                    # name of the kubeconfig context
HELM_KUBETOKEN                      # bearer kube-token used for auth
```

## options

> global flags

```sh
    --burst-limit int                 # client-side default throttling limit (default 100)
    --debug                           # enable verbose output
-h, --help                            # help for helm
    --kube-apiserver string           # the address and the port for the Kubernetes API server
    --kube-as-group stringArray       # group to impersonate for the operation, this flag can be repeated to specify multiple groups.
    --kube-as-user string             # username to impersonate for the operation
    --kube-ca-file string             # the certificate authority file for the Kubernetes API server connection
    --kube-context string             # name of the kubeconfig context to use
    --kube-insecure-skip-tls-verify   # if true, the Kubernetes API server's certificate will not be checked for validity. This will make your HTTPS connections insecure
    --kube-tls-server-name string     # server name to use for Kubernetes API server certificate validation. If it is not provided, the hostname used to contact the server is used
    --kube-token string               # bearer token used for authentication
    --kubeconfig string               # path to the kubeconfig file
-n, --namespace string                # namespace scope for this request
    --registry-config string          # path to the registry config file (default "/Users/daniel/Library/Preferences/helm/registry/config.json")
    --repository-cache string         # path to the file containing cached repository indexes (default "/Users/daniel/Library/Caches/helm/repository")
    --repository-config string        # path to the file containing repository names and URLs (default "/Users/daniel/Library/Preferences/helm/repositories.yaml")
```

## usage

```sh
helm completion  # generate autocompletion scripts for the specified shell
helm create      # create a new chart with the given name
helm dependency  # manage a chart's dependencies
helm env         # helm client environment information

helm help        # Help about any command
helm history RELEASE_NAME # fetch release history

helm lint        # examine a chart for possible issues

helm mapkubeapis # Map release deprecated Kubernetes APIs in-place
helm package     # package a chart directory into a chart archive

helm push        # push a chart to remote
helm registry    # login to or logout from a registry

helm rollback RELEASE_NAME [REVISION] # roll back a release to a previous revision


helm status RELEASE_NAME  # display the status of the named release

helm test        # run tests for a release

helm upgrade     # upgrade a release
helm verify      # verify that a chart at the given path has been signed and is valid
helm version     # print the client version information
```

## install

> install a chart

```sh
--create-namespace                           # create the release namespace if not present
```

```sh
helm install                                              # upload chart to k8s
helm install --generate-name bitnami/mysql 
helm install --debug --dry-run CHART ./PATH               # test the template rendering, but not actually install anything
```

## uninstall

> uninstall a release

```sh
helm uninstall RELEASE

helm uninstall mysql-1612624192   # uninstall release
```

## search

> search for a keyword in charts

```sh
helm search repo REPONAME

helm search repo grafana/loki --versions      # get all version of chart

helm search repo sealed-secrets


curl -sL https://bitnami-labs.github.io/sealed-secrets/index.yaml | yq '.entries[][].urls'
```

[[curl]]

## repo

> add, list, remove, update, and index chart repositories

```sh
helm repo add NAME REPO   # add a chart repository

helm repo add stable  https://charts.helm.sh/stable       # add as "stable" -> prepends "stable/REPO"
helm repo add datadog https://helm.datadoghq.com
helm repo add bitnami https://charts.bitnami.com/bitnami

helm repo index           # generate an index file given a directory containing packaged charts
helm repo list            # list chart repositories
helm repo remove          # remove one or more chart repositories
helm repo update          # update information of available charts locally from chart repositories
```

```sh
helm repo add bitnami-full-index https://raw.githubusercontent.com/bitnami/charts/archive-full-index/bitnami
helm search repo bitnami-full-index/postgresql --versions           # list avail versions
helm search repo bitnami-full-index/postgresql --version 11.1.26
curl -i https://raw.githubusercontent.com/bitnami/charts/archive-full-index/bitnami/index.yaml


```

[[curl]], [github.com/bitnami/charts/issues/14060](https://github.com/bitnami/charts/issues/14060)

## list

> list releases

```sh
-a, --all                  # show all releases without any filter applied
-A, --all-namespaces       # list releases across all namespaces
-d, --date                 # sort by release date
    --deployed             # show deployed releases. If no other is specified, this will be automatically enabled
    --failed               # show failed releases
-f, --filter string        # a regular expression (Perl compatible). Any releases that match the expression will be included in the results
-h, --help                 # help for list
-m, --max int              # maximum number of releases to fetch (default 256), 0 will not return all results, but the server's default
    --no-headers           # don't print headers when using the default output format
    --offset int           # next release index in the list, used to offset from start value
-o, --output format        # prints the output in the specified format. Allowed values: table, json, yaml (default table)
    --pending              # show pending releases
-r, --reverse              # reverse the sort order
-l, --selector string      # selector (label query) to filter on, supports '=', '==', and '!='.(e.g. -l key1=value1,key2=value2). Works only for secret(default) and configmap storage backends.
-q, --short                # output short (quiet) listing format
    --superseded           # show superseded releases
    --time-format string   # format time using golang time formatter. Example: --time-format "2006-01-02 15:04:05Z0700"
    --uninstalled          # show uninstalled releases (if 'helm uninstall --keep-history' was used)
    --uninstalling         # show releases that are currently being uninstalled
```

```sh
helm list                         # lists all of the releases for a specified namespace
helm ls -a                        # alias, list all, some might be pending which wouldn't show

helm list --filter 'ara[a-z]+'    # filter names by regex
```

## show

> show information of a chart

```sh
helm show all CHART_NAME        # show all information of the chart
helm show all CHART
helm show all bitnami/mysql

helm show crds CHART_NAME       # show the chart's CRDs

helm show readme CHART_NAME     # show the chart's README

helm show chart CHART_NAME      # show the chart's definition
helm show chart datadog --repo https://helm.datadoghq.com --version 2.6.11
helm show chart bitnami/mysql

helm show values CHART_NAME     # show the chart's values
helm show values oci://ghcr.io/prometheus-community/charts/prometheus-postgres-exporter
```

## get

> add, list, remove, update, and index chart repositories

```sh
-a, --all             # dump all (computed) values
-h, --help            # help for values
-o, --output format   # prints the output in the specified format. Allowed values: table, json, yaml (default table)
    --revision int    # get the named release with revision
```

```sh
helm get -h                      # or type a command followed by -h flag
helm get all      RELEASE_NAME   # download all information for a named release
helm get hooks    RELEASE_NAME   # download all hooks for a named release
helm get manifest RELEASE_NAME   # download the manifest for a named release
helm get metadata RELEASE_NAME   # fetches metadata for a given release
helm get notes    RELEASE_NAME   # download the notes for a named release

helm get values   RELEASE_NAME                # download the values file for a named release
helm get values   RELEASE_NAME -o yaml        # -o, --output format   prints the output in the specified format. Allowed values: table, json, yaml (default table)
helm get values   RELEASE_NAME -a             # get all computed values
helm get values   RELEASE_NAME --revision 1   # get vals from other revision
```

## history

> prints historical revisions for a given release

```sh
helm history RELEASE_NAME
```

## pull

> download a chart from a repository and (optionally) unpack it in local directory

```sh
helm pull grafana/loki --version 6.6.3        
helm pull stable/CHART --untar                # optionally untar chart
helm pull codecentric/keycloak --version 18.1.1

helm pull oci://ghcr.io/codecentric/helm-charts/keycloak --version 18.10.0    # form oci
```

## plugin

> manage client side helm plugins

```sh
helm plugin install     # install one or more Helm plugins
helm plugin install https://github.com/databus23/helm-diff

helm plugin list        # list installed Helm plugins

helm plugin uninstall   # uninstall one or more Helm plugins

helm plugin update      # update one or more Helm plugins
```

## plugin: diff

> plugin giving a preview of what a helm upgrade would change

```sh
helm plugin install https://github.com/databus23/helm-diff

helm diff revision RELEASE 100 55
```

## plugin: mapkubeapis

> plugin updates in-place helm release metadata that contains deprecated/removed Kubernetes APIs to a new instance with supported Kubernetes APIs

```sh
helm plugin install https://github.com/helm/helm-mapkubeapis

helm mapkubeapis ...
```

## plugin: secrets

> plugin for decrypt encrypted Helm value files on the fly

```sh
helm plugin install https://github.com/jkroepke/helm-secrets

helm secrets
```

## plugin: s3

> plugin that provides [[aws]] s3 protocol support

```sh
helm plugin install https://github.com/hypnoglow/helm-s3.git

helm s3 init s3://bucket-name/charts

helm s3 push ./epicservice-0.7.2.tgz mynewrepo

helm s3 delete epicservice --version 0.7.2 mynewrepo
```

## plugin: helm-git

> plugin that provides [[git]] protocol support

```sh
helm plugin install https://github.com/aslafy-z/helm-git --version 0.16.1

helm repo add cert-manager git+https://github.com/jetstack/cert-manager@deploy/charts?ref=v0.6.2

helm fetch cert-manager/cert-manager --version "0.6.6"
helm fetch git+https://github.com/jetstack/cert-manager@deploy/charts/cert-manager-v0.6.2.tgz?ref=v0.6.2

helm install . -f git+https://github.com/aslafy-z/helm-git@tests/fixtures/example-chart/values.yaml   # pull value files
```



## template

> locally render templates

```sh
helm template .     #  see only the resolved yaml

helm template CHART                                   # render chart templates locally and display the output
helm template CHART -x templates/deployment.yaml      # render just one template in a chart
```

---

## state secrets

```sh
kubectl get secret --field-selector type=helm.sh/release.v1 -o name
kubectl get secret --field-selector type=helm.sh/release.v1 --no-headers -o custom-columns=":metadata.name"
kubectl get secret --field-selector type=helm.sh/release.v1 -l name=external-dns --sort-by=.metadata.creationTimestamp -o jsonpath='{.items[-1].metadata.name}'


kubectl get secrets sh.helm.release.v1.external-dns.v11 -o json | jq -r '.data.release' | base64 -d | base64 -d | gzip -d  | jq '.chart.metadata.dependencies[].repository'


kubectl get ns -o custom-columns=":.metadata.name" --no-headers | while read NS; do
  helm -n $NS list -q | while read; do 
    [ -z $REPLY ] && continue;
    SEC=$(kubectl -n $NS get secret --field-selector type=helm.sh/release.v1 -l name=$REPLY --sort-by=.metadata.creationTimestamp -o jsonpath='{.items[-1].metadata.name}'); 
    echo kubectl -n $NS get secret $SEC -o json '| jq -r '.data.release' | base64 -d | base64 -d | gzip -d  | jq '.chart.metadata.dependencies[].repository''
  done
done
```

[[kubectl]]

---


## helmfile

> TODO: move to seperate file

```yaml
{{/* if dig "monitoring" "enabled" false .Values.mrz */}}
{{if (((.Values.mrz).monitoring).enabled) }}    # value optional
```

[[helmfile]]


## see also

- [[go-template]]
- [[kustomize]]
- [helm.sh/docs/intro/quickstart](https://helm.sh/docs/intro/quickstart/)#
- [[flux]], [[argocd]]
