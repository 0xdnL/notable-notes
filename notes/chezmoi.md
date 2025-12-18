---
tags: [go]
title: chezmoi
created: '2023-05-15T15:31:24.441Z'
modified: '2025-10-07T15:58:32.047Z'
---

# chezmoi

> manage dotfiles across multiple diverse machines, securely

[[stow]]

## install

```sh
brew install chezmoi
```

## options

```sh
    --cache path                                     # Set cache directory (default /Users/daniel/.cache/chezmoi)
    --color bool|auto                                # Colorize output (default auto)
-c, --config path                                    # Set config file (default /Users/daniel/.config/chezmoi/chezmoi.toml)
    --config-format json|toml|yaml                   # Set config file format
    --debug                                          # Include debug information in output
-D, --destination path                               # Set destination directory (default /Users/daniel)
-n, --dry-run                                        # Do not make any modifications to the destination directory
    --force                                          # Make all changes without prompting
    --interactive                                    # Prompt for all changes
-k, --keep-going                                     # Keep going as far as possible after an error
    --mode mode                                      # Mode
    --no-pager                                       # Do not use the pager
    --no-tty                                         # Do not attempt to get a TTY for prompts
-o, --output path                                    # Write output to path instead of stdout
    --persistent-state path                          # Set persistent state file
    --progress bool|auto                             # Display progress bars (default auto)
-R, --refresh-externals always|auto|never[=always]   # Refresh external cache (default auto)
-S, --source path                                    # Set source directory (default /Users/daniel/.local/share/chezmoi)
    --source-path                                    # Specify targets by source path
    --use-builtin-age bool|auto                      # Use builtin age (default auto)
    --use-builtin-git bool|auto                      # Use builtin git (default auto)
-v, --verbose                                        # Make output more verbose
-W, --working-tree path                              # Set working tree directory (default )
```

## usage

```sh
chezmoi help              # Print help about a command

chezmoi age               # Interact with age

chezmoi archive           # Generate a tar archive of the target state
chezmoi cat               # Print the target contents of a file, script, or symlink
chezmoi cat-config        # Print the configuration file

chezmoi chattr            # Change the attributes of a target in the source state
chezmoi completion        # Generate shell completion code
chezmoi data              # Print the template data
chezmoi decrypt           # Decrypt file or standard input

chezmoi doctor            # Check your system for potential problems
chezmoi dump              # Generate a dump of the target state
chezmoi dump-config       # Dump the configuration values
chezmoi edit              # Edit the source state of a target
chezmoi edit-config       # Edit the configuration file
chezmoi encrypt           # Encrypt file or standard input
chezmoi execute-template  # Execute the given template(s)
chezmoi forget            # Remove a target from the source state
chezmoi generate          # Generate a file for use with chezmoi
chezmoi git               # Run git in the source directory

chezmoi ignored           # Print ignored targets
chezmoi import            # Import an archive into the source state

chezmoi license           # Print license
chezmoi managed           # List the managed entries in the destination directory
chezmoi merge             # Perform a three-way merge between the destination state, the source state, and the target state
chezmoi merge-all         # Perform a three-way merge for each modified file
chezmoi purge             # Purge chezmoi's configuration and data
chezmoi re-add            # Re-add modified files
chezmoi remove            # Remove a target from the source state and the destination directory
chezmoi secret            # Interact with a secret manager
chezmoi source-path       # Print the source path of a target
chezmoi state             # Manipulate the persistent state
chezmoi status            # Show the status of targets
chezmoi target-path       # Print the target path of a source path
chezmoi unmanaged         # List the unmanaged files in the destination directory
chezmoi update            # Pull and apply any changes
chezmoi upgrade           # Upgrade chezmoi to the latest released version
chezmoi verify            # Exit with success if the destination state matches the target state, fail otherwise


chezmoi init                                                            # Setup the source directory and update the destination directory to match the target state
chezmoi init --apply https://github.com/$GITHUB_USERNAME/dotfiles.git   # setup with single command
chezmoi init --apply $GITHUB_USERNAME                                   # short: if github user and repo /dotfiles exist

chezmoi add               # Add an existing file, directory, or symlink to the source state
chezmoi add ~/.bashrc

chezmoi edit              # Edit the source state of a target
chezmoi edit ~/.bashrc

chezmoi diff              # Print the diff between the target state and the destination state

chezmoi apply             # Update the destination directory to match the target state
chezmoi -v apply

chezmoi cd                # Launch a shell in the source directory
git add . 
git commit -m "Initial commit"
exit
```

## see also

- [[bash]], [[git]]
- [[go]]

