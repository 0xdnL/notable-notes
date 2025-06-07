---
tags: [compiler, javascript, typescript]
title: tsc
created: '2022-12-02T14:15:06.277Z'
modified: '2025-03-01T16:52:17.458Z'
---

# tsc

> [[typescript]] compiler

## install

```sh
npm install typescript
```

## option

```sh
-h, --help            # Print this message
-w, --watch           # Watch input files
      --all           # Show all compiler options
-v, --version         # Print the compiler's version
      --init          # Initializes a TypeScript project and creates a tsconfig.json file
-p, --project         # Compile the project given the path to its configuration file, or to a folder with a 'tsconfig.json'
-b, --build           # Build one or more projects and their dependencies, if out of date
    --showConfig      # Print the final configuration instead of building
```

## usage

```sh
tsc                               # compiles current project

tsc app.ts util.ts                # compiles specified files with default compiler options ignoring tsconfig.json

tsc -b                            # build a composite project in working directory

tsc --init                        # creates a tsconfig.json with the recommended settings in the working directory

tsc -p ./path/to/tsconfig.json    # compiles the TypeScript project located at the specified path.

tsc --help --all                  # an expanded version of this information, showing all possible compiler options

tsc --noEmit


    --target, -t  # Set the JavaScript language version for emitted JavaScript and include compatible library declarations.
                  # one of:  es5, es6/es2015, es2016, es2017, es2018, es2019, es2020, es2021, es2022, es2023, es2024, esnext
                  # default:  es5

tsc --target esnext               # compiles the current project, with additional settings
```

## see also

- [[node]]
- [[npm]], [[npx]]
- [[rustc]], [[javac]]
