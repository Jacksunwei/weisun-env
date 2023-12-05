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
