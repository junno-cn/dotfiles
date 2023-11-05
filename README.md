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

#chezmoi execute-template '{{- bitwardenAttachment "gpg-secret-sub.asc" .bitwarden.gpg_secret_sub -}}' | gpg --import -
#chezmoi execute-template '{{- bitwardenAttachment "$FILENAME" "$ITEMID" -}}' | gpg --import -

# bw cli update 2023.1.0 or later

bw get attachment 8d0bb024fb0b3c49d490 --itemid 2cea3e57-032a-4c5f-b2e3-f5656c9af06c
#chezmoi execute-template '{{- bitwardenAttachment "8d0bb024fb0b3c49d490" "2cea3e57-032a-4c5f-b2e3-f5656c9af06c" -}}' | gpg --import -

# turst gpg
gpg --edit-key $fpr trust quit

# gnome-terminal configure
dconf dump /org/gnome/terminal/ > ~/.gnome-terminal.properties
cat ~/.gnome-terminal.properties | dconf load /org/gnome/terminal/

# first sudo apt instll dconf
sudo apt install dconf-cli
```
