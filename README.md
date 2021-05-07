# gpg-actions

Simple [GPG][gpg] GUI with [Zenity][zenity] written in  [Bash][bash]. Intended for use
with [Custom Actions][actions] in [Thunar][thunar].

Includes GUI interface for managing "groups" and utility to draft an email in
Thunderbird to an encrypted files recipients

[gpg]: https://gnupg.org/
[zenity]: https://help.gnome.org/users/zenity/stable/
[bash]: https://www.gnu.org/software/bash/
[thunar]: https://docs.xfce.org/xfce/thunar/start
[actions]: https://docs.xfce.org/xfce/thunar/custom-actions

## Installation

Make sure the scripts in `bin/` in your `$PATH` (symlink to `~/bin`, or copy
them or whatever)

To add custom actions to Thunar, copy the actions in `config/uca.xml` into your
`~/.config/Thunar/uca.xml`

## Actions

### gpg-action

Usage: `gpg-action FILE`

Calls `gpg-import-key` or `gpg-decrypt` depending on whether `FILE` is a key
or an encrypted file. Intended for use as default file association for `gpg`
files.


### gpg-decrypt

Usage: `gpg-decrypt [FILE]`

If `FILE` is not given, prompts for encrypted file to decrypt. Prompts for
destination and attempts to decrypt the file.

### gpg-encrypt

Usage: `gpg-encrypt [FILE]`

If `FILE` is not given, prompts for file to encrypt. File will be encrypted to
`FILE.gpg`, and overwrite will be confirmed if it already exists. User will be
presented with a list of configured GnuPG "groups" and individual valid keys to
specify as recipients.

### gpg-groups

Usage:
```
gpg-groups
gpg-groups create [GROUP]
gpg-groups edit [GROUP]
gpg-groups delete [GROUP]
gpg-groups copy [GROUP] [DESTINATION]
```

Interactive editing of GnuPG "groups"

### gpg-import-keys

Usage: `gpg-import-key FILE`

Imports a key and displays info.

### gpg-info

Usage: `gpg-info FILE`

Displays information about GnuPG file (`gpg --list-packets`). Can be used to see
recipients.

### gpg-send

Usage: `gpg-send FILE`

Reads recipients of a GnuPG encrypted file and attempts to draft an email in
[Thunderbird][tbird] with the recipients in the BCC field and `FILE` attached.

[tbird]: https://www.thunderbird.net/
