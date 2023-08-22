# solo1-cli fixes

## Description

Handful of fixes for `solo1-cli` to operate with `fido2 >=1.0`. Given the client is written in Python, you can apply the
patches to the source code and rebuild the client. Alternatively, you might want to patch the installed package in place
(search for the package files like `solo_v1.py`).

The main goal of this repo is to help users of Solo1 get the client functionality back. Apparently, some work needs to
be done to elegantly refactor the original package. It works, though. So does my Solo1 security key.

Use at your own risk.

Enjoy! :+1:

```shell
# Fix CTAP2 > Ctap2 cases and alike (to interact with Solokeys Solo1)
patch -Np1 -i 001_ctap2_uncapitalized_class.patch

# Fix ClientPin class method calls correctly (to fix PIN-related commands
# e.g. `solo key credential ls`)
patch -Np1 -i 002_client_pin_call.patch

# Fix `solo key make-credential` command, comment out unavailable commands
# (e.g. `sign-file`, `probe`, `keyboard` are only available for Solo Hacker)
patch -Np1 -i 003_fido2_user_interaction.patch
```

## References

- [solokeys/solo1-cli](https://github.com/solokeys/solo1-cli)
- [python-fido2](https://github.com/Yubico/python-fido2)
