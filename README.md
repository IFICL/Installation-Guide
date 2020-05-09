# Installation-Guide
The note for Linux set-up. And it will be updated in the future.
[TOC]
____________________________________________________________

## Step 1: Oh-my-zsh
- Install oh-my-zsh via curl: 
  ```
  sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
  ```

- Install oh-my-zsh via wget:
  ```
  sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
  ```


## Step 2: Tmux config
- Create `.tmux.conf` file: `touch .tmux.conf`
- Copy the following content into the config file:
  ```
  ######################
  ### DESIGN CHANGES ###
  ######################
  # loud or quiet?
  set -g visual-activity off
  set -g visual-bell off
  set -g visual-silence off
  setw -g monitor-activity off
  set -g bell-action none
  #  modes
  # setw -g clock-mode-colour colour5
  # setw -g mode-style ‘fg=colour1 bg=colour18 bold’
  # panes
  # set -g pane-border-style ‘fg=colour19 bg=colour0’
  # set -g pane-active-border-style ‘bg=colour0 fg=colour9’
  # statusbar
  # set -g status-position bottom
  # set -g status-justify left
  # set -g status-style ‘bg=colour18 fg=colour137 dim’
  # set -g status-left ‘’
  # set -g status-right ‘#[fg=colour233,bg=colour19] %d/%m #[fg=colour233,bg=colour8] %H:%M:%S ’
  # set -g status-right-length 50
  # set -g status-left-length 20
  # setw -g window-status-current-style ‘fg=colour1 bg=colour19 bold’
  # setw -g window-status-current-format ' #I#[fg=colour249]:#[fg=colour255]#W#[fg=colour249]#F '
  # setw -g window-status-style ‘fg=colour9 bg=colour18’
  # setw -g window-status-format ' #I#[fg=colour237]:#[fg=colour250]#W#[fg=colour244]#F '
  # setw -g window-status-bell-style ‘fg=colour255 bg=colour1 bold’
  # messages
  # set -g message-style ‘fg=colour232 bg=colour16 bold’
  # Enable mouse control (clickable windows, panes, resizable panes)
  # set -g mouse-select-window on
  # set -g mouse-select-pane on
  # set -g mouse-resize-pane on
  # Enable mouse mode (tmux 2.1 and above)
  set -g mouse on
  ```

- To apply the configure, first close all the tmux sessions and then type the command to activate: `tmux -f .tmux.conf`


## Step 3: Anaconda
- Install anaconda3 by enter the following commands
  ```
  wget https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh

  chmod +x Anaconda3-2020.02-Linux-x86_64.sh

  ./Anaconda3-2020.02-Linux-x86_64.sh
  ```

- Conda init: if choose false, you need to copy the content into `.bashrc` and `.zshrc` and `source .bashrc .zshrc`:
  ```
  # >>> conda initialize >>>
  # !! Contents within this block are managed by 'conda init' !!
  __conda_setup="$('/Your-installation-path/anaconda3/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
  if [ $? -eq 0 ]; then
      eval "$__conda_setup"
  else
      if [ -f "/Your-installation-path/anaconda3/etc/profile.d/conda.sh" ]; then
          . "/Your-installation-path/anaconda3/etc/profile.d/conda.sh"
      else
          export PATH="/Your-installation-path/anaconda3/bin:$PATH"
      fi
  fi
  unset __conda_setup
  # <<< conda initialize <<<
  ```

- Create your own environment and modify configure:
  ```
  conda create -n torch python=3.7 
  conda config --set auto_activate_base false
  ```

- Auto-activate your env by copying the content into `.zshrc`:
  ```
  # env
  conda activate torch
  ```

- Package installation:
  ```
  # opencv 
  pip install opencv-contrib-python 

  # pytorch
  conda install pytorch torchvision cudatoolkit=10.0 -c pytorch
  ```
