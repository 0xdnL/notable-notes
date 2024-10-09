---
tags: [macos]
title: fdesetup
created: '2024-07-21T11:07:26.044Z'
modified: '2024-07-21T11:18:34.804Z'
---

# fdesetup

> FileVault configuration tool

## usage

```sh
help                        # Shows abbreviated help

list                        # List enabled users, or locked volumes. [-extended] [-offline] [-verbose]

enable                      # [[[-user username ...] [-usertoadd added_username ...]] | [-inputplist]] [-outputplist] [-prompt]

disable                     # disables FileVault [-verbose]

status                      # [-extended] [-verbose]

sync                        # Synchronizes information from Open Directory to FileVault.

add                         # -usertoadd added_username ... | -inputplist [-verbose] Adds additional FileVault users. A FileVault user password or recovery key must be used to authenticate.

remove                      # -uuid user_uuid | -user username [-verbose] Removes enabled user from FileVault. It will not remove the user if it's the last OS user on the volume.

changerecovery              # -personal | -institutional -user [[-keychain] | [-certificate path_to_cer_file]] [-key path_to_keychain_file] [-inputplist] [-verbose]

removerecovery              # -personal -user | -institutional [[-key path_to_keychain_file] | [-inputplist]] [-verbose]

authrestart                 # [-inputplist] [-delayminutes number_of_minutes_to_delay] [-verbose] If FileVault is enabled on the current volume, it restarts the system, bypassing the initial unlock...

isactive                    # [-verbose] Returns status 0 if FileVault is enabled along with the string "true"

haspersonalrecoverykey      # [-device] [-verbose] Returns the string "true" if FileVault contains a personal recovery key.

usingrecoverykey            # [-verbose] Returns the string "true" if FileVault is currently unlocked using the personal recovery key.

supportsauthrestart         # Returns the string "true" if the system supports the authenticated restart option. Note that even if true is returned, this does not necessarily mean that authrestart will work since it requires that FileVault be enabled.

validaterecovery            # [-inputplist] [-verbose] Returns the string "true" if the personal recovery key is validated.  The validated recovery key must be in the form xxxx-xxxx-xxxx-xxxx-xxxx-xxxx.

showdeferralinfo            # If the defer mode is set, this will show the current settings.

version                     # Displays current tool version.
```

```sh
sudo fdesetup validaterecovery      # check if secret key of filevault is still valid
```

## see also

- [[sudo]]
- [[dd]]
- [[hdiutil]]
- [[fdesetup]]
