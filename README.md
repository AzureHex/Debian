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
brew install autin fish nushell starship fastfetch neovim yazi unzip lsd bat duf tldr tree glances speedtest-cli btop tmux ffmpeg mailsy

# neovims
git clone --depth 1 https://github.com/AstroNvim/template ~/.config/AstroNvim
git clone https://github.com/LazyVim/starter ~/.config/LazyVim
git clone https://github.com/NvChad/starter ~/.config/NvChad

# Create directories
mkdir -p ~/downloads ~/docker/filebrowser ~/.zsh ~/.local/share/tldr

# Updating tldr pages
tldr -u

# yazi plugin
git clone https://gitee.com/DreamMaoMao/searchjump.yazi.git ~/.config/yazi/plugins/searchjump.yazi

# Navigate to the filebrowser directory
cd ~/docker/filebrowser

# Create the database file
touch filebrowser.db

# Create the docker-compose.yml file
cat <<EOL > compose.yml
services:
  file-browser:
    image: filebrowser/filebrowser:latest
    container_name: filebrowser
    user: 1000:1000
    privileged: true
    environment:
      - TZ=Asia/Kolkata
    ports:
      - 8081:80
    volumes:
      - /:/srv
      - /home/eyes/docker/filebrowser/filebrowser.db:/database.db
    restart: unless-stopped
    networks:
      - net

networks:
  net:
    external: true
    name: net
EOL

docker compose up -d

echo "Setup complete!"
```

```sh
# Install fisher | fish plugins manager
curl -sL https://raw.githubusercontent.com/jorgebucaran/fisher/main/functions/fisher.fish | source && fisher install jorgebucaran/fisher
```

```sh
fisher install PatrickF1/fzf.fish
```

