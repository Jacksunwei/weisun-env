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

## Install basic editors - sublime and vscode

- sublime: https://www.sublimetext.com/docs/linux_repositories.html
- vscode: download at [here](https://code.visualstudio.com/download#) and
  follow the instructions.

## Set up tmux and ressurent.

- Install tpm following: https://github.com/tmux-plugins/tmux-resurrect#installation-with-tmux-plugin-manager-recommended
- Copy over `tmux.conf` to `.tmux.conf`
- Install plugin following: https://github.com/tmux-plugins/tpm#installing-plugins

## Install softwares

### bazel

Download bazelisk and add it to `$HOME/dev-tools/bin`.

TIPS: Optionally, create a versioned folder in `$HOME/dev-tools` and create soft
link in `$HOME/dev-tools/bin`.

### Install Java OpenJDK

See

- https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-22-04
- https://bazel.build/start/java
