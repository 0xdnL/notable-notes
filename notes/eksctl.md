---
tags: [container]
title: eksctl
created: '2021-10-13T09:32:12.878Z'
modified: '2024-11-29T12:29:38.628Z'
---

# eksctl

> for creating and managing eks clusters on [[aws]]

written in [[go]], uses `cloudformation`, was created by weaveworks

## install

```sh
brew tap weaveworks/tap && brew install weaveworks/tap/eksctl
```

## option

```sh
--profile=PROFILE       # aws profile used to connect
```

## usage

```sh
eksctl get cluster --name NAME --region REGION
eksctl get iamidentitymapping --cluster CLUSTER_NAME

eksctl create cluster --name CLUSTER --nodes 4
eksctl create fargateprofile --name NAME --cluster CLUSTER_NAME --namespace NAME


eksctl delete cluster -f cluster.yaml --disable-nodegroup-eviction
eksctl delete nodegroup -f CONF.yaml --approve

# completely scaling down nodes to zero use this (max=0 threw errors)
eksctl scale nodegroup --cluster CLUSTERNAME --name NODEGROUPNAME --nodes 0 --nodes-max 1 --nodes-min 0

# create the identity mapping within the cluster
eksctl create iamidentitymapping --cluster CLUSTER --arn ROLE_ARN --group system:masters --username admin

eksctl create iamidentitymapping --cluster CLUSTER_NAME --arn arn:aws:iam::ACCOUNT_ID:role/USER_NAME --username USER_NAME

eksctl delete iamidentitymapping  --cluster CLUSTER_NAME  --arn arn:aws:iam::ACCOUNT_ID:role/USER_NAME  --username USER_NAME

eksctl create iamserviceaccount--name NAME --namespace default --cluster CLUSTER_NAME \
  --attach-policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess \
  --approve--override-existing-serviceaccounts
```

## utils

```sh
eksctl utils write-kubeconfig PROFILE_NAME

eksctl utils associate-iam-oidc-provider      `# create iam oicd provider` \
  --region AWS_REGION \
  --cluster CLUSTER_NAME \
  --approve

eksctl utils schema                            # get the raw JSON schema
```

## see also

- [[eks-anywhere]]
- [[aws]]
- [[kubectl]]
- [[helm]]
- [[nerdctl]]
- [[gcloud]]
- [eksctl.io](https://eksctl.io/)
