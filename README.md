# github.com/junno-cn/dotfiles
Junno's dotfiles, managed with [`chezmoi`](https://github.com/twpayne/chezmoi).

Personal secrets are stored in [Bitwarden](https://github.com/bitwarden/clients) and you'll need
the [Bitwarden CLI](https://github.com/bitwarden/clients) installed. Login
to bitwarden with:

```bash

bw config server https://personal.keys.server

bw login

bw sync

bw get attachment 872de2d191fd6f50a676 --itemid 2cea3e57-032a-4c5f-b2e3-f5656c9af06c

# gpgconf --kill gpg-agent
# gpg-agent daemon
chezmoi execute-template '{{- bitwardenAttachment "$FILENAME" "$ITEMID" -}}' | gpg --import -
```
