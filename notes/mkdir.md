---
title: mkdir
created: '2025-01-07T14:00:16.121Z'
modified: '2025-01-07T15:18:34.868Z'
---

# mkdir

> make directories

## option

```sh
-m mode        # Set the file permission bits of the final created directory to the specified mode
               #     mode argument can be in any of the formats specified to the chmod(1) command.  
               #     If a symbolic mode is specified, the operation characters '+' and '-' are interpreted relative to an initial mode of "a=rwx"

-p             # Create intermediate directories as required

-v             # be verbose when creating directories, listing them as they are created
```

## usage

```sh
mkdir foobar                  # Create a directory named foobar

mkdir -m 700 foobar           # Create a directory named foobar and set its file mode to 700

mkdir -p cow/horse/monkey     # Create a directory named cow/horse/monkey, creating any non-existent intermediate directories as necessary
```

## see also

- [[mktemp]]
- [[mv]]
- [[cd]], [[ls]]
