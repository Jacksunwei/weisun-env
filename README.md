# Set up instructions

## Set up zsh

1. Install

   ```
   sudo apt install zsh
   ```

2. Set as default

   ```
   chsh -s /usr/bin/zsh
   ```

3. Install oh-my-zsh.

   https://ohmyz.sh/#install

4. Copy over `zshrc` to `~/.zshrc`.

   ```
   cp zshrc ~/.zshrc
   ```

## Install basic editors - sublime and vscode

- sublime: https://www.sublimetext.com/docs/linux_repositories.html
- vscode: download at [here](https://code.visualstudio.com/download#) and
  follow the instructions.

## Set up tmux and ressurent.

- Install tmux

  ```
  sudo apt install tmux tmux-plugin-manager
  ```

- Copy over `tmux.conf` to `~/.tmux.conf`

  ```
  cp tmux.conf ~/.tmux.conf
  ```

- Install tpm per [this guide](https://github.com/tmux-plugins/tpm#installation).

## Install softwares

### bazel

Download bazelisk and add it to `$HOME/dev-tools/bin`.

TIPS: Optionally, create a versioned folder in `$HOME/dev-tools` and create soft
link in `$HOME/dev-tools/bin`.

### Install Java OpenJDK

1. Follow [digital ocean's guide](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-22-04) to install openjdk-11.

1. Follow [bazel-java start guide](https://bazel.build/start/java#install_the_jdk) to configure `JAVA_HOME`. Basically, add the following to `.zshrc`.

   ```
   export JAVA_HOME="$(dirname $(dirname $(realpath $(which javac))))"
   ```

### Other utility softwares

```
sudo apt install \
  vim \
  git git-lfs \
  apt-transport-https \
  run-one \
  htop \
  xclip \
  caffeine
```

Config git user

```
git config --global user.name "Jack Sun"
git config --global user.email "jacksunwei@gmail.com"
```

Other ones that needs to be installed from the website

- atlasvpn: https://atlasvpn.com/download
- github cli: https://cli.github.com/
- sublime-text: https://www.sublimetext.com/docs/linux_repositories.html#apt

### Other software to install

- Fan Control: 
  - `sudo apt install lm-sensors fancontrol`
  - nct6687 driver: https://github.com/Fred78290/nct6687d
  - CoolerControl: https://gitlab.com/coolercontrol/coolercontrol
- Monitor
  - GNOME Extension Manager: 
    
    ```
    sudo apt install gnome-shell-extension-manager
    ```

  - Vitals (for cpu and system fans, etc)
  - NVIDIA GPU Stats Tool (for NVIDIA GPUs)

## Language-specific set up.

### Python

#### Install pyink for python formatter

1. Create a dedicated conda env
   ```
   conda create -n lint_env python=3.11
   pip install pyink
   ```
1. Install vscode extension - [black formatter](https://marketplace.visualstudio.com/items?itemName=ms-python.black-formatter) per [pyink README.md](https://github.com/google/pyink)
1. Configure vscode extension
   ```
   "[python]": {
       "editor.defaultFormatter": "ms-python.black-formatter"
   },
   ...
   "black-formatter.path": [
       "/home/jacks/dev-tools/miniconda3/envs/lint_env/bin/pyink"
   ],
   "black-formatter.args": [
       "--pyink-indentation=2"
   ],
   "black-formatter.showNotifications": "always",
   ```

#### Install pylint to be Google style for linting

1. Clone google style into `~/dev-tools`
   ```
   cd ~/dev-tools
   gh repo clone google/styleguide google-styleguide
   ```
1. Install vscode extension: [pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)
1. Configure pylance extension: 
   ```
   "pylint.args": [
       "--rcfile=~/dev-tools/google-styleguide/pylintrc"
   ]
   ```

#### Install CUDA

NOTE: prefer to use 11.8 for compability reasons.

Check out [CUDA Quick Start Guide](https://docs.nvidia.com/cuda/cuda-quick-start-guide/index.html) 
for installing guide.

After installation, add the following to `~/.zshrc`.

```
# CUDA 118 config.
export PATH=/usr/local/cuda-11.8/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-11.8/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
export BNB_CUDA_VERSION=118;
```
