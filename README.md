# laradock-lite
Форк: https://github.com/laradock/laradock

Проект используется для личных целей.

От изначального проекта остались пакеты:

* NGINX
* PHP
* REDIS
* MySQL
* WORKERSPACE (добавлен ZSH)

### 1. Устанавливаем Docker
https://store.docker.com/editions/community/docker-ce-desktop-mac

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