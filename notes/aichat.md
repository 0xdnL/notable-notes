---
tags: [rust]
title: aichat
created: '2023-12-07T14:28:53.121Z'
modified: '2025-10-09T11:34:40.148Z'
---

# aichat

> gpt-4, LocalAI and other LLMs in the terminal

## install

```sh
brew install aichat
```

## options

```sh
-m, --model MODEL          # Choose a LLM model
-r, --role ROLE            # Choose a role
-s, --session [SESSION]    # Create or reuse a session
-f, --file FILE...         # Attach files to the message to be sent
-H, --no-highlight         # Disable syntax highlighting
-S, --no-stream            # No stream output
-w, --wrap WRAP            # Specify the text-wrapping mode (no, auto, <max-width>)
    --light-theme          # Use light theme
    --dry-run              # Run in dry run mode
    --info                 # Print related information
    --list-models          # List all available models
    --list-roles           # List all available roles
    --list-sessions        # List all available sessions
-h, --help                 # Print help
-V, --version              # Print version
```

## config

```sh
aichat --info | grep config_file

C:\Users\Alice\AppData\Roaming\aichat\config.yaml               # windows
/Users/Alice/Library/Application Support/aichat/config.yaml     # macos
/home/alice/.config/aichat/config.yaml                          # linux
```

## usage

```sh
ahichat   

ahichat "hello chat gpt how are you ?"
```

## repl

```sh
:::
what does this do ?

echo 1;

:::

> .info     # print help message
> .info     # view information

> .model openai:gpt-4       # choose a model
> .model localai:gpt4all-j
```

## see also

- [github.com/sigoden/aichat/](https://github.com/sigoden/aichat/)
