---
tags: [container]
title: kubernetes rbac
created: '2022-03-23T21:22:09.880Z'
modified: '2024-10-20T13:16:11.098Z'
---

# kubernetes rbac

> `role base access controll` - defines user privileges in cluster

- maps http-verbs to permissions -> POST to CREATE
- ROLE -> What
- ROLEBINDING -> WHO
- ROLE,ROLEBINDING -> namespace wide
- CLUSTERROLE,CLUSTEROLEBINDING -> cluster wide


### default ClusterRoles

- cluster-admin: Cluster-wide superuser
- admin: Full access within a Namespace
- edit: Read/write within a Namespace
- view: Read-only within a Namespace


## list bindings

```sh
kubectl get rolebindings,clusterrolebindings --all-namespaces \
-o custom-columns='KIND:kind,NAMESPACE:metadata.namespace,NAME:metadata.name,SERVICE_ACCOUNTS:subjects[?(@.kind=="ServiceAccount")].name' 
```

[[rbac-lookup]], [[rbac-tool]], [[k9s]]


## see also

- [https://aws.github.io/aws-eks-best-practices/security/docs/iam/](https://aws.github.io/aws-eks-best-practices/security/docs/iam/)
- [anaisurl.com/kubernetes-rbac/](https://anaisurl.com/kubernetes-rbac/)
- [medium.com/devops-mojo/kubernetes-role-based-access-control-rbac-overview-introduction-rbac-with-kubernetes-what-is-2004d13195df](https://medium.com/devops-mojo/kubernetes-role-based-access-control-rbac-overview-introduction-rbac-with-kubernetes-what-is-2004d13195df)
- [sysdig.com/learn-cloud-native/kubernetes-security/kubernetes-rbac/](https://sysdig.com/learn-cloud-native/kubernetes-security/kubernetes-rbac/)
- [blog.aquasec.com/kubernetes-verbs](https://blog.aquasec.com/kubernetes-verbs)
- [kubernetes.io/docs/reference/access-authn-authz/rbac/](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)

