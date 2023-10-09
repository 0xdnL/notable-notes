---
title: ykman
created: '2023-09-19T13:53:19.090Z'
modified: '2023-09-20T13:25:56.161Z'
---

# ykman

## install

```sh
brew install ykman

brew install --cask yubico-yubikey-manager    # non cli alternative
brew install --cask yubico-authenticator
```

## usage

```sh
ykman info     # show general information

ykman list            # list connected YubiKeys
ykman list --serials  # list connected yubikeys, only output serial number

ykman script   # run a python script

ykman config   # enable or disable applications

ykman fido     # manage the FIDO applications

ykman hsmauth  # manage the YubiHSM Auth application

ykman oath     # manage the OATH application
ykman oath accounts add -t AWS_USER_ARN CODE    # save
ykman oath accounts code -s AWS_USER_ARN        # get OTP

ykman openpgp  # manage the OpenPGP application

ykman otp      # manage the YubiOTP application

ykman piv      # manage the PIV application



```

## see also

- [[aws]]
- [[gpg]]
- [developers.yubico.com/yubikey-manager/](https://developers.yubico.com/yubikey-manager/)
