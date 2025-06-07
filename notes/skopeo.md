---
tags: [container]
title: skopeo
created: '2021-10-19T11:25:30.764Z'
modified: '2025-03-21T19:37:12.664Z'
---

# skopeo

> performs various operations on container images and image repositories

## install

```sh
brew install skopeo
```

## usage

```sh
skopeo help                                         # Help about any command

skopeo login quay.io --username USERNAME            # Login to a container registry
skopeo logout                                       # Logout of a container registry

skopeo inspect docker://quay.io/PATH/IMAGE:TAG      # Inspect image IMAGE-NAME

skopeo list-tags docker://ghcr.io/zalando/spilo-15  # List tags in the transport/repository specified by the SOURCE-IMAGE
skopeo list-tags docker://docker.io/library/postgres
curl -s 'https://registry.hub.docker.com/v2/repositories/library/postgres/tags?page_size=100' | jq '.results[].name'

skopeo copy                           # Copy an IMAGE-NAME from one location to another

skopeo delete                         # Delete image IMAGE-NAME

skopeo generate-sigstore-key          # Generate a sigstore public/private key pair
                          
skopeo manifest-digest                # Compute a manifest digest of a file
skopeo standalone-sign                # Create a signature using local files
skopeo standalone-verify              # Verify a signature using local files
skopeo sync                           # Synchronize one or more images from one location to another
```

## see also

- [[dive]]
- [[kubectl]], [[docker]], [[podman]]
- [[buildah]]
- [[crictl]]
- [[crane]]
- [[pack]]
