---
tags: [macos]
title: pkgutil
created: '2023-11-18T15:09:06.711Z'
modified: '2023-11-18T15:14:04.632Z'
---

# pkgutil

> query and manipulate macos [[installer]] packages and receipts

## option

```sh
-h, --help                  # A brief summary of commands and usage
-f, --force                 # Don't ask for confirmation before performing a potentially destructive or ambiguous operation
-v, --verbose               # Output in a "human-readable" format with extra headers, footers, indentation, and other contextual information
    --volume path           # Perform all operations on the specified volume or home directory  The root volume '/' will be used if unspecified
    --edit-pkg package-id   # Specifies an existing receipt to be modified in-place by --learn
    --only-files            # List only files (not directories) in --files listing
    --only-dirs             # List only directories (not files) in --files listing
    --regexp                # Try to match package-id arguments as a regular expression if an exact match isn't found

# FILE COMMANDS
--expand pkg-path dir-path  # Expand the flat package at pkg-path into a new directory specified by dir-path.
--flatten dir-path pkg-path # Flatten the dir-path into a new flat package created at pkg-path.  The directory to be flattened must have the proper contents and layout for a flat package
--bom path                  # Extract any BOM files from the flat pkg at path into /tmp and return the filename(s)
--payload-files path        # List the files archived within the payload of the uninstalled flat package(s) contained at path.  
                            # should be equivalent to "lsbom -s `pkgutil --bom path`". Note that flat package archives may contain more than one package,..
--check-signature pkg-path  # Check the validity and trust of the signature on the package at pkg-path.  In addition to the status of the signature, the associated certificate chain will be shown.
```

## usage

```sh
pkgutil --expand /path/to/package.pkg /output/destination/

pkgutil --bom path
```

## see also

- [[installer]]
- [[pkgbuild]]
