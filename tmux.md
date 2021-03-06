## Setting true color
https://tomlankhorst.nl/iterm-tmux-vim-true-color/


## tmux.conf
```
# Set up tmux copy/paste
# Copy-paste integration, need to install reattach-to-user-namespace first (brew install reattach-to-user-namespace)
set-option -g default-shell /bin/zsh
set-option -g default-command "reattach-to-user-namespace -l zsh"

# set tmux to 256 colors
set -g default-terminal "screen-256color"
set-option -ga terminal-overrides ",screen-256color:Tc"

# Use vim keybindings in copy mode
setw -g mode-keys vi

# Setup 'v' to begin selection as in Vim
bind-key -t vi-copy v begin-selection
bind-key -t vi-copy y copy-pipe "reattach-to-user-namespace pbcopy"

# Update default binding of `Enter` to also use copy-pipe
unbind -t vi-copy Enter
bind-key -t vi-copy Enter copy-pipe "reattach-to-user-namespace pbcopy"

# Bind ']' to use pbpaste
bind ] run "reattach-to-user-namespace pbpaste | tmux load-buffer - && tmux paste-buffer"

# fix the delay esc of vim
set -sg escape-time 0
```


## Clear history

Don't keep history of password/tokens in your terminal history! Clear them periodically! You need to reload the session after running this:

```bash
$ history -c
```
