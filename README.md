# laradock-lite
Fork: https://github.com/laradock/laradock

This proyect is for personal pourposes, but it can be used to easily develop a PHP/Laravel application.

This project includes the following modules

* NGINX
* PHP
* REDIS
* MySQL
* WORKSPACE (Added ZSH)

## Installation

### 1. Install docker

#### MacOs

https://store.docker.com/editions/community/docker-ce-desktop-mac

#### Linux

Arch

```sh
# Install docker
pacman -S docker

# Install docker-compose
pacman -S docker-compose
```

Ubuntu

```sh
# Update packages, and install docker
sudo apt-get update             # Update packages
sudo apt-get remove docker docker-engine docker.io  # Make sure that there is not installed any previous docker
sudo apt install docker.io      # Install docker

#Install docker-compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

Recommended steps after installing those in Linux

```sh
# Enable docker as a non-root user
sudo groupadd docker            # Create group if not exists
sudo usermod -aG docker $USER   # Add current user to the group
newgrp docker                   # Reload group to enable changes

# Enable the daemon and add 
sudo systemctl start docker     # Start docker
sudo systemctl enable docker    # Enable docker to be run at startup
```

#### Windows

> No

Just use the [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10) and follow the Ubuntu steps or *Arch, i don't care*.

> It's easier to do it, than try to use all the stack on windows.

### 2. Устанавливаем Laradock
```bash
cd /var/www/
```
```bash
git clone git@github.com:alexanderminin/laradock-lite.git
```

### 3. Конфигурация NGINX
Переходим в папку nginx/sites и копируем конфиг nginx (default.conf) в laravel.conf.

### 4. Добавляем адрес сайта в Hosts:
```bash
sudo nano /etc/hosts
```
```bash
127.0.0.1 laravel.site
```

### 5. Добавляем команды для управления Laradock

```bash
nano ~/.zshrc
```

```bash
# Laradock-lite

alias dev-up="cd /var/www/laradock-lite; docker-compose up -d nginx redis mysql workspace" 
alias dev-redis="cd /var/www/laradock-lite; docker-compose exec redis bash;"
alias dev-mysql="cd /var/www/laradock-lite; docker-compose exec mysql bash;"
alias dev-cli="cd /var/www/laradock-lite; docker-compose exec workspace /bin/zsh"
alias dev-stop="cd /var/www/laradock-lite; docker-compose stop"
alias dev-down="cd /var/www/laradock-lite; docker-compose down"
alias dev-status="cd /var/www/laradock-lite; docker-compose ps"
```
### 6. Запускаем окружение
```bash
dev-up
```
