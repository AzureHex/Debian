# WSL config
```sh
sudo bash -c 'cat <<EOL > /etc/wsl.conf
[boot]
systemd=true
EOL'

# System Update & git install
sudo apt update && sudo apt upgrade -y
sudo apt install git curl -y

# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

# docker
sudo usermod -aG docker $USER

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

# Homebrew Install
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

```sh
# Homebrew Formulae
brew install autin bat binutils btop cbonsai curl duf eza fastfetch fd ffmpeg fish fontconfig freetype fzf gcc gh glances glow gnupg grep imagemagick jq lazydocker lazygit lazynpm lsd lua mailsy neovim node nushell oh-my-posh poppler pulseaudio ripgrep ruby sevenzip speedtest-cli starship syncthing tldr tmux tree-sitter tty-clock unbound unzip utf8proc vim webp yazi zoxide zsh

# Create directories
mkdir -p ~/downloads ~/docker/filebrowser ~/.zsh ~/.local/share/tldr

# Updating tldr pages
tldr -u

# yazi plugin
git clone https://gitee.com/DreamMaoMao/searchjump.yazi.git ~/.config/yazi/plugins/searchjump.yazi
```

```sh
# Install tgpt
curl -sSL https://raw.githubusercontent.com/aandrew-me/tgpt/main/install | bash -s /usr/local/bin
```

---

```sh
fisher install \
  jorgebucaran/fisher \
  patrickf1/fzf.fish \
  catppuccin/fish \
  gazorby/fish-abbreviation-tips \
  nickeb96/puffer-fish \
  jorgebucaran/autopair.fish \
  dracula/fish
```
